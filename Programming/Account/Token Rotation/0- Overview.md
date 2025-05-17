# 🔐 Secure Refresh Token Flow and Cookie Strategy

This document outlines the architecture and best practices used to implement secure refresh token rotation using encrypted cookies in the Hallboard authentication system.

---

## ✅ Overview

- **Access Token**: Short-lived JWT (e.g., 15 min), stored in an `HttpOnly` secure cookie.
    
- **Refresh Token**: Opaque string with associated `jtiValue`, stored securely in an encrypted cookie.
    
- **Backend**: Validates, rotates, and manages sessions via a database of refresh tokens.
    

---

## 🔄 Refresh Token Flow
 
### 🔐 1. Login / Initial Authentication

- User logs in with credentials or wallet.
    
- `TokenService.GenerateTokensAsync(...)`:
    
    - Creates a new `jtiValue` (GUID v7)
        
    - Stores `UserId`, `jtiValue`, `TokenValueHashed`, and `SessionMetadata` in `RefreshTokens` collection
        
    - Creates access token with `sub = identifierHash`
        

### 🍪 2. Cookies Sent to Client

- `auth.access-token`: JWT access token
    
- `auth.refresh-token`: Encrypted `RefreshTokenResponse`
    
    - Contains: `RawRefreshToken`, `JtiValue`, `ExpiresAt`
        
    - Encrypted using ASP.NET's `IDataProtectionProvider`
        

### 🔁 3. Token Rotation on Refresh

- On API call with expired access token:
    
    - Interceptor sends request to `/api/account/refresh-tokens`
        
    - Decrypts cookie → `RefreshTokenRequest`
        
    - Validates:
        
        - DB lookup by `JtiValue`
            
        - `TokenHasher.ValidateToken(.HashToken(incomingRaw), TokenValueHashed)`
            
        - Expiry, `IsRevoked`, and `UsedAt`
            
        - Device info matches `SessionMetadata`
            
    - If valid:
        
        - Marks current refresh token as `IsRevoked = true`, `UsedAt = now`
            
        - Creates a new refresh token + new `jti`
            
        - Issues a new access token and sends both in cookies
            

---

## 🧱 Cookie Configuration

| Cookie               | Type      | HttpOnly | Secure | SameSite       | Path                          |
| -------------------- | --------- | -------- | ------ | -------------- | ----------------------------- |
| `auth.access-token`  | JWT       | ✅ XSS    | ✅ SSL  | `Strict / Lax` | `/`                           |
| `auth.refresh-token` | Encrypted | ✅ XSS    | ✅ SSL  | `Strict / Lax` | `/api/account/refresh-tokens` |

---

## 🧠 Security Benefits

- **No raw refresh tokens in DB** (stored hashed with HMAC)
    
- **Device fingerprinting** (via `SessionMetadata`)
    
- **Rotation with revocation** — one-time use per refresh
    
- **Encrypted cookies** — prevents tampering and snooping
    
- **Minimal data exposed to frontend** — no `UserId` or internal IDs
    

---

## 🛡 Future Enhancements

- Add `RefreshTokenUsageLog` collection for auditing unusual reuse
    
- Optionally encrypt access token cookie for added defense-in-depth
    
- Support multiple simultaneous refresh tokens per user/device
    
- Visual dashboard of sessions ("Logged in devices")
    

---

> 📁 Last updated: April 3, 2025
> 
> Author: Reza Taba