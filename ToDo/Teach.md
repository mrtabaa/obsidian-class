- [x] Async Task
- [x] CancellationToken
- [x] GlobalUsingskde
- [x] DTO
- [x] https => api
- [x] https => client
- [x] Interface / Repository
- [x] Setup Postman: Account => register + User => All Users
- [x] [[New-sln,-API]] => `appsettings.json`
- [x] [[New-sln,-API]] => `BaseApiController`
- [x] Move `UserController` codes to `UserRepository`
- [x] Test in Postman
- [x] Install Angular Material from [[Install and Create Angular Project]]
- [x] Get users in `client`
- [x] Move `component.ts` code to a `service`
- [x] Create components => not-found / no-access / navbar / home / account => login + register
- [x] Set route.module
- [x] PasswordSalt & PasswordHash
- [x] Save `user` on the browser and stay logged-in
- [x] Home => Show and hide `logout` button with `ng-template`
- [x] Home => Move `ts` code to `ngOnInit()`
- [x] Design Register page
- [x] Design Login page
- [x] Switch login-register and logout places
- [x] Design Navbar
	- [x] Move `ts` code to `ngOnInit()`
	- [x] Move `Login`, `Register` and `Logout` buttons to `Navbar`
	- [x] menu with Photo location
- [x] `app.component.html` Layout (Remove div) and change scss
- [x] API cleanup => ExtensionMethods:
	- [x] ApplicationServiceExtensions.cs => AddApplicationServices
	- [x] IdentityServiceExtensions.cs => AddIdentityServices
	- [x] RepositoryServiceExtensions.cs => AddRepositoryServices
- [x] Client cleanup => Modules:
	- [x] [[component module]]
	- [x] [[material module]]
- [x] [[JWT (Token)]]
	- [x] `jwt.interceptor.ts` => Fix `showAllUsers()` error `401-Unathorized` in `Home` by sending the `token`
