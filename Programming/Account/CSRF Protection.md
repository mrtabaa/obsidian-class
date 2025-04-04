
#### API

1. `IdentityServiceExtensions`
```C#
// CSRF protection  
services.AddAntiforgery(  
    options =>  
    {  
        options.HeaderName = "X-XSRF-TOKEN";  
        options.Cookie.Name = "XSRF-TOKEN";  
        options.Cookie.HttpOnly = false; // Must be false so Angular can access it  
        options.Cookie.SecurePolicy = CookieSecurePolicy.Always;  
        options.Cookie.SameSite = SameSiteMode.None; // TODO: Change to Lax  
    }  
);  
  
// Applies CSRF protection to all non-Get requests  
services.AddControllers(options =>  
{  
    options.Filters.Add(new AutoValidateAntiforgeryTokenAttribute());  
});
```

2. `AccountController`
```C#
[AllowAnonymous]
    [HttpGet("csrf_token")]
    public IActionResult GetCsrfToken()
    {
        AntiforgeryTokenSet tokens = antiforgery.GetAndStoreTokens(HttpContext);

        if (tokens.RequestToken is null)
        {
            logger.LogError("CSRF token generation failed.");
            return StatusCode(500, "Internal server error on CSRF protection.");
        }

        HttpContext.Response.Cookies.Append(
            "XSRF-TOKEN",
            tokens.RequestToken
        );

        logger.LogInformation("CSRF token generated successfully."); // Log success
        return Ok("CSRF token set");
    }

```

#### Client

3. `AccountService`
```ts
getCsrfToken$(): Observable<void> {
    return this._http.get<void>(this.baseUrl + 'csrf_token').pipe(take(1));
  }

  register(userInput: UserRegister): Observable<void> {
    return this._http.post<boolean>(this.baseUrl + 'register', userInput)
      .pipe(
        map((isRegisterSuccess: boolean) => {
          if (isRegisterSuccess) {
            sessionStorage.setItem('email', userInput.email);
            this._isVerifyingAccountSig.set(true);
          }
        })
      );
  }
```

4. `AppComponent`
```ts
ngOnInit(): void {
this.getCsrfToken();
this.accountService.reloadLoggedInUser();
}

private getCsrfToken(): void {
    this.accountService.getCsrfToken$()
      .pipe(take(1))
      .subscribe({
        next: () => console.log("CSRF Token Retrieved"),
        error: (err: HttpErrorResponse) => {
          console.error('Error retrieving CSRF token:', err);
          if (err.status === 0) {
            this.snackBar.open(
              'A network error occurred. Please try again later.',
              'Retry',
              {
                horizontalPosition: 'center',
                verticalPosition: 'top',
                duration: 7000,
              }
            ).onAction()
              .pipe(take(1))
              .subscribe(() => this.getCsrfToken());
          } else {
            this.snackBar.open(
              'The server is having trouble validating your session. Please refresh the page.',
              'Refresh',
              {
                horizontalPosition: 'center',
                verticalPosition: 'top',
                duration: 7000,
              }
            ).onAction()
              .pipe(take(1))
              .subscribe(() => window.location.reload());
          }
        }
      });
  }
```

5. `csrfInterceptor`
```ts
import {HttpErrorResponse, HttpInterceptorFn} from '@angular/common/http';
import {inject} from "@angular/core";
import {AccountService} from "../services/account.service";
import {catchError, finalize, Observable, switchMap, take, throwError} from "rxjs";
import {MatSnackBar} from "@angular/material/snack-bar";

const maxRetries = 2;

export const csrfInterceptor: HttpInterceptorFn = (req, next) => {
  const accountService = inject(AccountService);
  const snackBar = inject(MatSnackBar);

  let retryCount = 0;
  let csrfRetryInProgress = false;

  const handleRequest = (): Observable<any> => {
    return next(req).pipe(
      catchError((error: HttpErrorResponse) => {
        const isPotentialCsrf = error.status === 403 &&
          error?.error?.error === 'InvalidCsrfToken' &&
          ['POST', 'PUT', 'DELETE'].includes(req.method);

        if (isPotentialCsrf && !csrfRetryInProgress && retryCount < maxRetries) {
          csrfRetryInProgress = true;
          retryCount++;

          return accountService.getCsrfToken$().pipe(
            switchMap(() => handleRequest()), // No manual reset needed here
            catchError(err => {
              if (retryCount >= maxRetries) {
                snackBar.open(
                  'The server is having trouble validating your session. Please refresh the page.',
                  'Refresh',
                  {
                    horizontalPosition: 'center',
                    verticalPosition: 'top',
                    duration: 7000,
                  }
                ).onAction()
                  .pipe(take(1))
                  .subscribe(() => window.location.reload());
              }
              return throwError(() => err);
            }),
            finalize(() => {
              csrfRetryInProgress = false;
            })
          );
        }

        return throwError(() => error);
      })
    );
  };

  return handleRequest(); // Initial call
};
```