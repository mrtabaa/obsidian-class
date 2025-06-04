`RefreshToken` (Model)
```C#
namespace api.Models.Helpers;

public class RefreshToken
{
    [property: BsonId]
    [property: BsonRepresentation(BsonType.ObjectId)]
    public ObjectId Id { get; set; }

    public ObjectId UserId { get; set; }
    public string JtiValue { get; init; } = string.Empty;
    public string TokenValueHashed { get; init; } = string.Empty;
    public DateTimeOffset CreatedAt { get; init; }
    public DateTimeOffset ExpiresAt { get; init; }

    public DateTimeOffset? UsedAt { get; set; } // Token is used before and not allowed again
    public bool IsRevoked { get; set; } // Admin revoked session manually OR user logout

    [Required] public SessionMetadata? SessionMetadata { get; init; }
}
```

`SessionMetadata`
```C#
namespace api.Models.Helpers;

public record SessionMetadata(
    [Length(1, 64)] string DeviceType,
    [Length(1, 128)] string DeviceName,
    [Length(1, 512)] string UserAgent,
    [Length(1, 64)] string IpAddress,
    [Length(1, 64)] string Location
);
```

`TokenDto`
```C#
namespace api.DTOs.Account;

public record TokenDto(
    string AccessToken, // JWT
    RefreshTokenResponse RefreshTokenResponse
);
```

`RefreshTokenRequest`
```C#
namespace api.DTOs.Account;

public class RefreshTokenRequest
{
    [Length(10, 256)] public string RawRefreshToken { get; init; } = string.Empty;

    [Length(10, 128)] public string JtiValue { get; init; } = string.Empty;

    public SessionMetadata? SessionMetadata { get; set; }
}
```

`RefreshTokenResponse`
```C#
namespace api.DTOs.Account;

public record RefreshTokenResponse(
    string TokenValueRaw,
    string JtiValue,
    DateTimeOffset ExpiresAt
);
```