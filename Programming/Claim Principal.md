In `Extensions` folder create a class called `ClaimPrincipalExtensions` with this code.

```C#
public static class ClaimPrincipalExtensions
{
    public static string? GetUserId(this ClaimsPrincipal user)
    {
        return user.FindFirst(ClaimTypes.NameIdentifier)?.Value;
    }
}
```