- [x] Upgrade to .NET-Core 8.0 from [[Upgrade .NET Core]]
- [x] Upgrade to Angular 17 [[Update Node & Angular]]
- [x] [Client-Side Vs. Server-Side Rendering](https://www.searchenginejournal.com/client-side-vs-server-side/482574/) CSR vs SSR
- [x] Disable `https/ssl` for development
- [x] Change app's browser title
- [x] Apply `async` pipe to DOM and remove `subscribe` (if `error` response is NOT needed) => home, navbar, etc. 
- [x] .NET 8.0 Primary Constructor
- [x] Changed these
	- [x] Injected `HttpClient` in `app.config.ts`
	- [x] Injected `HttpClient` in `app.config.server.ts` with `withFetch()`
	- [x] replaced constructors' injections with `inject`
	- [x] accessed `localStorage` with `PLATFORM_ID`
	- [x] updated `jwt.interceptor.ts` codes to Angular 17 version
	- [x] `app.routes.ts`  => added `account` to `register` and `login`
- [x] Update old Angular structural directives with Angular 17
	- [x] Replace `*ngFor` with `@for`. [See this page](https://medium.com/@kristiyan.velkov/angular-17-new-built-in-for-loop-86caf01b9d9e)
	- [x] Replace `*ngIf / else (ng-template)` with `@if / @else if / @else`. [See this page](https://blog.angular-university.io/angular-if/)
- [x] Added more properties to
	- [x] `AppUser.cs`
	- [x] `AccountDto` => replace `MaxLength,MinLength` with `Length(10, 500)`
	- [x] `UserDto.cs`
	- [x] Create `Photo.cs`
- [x] Create [[Postman TokenService]]
- [x] client => Create environments and place `baseApiUrl` in `environment.development`
	```bash
	ng g environments 
	```
- [x] `AccountRepo` => Change `var` to `UpdateDefinition<AppUser>`
- [x] Generate a UserDto using AppUser
- [x] Mappers
- [x] GetUserByEmailAsync()
- [x] CalculateAge() for UserDto -- [[DateTimeExtensions]]
- [x] `Count()` for `List` and `Any()` for `IEnumerable`
- [x] [[Claim Principal]]
	- [x] `TokenService` change `DateTime.Now` to `DateTime.UtcNow`
	- [x] Add `ValidateLifetime = true` to `IdentityServiceExtensions` class
	- [x] `UserController` => simplify `ClaimPrincipalExtensions.GetUserId(User)` to `User.GetUserId()`
	- [x] `ClaimPrincipalExtensions` rename `user` to `principal`
- [x] localStorage => Replace `user` with `token`
	- [x] `app.component.ts` => Get the `user` from `api` to have a fresh user on every browser's refresh to prevent expired token issue. 
	- [x] Update [[jwt.interceptor.ts]]
	- [x] Reload problem was caused, api was returning `UserDto` while client was expecting `LoggedInDto`.
		- [x] api => Move `ReloadLoggedInUser` from `UserController` to `AccountController`.
		- [x] client => Move `getLoggedInUser()` from `user.service.ts` to `account.service.ts`.
- [x] Create these components
	- [x] `ServerErrorComponent` => `path: 'server-error'` design for any server error
	- [x] `MemberListComponent` => `path: 'members'` to show members
- [x] Separate `user` and `member`
	- [x] Create/Rename to `member` model
	- [x] Create `member.service.ts`
- [x] Remove `id` from
	- [x]  client's `user.model`
	- [x] `LogedInUserDto`
- [x] Basic `authGuard` with `MatSnackBar`
- [x] Advance `app.routes`
- [x] Modify the `Register` component
	- [x] Add `Range` to `DateOfBirth` in `RegisterDto` to prevent `1/1/1`
	- [x] Convert Angular `Date` to C# `DateOnly` for DateOfBirth
	- [x] Add all properties to the component
	- [x] unsubscribe
- [x] error's `actualLength` and `minLength` and `maxLength`
- [x] Add `autoFocusDir`
- [x] Replace `Observable` with `Signal` to improve `Angular Change Detection` 
	- [x] `AccountService`
	- [x] `Navbar`
- [x] Fix navbar 
	- [x] menu items' padding
	- [x] links to `members` and `messages`
- [x] Print errors wherever user submits a form
	- [x] `Register`: User already exists.
	- [x] `Login`: Wrong username or password.
- [x] Fix TODOs
	- [x] use `requiredLength` in DOM instead of hard-coded value. 
- [x] Reorganize project folders architecture
	- [x] Remove `PhotoModifySaveService` and `IPhotoModifySaveService` from your project
	- [x] Create `backend` folder
	- [x] Move `api` to `backend`
	- [x] Move `match-finder.sln` to `backend` folder.
- [x] Photo Upload (API)
	- [x] `image-processing` project:
		- [x] From `Solution Explorer` create a `new Empty web, empty` project called `image-processing`. (Credit to Iman!)
		- [x] Add required libraries from `Nuget Gallery` to `image-processing.csproj`
			```C#
			"SkiaSharp"
			"SkiaSharp.NativeAssets.Linux"
			```
		- [x] Uninstall above libraries from `api.csproj` (if installed).
		- [x] From `_resources folder` import the given folders into `image-processing` project's folder ..  (`Helpers`, `Interfaces`, `Services`)

	- [x] `api` project:
		- [x] Add a `Photo` record/model
		- [x] Create an endpoint `AddPhoto` in `UserController` which takes a file
			- [x] Validate file (`minSize`, `maxSize`) and `fileType` to be image
		- [x] Create an `UploadPhotoAsync` method in `UserRepository` and `IUserRepository`
			- [x] Add `Photo` creation in `_Mapper`
		- [x] Add `wwwroot` folder to `api` folder
		- [x] In `api` => `Program.cs`Add `app.UseStaticFiles();` before `app.UseCors();`
		- [x] Add a reference of `image-processing` project to `api`
		- [x] Add these items to `api`'s `globalUsings.cs`
			```C#
		global using image_processing.Interfaces;
		global using image_processing.Services;
		global using image_processing.Helpers;
			```
		- [x] Add all new services to `RepositoryServiceExtensions`
		- [x] Make `PhotoService` to inherit from `PhotoStandardSize`
	- [x] Test Photo upload with `postman`. 
	- [x] Test the photo URL in the browser
	- [x] Check `MongoDbCompass` doc
- [x] Setup `member-card`. (teach `@input`)
- [x] Install [[Postman]] again
- [x] Photo Upload (client)
	- [x] In `userController` rename `fileInput` to `file` due to the `ng2-file-upload` requirement
	- [x] Create `user-edit` component under `components/user` folder
	- [x] Move `photo-editor` to `components/user`
	- [x] Inject `accountService` to get the `loggedInUser` (we need his/her `id/email`)
	- [x] Inject `memberService` to get the `getMemberByEmail()`. Use `loggedInUser.email` to get the logged-in member.
	- [x] Send this member to `photo-edit.component.ts` using `@Input`
	- [x] Create `photo-editor` component
	- [x] Install `"ng2-file-upload",`
	- [x] Explained `user-edit.component.html` causing `photo-editor` not reloading on browser's refresh. 
	- [x] Set `navbar/profile` photo on the first upload:
		- [x] `api` and `client` => in `LoggedInUser` model => Add `gender` & `profilePhotoUrl` 
		- [x] `api` => `Mappers` => initialize `Gender` and `ProfilePhotoUrl`. `IsMain` photo should be set. 
		- [x] In `photo-editor-component.ts` setup `setNavbarProfilePhoto()`
		- [x] Now `profilePhotoUrl` is available in `loggedInUserSig`. Use it anywhere in your app like `navbar`. 
		- [x] Make it round with `border-radios: 50%`.
- [x] Set another photo as main:
	- [x] API
		- [x] Create appropriate `Controller endpoint` and `Repository method`.
		- [x] Test in `Postman`
		- [x] Remove unnecessary `<string>` from `ActionResult` since we are not returning a plain string.
	- [x] Client
		- [x] Create `UpdateResult`  model in `models/helpers/update-result.model.ts`
		- [x] Add `setMainPhoto()` in `user.service`
		- [x] Use `setMainPhoto()` in `photo-editor` component
		- [x] Add `Set profile` button in `DOM`
		- [x] Set `loggedInUser` again to change `navbar profile photo`.
- [x] Delete photo:
	- [x] Make appropriate `Controller endpoint` and `Repository method`.
	- [x] Add `DeletePhotoFromDisk()` in `IPhotoService` and `PhotoService`
	- [x] Add `deletePhoto()` in `user.service`
	- [x] Use `deletePhoto()` in `photo-editor` component
	- [x] Add `delete` button in `DOM`
	- [x] Test in `Postman`
- [x] Update `LastActive` with `IAsyncActionFilter` instead of on login. 
	- [x] Delete line 72 of `AccountRepository` (if any). `LoginAsync`
	- [x] Create `LogUserActivity` class and inherit from `IAsyncActionFilter`. 
	- [x] Implement `UpdateLastActive()` in `AccountRepository`. No `endpoint` needed!
	- [x] Use `UpdateLastActive()` in `LogUserActivity`.
	- [x] Add it in `ApplicationServiceExtensions` as a `scoped service`.
	- [x] Add `[ServiceFilter(typeof(LogUserActivity))]` to the `BaseApiController`
- [x] Setup `user-edit`
	- [x] API
		- [x] Create `UserUpdateDto.cs` record/model.
		- [x] Create `UpdateUserAsync()` in `UserRepository` to update the user. 
		- [x] Update `IUserRepository`
		- [x] Test with `Postman`
	- [x] Client
		- [x] Implement `updateUser()` 
- [x] Loading using `ngx-spinner`
	- [x] Install `ngx-spinner`
	- [x] Setup the appropriate style in `angular.json`
	- [x] Create `LoadingService.ts`
	- [x] Create `LoadingInterceptor`
	- [x] Register it in `appConfig`
	- [x] Use it in `app-component`
- [x] Complete navbar links
	- [x] `MatTabsModule`,
	- [x] Links list
	- [x] Use in DOM and style it. 
- [x] Error Handling
	- [x] Client
		- [x] Add `error.interceptor`
			- [x] Explain `modelStateErrors`
		- [x] Make sure routing addresses match `app.routes`
		- [x] Update `app.config`
		- [x] Design the error components as you like.
	- [x] API
		- [x] Use `ExceptionController` as an example.
		- [x] Create a `ExceptionMiddleware` class
		- [x] Create `ApiException` record to store exceptions in DB. 
		- [x] Register it in `Program.cs`
- [x] Fix `User Since / Created` in `user-edit`.
- [x] `Encapsulation` with traditional  `Properties/props`. (The new way is`record`).
	- [x] Class with one constructor - `Parameter-less`.
	- [x] Class with one constructor - With `Parameter/s`.
		- [x] with 1 parameter.
		- [x] with 2 parameters.
	- [x] `Full prop` with conditions
	- [x] `Short prop`
		- [x] Without default value
		- [x] With default value
- [ ] Pagination
	- [x] API
		- [x] `Helpers` folder => Create `PagedList`
		- [x] `Helpers` folder => Create `PaginationParams`
		- [x] `Extensions` folder => Add `HttpExtensions`
		- [x] `Models` folder => `Helpers` folder => Create a `PaginationHeader` record.
		- [x] `MemberController` => Adjust `GetAll` appropriately.
		- [x] Test it in `Postman`. Check `Response`'s `Headers`.
	- [ ] Client
		- [x] Create `pagination.ts`
		- [x] Create `paginatedResult.ts`
		- [x] Modify `MemberService`
		- [x] Use `memberService.getAll()` in `member-list`.
		- [x] Setup and implement the `Paginator` of Angular Material.
		- [ ] Create `paginationHandler.ts` and make pagination `Generic/Reusable`.
- [ ] Switch from `token` to `loggedInUser` in `app.component`'s `localStorage`. Apply anywhere it's used.
	- [ ] In `AccountController` change `GetLoggedInUser()` to `AuthorizeLoggedInUser()`. No need to call a repository.
	- [ ] Remove `GetLoggedInUserAsync()` from `AccountRepository`
	- [ ] Fix `authGuard`
- [ ] Directive. e.g. `toLower()` and `toUpper()`
- [ ] Install [[lodash]] to generate `numbers[]` from 18 to 99.
- [ ] Upgrade Angular security
	- [ ] `npm audit`
	- [ ] Update `angular/cli` through `npm` 
	- [ ] Update Angular
	- [ ] `npm audit`
Add [Transaction](https://www.mongodb.com/products/capabilities/transactions) when needed
