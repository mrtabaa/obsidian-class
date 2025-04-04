1. Add this to `IdentityServiceExtensions` under `#region Token`
```C#
services.AddDataProtection(); // To Encrypt/Decrypt cookies
```

2. Code
```C#
using System.Security.Cryptography;

namespace api.Extensions;

public static class TokenHasher
{
    public static string HashWithSecret(string input, string secretKey)
    {
        byte[] keyBytes = Encoding.UTF8.GetBytes(secretKey);
        using var hmac = new HMACSHA256(keyBytes);
        byte[] hash = hmac.ComputeHash(Encoding.UTF8.GetBytes(input));
        return Convert.ToHexString(hash).ToLowerInvariant();
    }

    public static bool ValidateToken(string incomingTokenHashed, string expectedTokenHashed)
    {
        byte[] aBytes = Encoding.UTF8.GetBytes(incomingTokenHashed);
        byte[] bBytes = Encoding.UTF8.GetBytes(expectedTokenHashed);

        // Always use SecureEquals instead of == to prevent timing attacks.
        return CryptographicOperations.FixedTimeEquals(
            aBytes, bBytes
        );
    }
}
```