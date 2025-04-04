Install
```C#
<PackageReference Include="UAParser.Core" Version="4.0.4"/>
```


Dto used in `RefreshToken.cs`
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

Code used in `AccountController`
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