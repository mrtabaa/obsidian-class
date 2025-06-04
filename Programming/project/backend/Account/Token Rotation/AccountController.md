#### Endpoint
```C#
 [HttpPost("refresh-tokens")]
    public async Task<ActionResult> RefreshTokens(CancellationToken cancellationToken)
    {
        bool isSuccess = Request.Cookies.TryGetValue("auth.refresh-token", out string? protectedRefreshToken);
        if (!isSuccess || string.IsNullOrEmpty(protectedRefreshToken))
            return Unauthorized("Your session has expired. Login again.");

        // Decrypt RefreshTokenDto
        RefreshTokenRequest refreshTokenRequest = tokenCookieService.DecryptRefreshTokenRequest(protectedRefreshToken);

        refreshTokenRequest.SessionMetadata = ExtractSessionMetadata();

        OperationResult<TokenDto>
            result = await accountRepository.RefreshTokensAsync(refreshTokenRequest, cancellationToken);

        if (!result.IsSuccess)
        {
            return result.Error?.Code switch
            {
                ErrorCode.IsSessionExpired => Unauthorized(result.Error.Message),
                _ => BadRequest("Failed to refresh token. Try again or contact the support.")
            };
        }

        AddTokensToResponseCookies(result.Result);
        return Ok("Tokens refreshed successfully.");
    }
```

#### SessionMetadata
1. Install `api.csproj`
```csproj
<PackageReference Include="UAParser.Core" Version="4.0.4"/>
```

2. Code
```C#
private SessionMetadata ExtractSessionMetadata()
    {
        var userAgent = HttpContext.Request.Headers["User-Agent"].ToString();
        Parser? parser = Parser.GetDefault();
        ClientInfo? client = parser.Parse(userAgent);

        string deviceType = client.Device.IsSpider ? "Bot" :
            string.IsNullOrWhiteSpace(client.Device.Family) ? "Unknown" : client.Device.Family;
        var os = $"{client.OS.Family} {client.OS.Major}";
        var browser = $"{client.Browser.Family} {client.Browser.Major}";

        var deviceName = $"{os} - {browser}";

        string ipAddress = HttpContext.Connection.RemoteIpAddress?.ToString() ?? "Unknown";

        // Optionally get location from headers (e.g., behind Cloudflare)
        string location = HttpContext.Request.Headers["CF-IPCountry"].FirstOrDefault() ?? "Unknown";

        return new SessionMetadata(
            deviceType,
            deviceName,
            string.IsNullOrWhiteSpace(userAgent) ? "Unknown" : userAgent,
            ipAddress,
            location
        );
    }
```

#### Add tokens to cookies
```C#
private void AddTokensToResponseCookies(TokenDto tokenDto)
    {
        // Access Token
        Response.Cookies.Append(
            "auth.access-token", tokenDto.AccessToken, new CookieOptions
            {
                HttpOnly = true,
                Secure = true,
                // TODO: Create an obsidian document for token management
                // Use 'SameSiteMode.lax' if using OAuth, payments sites, etc.
                // Also implement CSRF Tokens to prevent CSRF attacks
                SameSite = SameSiteMode.None,
                // Domain = ".hallboard.com", // Ensures the cookie is valid across subdomains (e.g., www.hallboard.com, api.hallboard.com)
                Expires = DateTimeExtensions.GetTokenExpirationDate(tokenDto.AccessToken), // e.g. 15 min,
                Path = "/"
            }
        );

        // Refresh Token
        string encryptedCookie = tokenCookieService.EncryptRefreshTokenResponse(tokenDto.RefreshTokenResponse);

        Response.Cookies.Append(
            "auth.refresh-token", encryptedCookie, new CookieOptions
            {
                HttpOnly = true,
                Secure = true,
                SameSite = SameSiteMode.None,
                // Domain = ".hallboard.com",
                Expires = tokenDto.RefreshTokenResponse.ExpiresAt.UtcDateTime,
                Path = "/api/account/refresh-tokens"
            }
        );
    }
```