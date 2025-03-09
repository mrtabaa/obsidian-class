Register/Login: 
	Return `AccessToken` & `RefreshToken`

#### ACCESS_TOKEN => All requests
Time: 60 Seconds


#### REFRESH_TOKEN => Only when AccessToken is expired
Time: 7 Days

##### Token Rotation
Every time `AccessToken` is expired we rotate both tokens.

#### Browser Safety
Use `Cookies` and make sure you have `httpOnly` and `SameSite` set. 