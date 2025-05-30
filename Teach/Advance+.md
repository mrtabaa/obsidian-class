- [x] `AccountService` => Debugged line 91 `loggedInUser.roles = [];` 
- [x] `AccountController` => Improve `login/register` errors handling.
- [x] `AccountController` and `AccountRepository` => Replace `AuthorizeLoggedInUser()` with `ReloadLoggedInUser()`
- [x] Add `VariablesExtensions`
- [x] Replace `string Id` with `ObjectId Id`
	- [x] Install `BCrypt`
	- [x] Modify Token with Id hashing
- [x] Install Replication
	[replication - How to configure a replica set with MongoDB - Stack Overflow](https://stackoverflow.com/a/77932054/3944285)
- [x] Remove `member-card` if unfollowed
- [x] Implement `FriendsComponent` pagination
- [x] Debug `Edit Profile` 
- [x] Upgrade `ng2-file-upload` to `7`
- [x] Implement `MemberDetails`
- [x] Prevent leaving page if modified
	- [x] See Angular Dialog
	- [x] Create `ConfirmComponent`
	- [x] Create `CommonService`
	- [x] Create `preventUnsavedChangesGuard`
		- [x] Apply in `app-route`
	- [x] `UserEdit` 
		- [x] Create `CheckisAnyValueChanged(): boolean` method
			- [x] Apply it to `submit` button and `warning`
	- [x] Create `MemberDetails`
- [x] Improve security by removing `UserName` from the token
	- [x] Create a `GetUserNameByHashedUserId()` in the `UserRepo`
	- [x] Modify the `TokenService`
	```C#
	var claims = new List<Claim>
		{
			new(JwtRegisteredClaimNames.Sub, identifierHash),
			new(JwtRegisteredClaimNames.Jti, jtiValue) // session identifier or token ID, // TODO: store in db/cache to prevent multiple login sessions with one token. If already exists, reject new login.
		};
	```
- [x] Debug Navbar menu `profilePhoto`
- [x] Filter, Search
<<<<<<< Updated upstream
- [x] `MemberRepo` => Line 43, `StringComparison.CurrentCultureIgnoreCase`
- [x] Detect Desktop/Mobile by `observer` in `TS`
- [x] `ngStyle` and `ngClss` and `signal`
- [x] `OperationResult`
- [x] Client => Change path from `absolute` to `relative`
	`apiUrl: 'http://localhost:5100/api/',` 
	to 
	`apiUrl: '//localhost:5100/api/', // Relative URL rather than Absolute with 'http:', Auto-adjust with browser`
- [x] refresh/access [[0- Tokens]]
- [ ] [[00_Overview]] `Clean Architecture` and `SOLID`
	- [ ] Centralize packages and build [[dotnet-centralized-build-setup]]
- [ ] OpenApi & Swagger
- [ ] Deployment
- [ ] [Advanced Rate Limiting Use Cases In .NET](https://www.milanjovanovic.tech/blog/advanced-rate-limiting-use-cases-in-dotnet)
- [ ] CSRF/XSRF Attack
- [ ] [[Verify Account]]
- [ ] [[Reset Password]]
- [ ] SignalR
- [ ] `EntityFramework Core` ORM => `PostgreSql`
