
```C#
    public async Task<TokenDto> GenerateTokensAsync(
        RefreshTokenRequest refreshTokenRequest, ObjectId userId, CancellationToken cancellationToken
    )
    {
        string identifierHash = await StoreHashedUserId(
            userId, cancellationToken
        ); // this securedId is stored in user's collection to associate with the AppUser.

        return new TokenDto(
            GenerateAccessTokenAsync(identifierHash),
            await GenerateRefreshTokenAsync(refreshTokenRequest, userId, cancellationToken)
        );
    }

    private string GenerateAccessTokenAsync(string identifierHash)
    {
        var claims = new List<Claim>
        {
            new(JwtRegisteredClaimNames.Sub, identifierHash)
        };

        var key = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(_jwtSettings.Key));
        var creds = new SigningCredentials(key, SecurityAlgorithms.HmacSha512Signature);

        var token = new JwtSecurityToken(
            _jwtSettings.Issuer,
            _jwtSettings.Audience,
            claims,
            expires: DateTime.UtcNow.AddMinutes(10), // Short lifespan
            signingCredentials: creds
        );

        return new JwtSecurityTokenHandler().WriteToken(token);
    }

    private async Task<RefreshTokenResponse> GenerateRefreshTokenAsync(
        RefreshTokenRequest refreshTokenRequest, ObjectId userId, CancellationToken cancellationToken
    )
    {
        var tokenValueRaw = Guid.CreateVersion7().ToString();

        var refreshToken = new RefreshToken
        {
            UserId = userId,
            JtiValue = Guid.CreateVersion7().ToString(),
            TokenValueHashed = TokenHasher.HashWithSecret(tokenValueRaw, _jwtSettings.Key),
            CreatedAt = DateTimeOffset.UtcNow,
            ExpiresAt = DateTimeOffset.UtcNow.AddDays(7),
            SessionMetadata = refreshTokenRequest.SessionMetadata
        };

        await _collectionRefreshTokens.InsertOneAsync(refreshToken, null, cancellationToken);

        return new RefreshTokenResponse(
            tokenValueRaw,
            refreshToken.JtiValue,
            refreshToken.ExpiresAt
        );
    }
```