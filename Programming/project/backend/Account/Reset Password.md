Implementing password recovery in an application managed by Microsoft Identity involves a secure process that allows users to reset their passwords if they forget them. Here's a step-by-step guide to implement this feature:
### **Flow Overview**

1. User receives an email with the reset link.
2. User clicks the link and is redirected to `https://yourapp.com/reset-password?token=...&email=...`.
3. Angular component extracts the token and email from query parameters.
4. User enters their new password and submits the form.
5. Angular sends the token, email, and new password to the backend API.
6. Backend validates the token and updates the password.
7. If successful, Angular navigates the user back to the login page.

---
## Backend
### Step 1: Generate a Password Reset Token

1. **Expose an API Endpoint** Create an endpoint in your `AccountController` to initiate the password reset process.
    
2. **Generate a Token** Use the `UserManager` to generate a password reset token for the user.
```C#
[HttpPost("request-password-reset/{email}")]
public async Task<ActionResult> RequestPasswordReset(string email)
{
    var user = await _userManager.FindByEmailAsync(email);
    if (user == null || !await _userManager.IsEmailConfirmedAsync(user))
    {
        // To avoid user enumeration attacks, do not reveal that the user does not exist.
        return Ok("If the email is registered and verified, a reset link will be sent.");
    }

    var resetToken = await _userManager.GeneratePasswordResetTokenAsync(user);

    // Generate a URL for the frontend to use
    var resetLink = Url.Action(
        "ResetPassword",
        "Account",
        new { token = resetToken, email = user.Email },
        protocol: HttpContext.Request.Scheme
    );

    // Send the reset link to the user's email
    await _emailService.SendEmailAsync(user.Email, "Password Reset", $"Reset your password using this link: {resetLink}");

    return Ok("If the email is registered and verified, a reset link will be sent.");
}

```
### Step 2: Reset Password

1. **Expose a Reset Password Endpoint** Create another API endpoint to handle the password reset request.
    
2. **Validate the Token** Use `UserManager.ResetPasswordAsync` to verify the token and reset the password.
```C#
[HttpPost("reset-password")]
public async Task<ActionResult> ResetPassword([FromBody] ResetPasswordDto resetPasswordDto)
{
    var user = await _userManager.FindByEmailAsync(resetPasswordDto.Email);
    if (user == null)
    {
        // Avoid user enumeration attacks
        return BadRequest("Invalid request.");
    }

    var resetResult = await _userManager.ResetPasswordAsync(user, resetPasswordDto.Token, resetPasswordDto.NewPassword);

    if (!resetResult.Succeeded)
    {
        return BadRequest(resetResult.Errors);
    }

    return Ok("Password has been reset successfully.");
}

```
`ResetPasswordDto`
```C#
public class ResetPasswordDto
{
    public string Email { get; set; }
    public string Token { get; set; }
    public string NewPassword { get; set; }
}
```

### Step 3: Secure the Flow

1. Email Verification Ensure the user’s email is verified before allowing password reset.
    
2. Token Expiration Microsoft Identity tokens for password reset typically expire after a default period (e.g., 1 day). You can configure this in IdentityOptions.
```c#
services.Configure<IdentityOptions>(options =>
{
    options.Tokens.PasswordResetTokenProvider = TokenOptions.DefaultProvider;
});

```
3. Prevent User Enumeration Always return a generic response like, "If the email is registered, a reset link will be sent," even if the email is not found.
    
4. Recaptcha for Requests Use reCAPTCHA to prevent bots from flooding the password reset request endpoint.


### Optional Enhancements

1. **reCAPTCHA** to prevent attacks and spamming.
2. **Audit Logging** Log every password reset request and reset attempt for monitoring and security.
3. **Throttle Requests** Limit the number of password reset requests per user to prevent abuse.
4. **Notify on Reset** Send a notification email to the user when their password is successfully reset.

## Fronend
1. **Create a Password Reset Component:**
**Example:** `reset-password.component.ts`
```ts
import { Component } from '@angular/core';
import { FormBuilder, FormGroup, Validators } from '@angular/forms';
import { ActivatedRoute, Router } from '@angular/router';
import { AuthService } from '../services/auth.service';

@Component({
  selector: 'app-reset-password',
  templateUrl: './reset-password.component.html',
})
export class ResetPasswordComponent {
  resetPasswordForm: FormGroup;
  token: string | null = null;
  email: string | null = null;
  isSubmitting = false;

  constructor(
    private fb: FormBuilder,
    private route: ActivatedRoute,
    private router: Router,
    private authService: AuthService
  ) {
    this.resetPasswordForm = this.fb.group({
      newPassword: ['', [Validators.required, Validators.minLength(8)]],
      confirmPassword: ['', [Validators.required]],
    });
  }

  ngOnInit(): void {
    // Extract token and email from query params
    this.token = this.route.snapshot.queryParamMap.get('token');
    this.email = this.route.snapshot.queryParamMap.get('email');
  }

  onSubmit(): void {
    if (this.resetPasswordForm.invalid) return;

    const { newPassword, confirmPassword } = this.resetPasswordForm.value;
    if (newPassword !== confirmPassword) {
      alert('Passwords do not match');
      return;
    }

    this.isSubmitting = true;
    this.authService.resetPassword(this.token!, this.email!, newPassword)
      .subscribe({
        next: () => {
          alert('Password reset successfully.');
          this.router.navigate(['/login']);
        },
        error: (err) => {
          console.error(err);
          alert('Failed to reset password.');
        },
        complete: () => this.isSubmitting = false,
      });
  }
}
```
2. **Add Routing for the Component:**
**Example:** `app-routing.module.ts`
```ts
const routes: Routes = [
  { path: 'reset-password', component: ResetPasswordComponent },
  // other routes
];
```
