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
- [ ] Prevent leaving page if modified
	- [ ] See Angular Dialog
	- [ ] Create `ConfirmComponent`
	- [ ] Create `CommonService`
	- [ ] Create `preventUnsavedChangesGuard`
		- [ ] Apply in `app-route`
	- [ ] `UserEdit` 
		- [ ] Create `isAnyValueChanged(): boolean` method
			- [ ] Apply it to `submit` button and `warning`
	- [ ] Create `MemberDetails`
- [ ] Improve security by removing `UserName` from the token
	- [ ] Create a `GetUserNameByHashedUserId()` in the `UserRepo`
	- [ ] Modify the `TokenService`
	```C#
	var claims = new List<Claim>
		{
			new(JwtRegisteredClaimNames.Sub, identifierHash),
			new(JwtRegisteredClaimNames.Jti, jtiValue) // session identifier or token ID, // TODO: store in db/cache to prevent multiple login sessions with one token. If already exists, reject new login.
		};
	```
- [ ] Filter, Search
- [ ] Debug Navbar menu `profilePhoto`
- [ ] Detect Desktop/Mobile by `observer` in `TS`
- [ ] Deployment
- [ ] SignalR
- [ ] `EntityFramework Core` ORM => `MySQL`
- [ ] `Clean Architecture` and `SOLID`