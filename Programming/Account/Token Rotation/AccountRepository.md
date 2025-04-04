##### RefreshTokenAsync
```C#
    public async Task<OperationResult<TokenDto>> RefreshTokensAsync(
        RefreshTokenRequest refreshTokenRequest, CancellationToken cancellationToken
    )
    {
        RefreshToken expectedTokenFromDb = await _collectionRefreshTokens.
                                               Find(
                                                   token => token.JtiValue == refreshTokenRequest.JtiValue
                                               ).
                                               SingleOrDefaultAsync(cancellationToken)
                                           ?? throw new ArgumentNullException(
                                               nameof(expectedTokenFromDb), "cannot be null."
                                           );

        if (!ValidateSession(refreshTokenRequest, expectedTokenFromDb))
        {
            //TODO: Logged in from new device/location. Perform 2FA.
        }

        if (expectedTokenFromDb.UsedAt is not null)
        {
            await RevokeAllRefreshTokens(expectedTokenFromDb.UserId, cancellationToken);
            // TODO: Hacked, force to change password.    
        }

        // Check token expiration, revoked, and HMAC validation
        if (
            expectedTokenFromDb.ExpiresAt < DateTimeOffset.UtcNow
            || expectedTokenFromDb.IsRevoked // e.g. revoked by admin or user logout
            || !TokenHasher.ValidateToken(refreshTokenRequest.RawRefreshToken, expectedTokenFromDb.TokenValueHashed)
        )
        {
            return new OperationResult<TokenDto>(
                false,
                Error: new CustomError(
                    ErrorCode.IsSessionExpired,
                    SessionExpiredMessage
                )
            );
        }

        UpdateDefinition<RefreshToken>? revokeTokenUpdateDef = Builders<RefreshToken>.Update.
            Set(token => token.UsedAt, DateTimeOffset.UtcNow).Set(t => t.IsRevoked, true);

        await _collectionRefreshTokens.UpdateOneAsync(
            token => token.Id == expectedTokenFromDb.Id, revokeTokenUpdateDef, null,
            cancellationToken
        );

        // Token is valid
        return new OperationResult<TokenDto>(
            true,
            await _tokenService.GenerateTokensAsync(refreshTokenRequest, expectedTokenFromDb.UserId, cancellationToken),
            null
        );
    }
```

##### Helper methods
ValidateSession
```C#
private static bool ValidateSession(RefreshTokenRequest refreshTokenRequest1, RefreshToken refreshToken)
        =>
            ValidationsExtension.ValidateObjectId(refreshToken.UserId)
            && !(refreshToken.SessionMetadata is null || refreshTokenRequest1.SessionMetadata is null)
            && refreshToken.SessionMetadata.DeviceType == refreshTokenRequest1.SessionMetadata.DeviceType
            && refreshToken.SessionMetadata.DeviceName == refreshTokenRequest1.SessionMetadata.DeviceName
            && refreshToken.SessionMetadata.UserAgent == refreshTokenRequest1.SessionMetadata.UserAgent
            && refreshToken.SessionMetadata.IpAddress == refreshTokenRequest1.SessionMetadata.IpAddress;
```

RevokeAllRefreshTokens
```C#
private async Task RevokeAllRefreshTokensAsync(ObjectId userId, CancellationToken cancellationToken)
    {
        // TODO: Record and warn as hacked / Token stolen and used again.
        UpdateDefinition<RefreshToken> updateDefinition = Builders<RefreshToken>.Update.Set(
            token => token.IsRevoked, true
        );

        await _collectionRefreshTokens.UpdateManyAsync(
            token => token.UserId == userId, updateDefinition, null, cancellationToken
        );
    }
```