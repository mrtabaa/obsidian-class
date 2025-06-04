[**ITokenService**](https://github.com/mrtabaa/HealthApp/blob/dotnet6/api/Interfaces/ITokenService.cs)
And
[**TokenService**](https://github.com/mrtabaa/HealthApp/blob/dotnet6/api/Services/TokenService.cs)

**Set Postman global token:** 
	Go to `Login` request =>  `tests` Tab
	Enter the following code:
```js
const user = pm.response.json();

pm.test("Has properties", function() {
	pm.expect(user).to.have.property('email');
	pm.expect(user).to.have.property('token');
});

if (pm.test("Has properties")) {
	pm.globals.set('token', user.token);
}
```
Then go to `Environments` => `Globals`Tab => Create a variable called `token`
![[postman-token-2.png]]

Then set this variable in `User`'s `Authentication`' tab
![[postman-token-1.png]]

Back to [[Project Steps]]