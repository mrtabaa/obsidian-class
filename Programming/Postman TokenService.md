[**ITokenService**](https://github.com/mrtabaa/HealthApp/blob/dotnet6/api/Interfaces/ITokenService.cs)
And
[**TokenService**](https://github.com/mrtabaa/HealthApp/blob/dotnet6/api/Services/TokenService.cs)

Set Postman global token => login => test
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

![[postman-token-2.png]]

![[postman-token-1.png]]

Back to [[0 - Project Steps]]