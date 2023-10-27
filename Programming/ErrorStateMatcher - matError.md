**Show mat-error while typing or touched:**

1. `Client` => `app` => Create a folder called `validators`

2. In `validators` folder, create `default-error-state.matcher.ts` file with this code:
```ts
import { FormControl, FormGroupDirective, NgForm } from '@angular/forms';
import { ErrorStateMatcher } from '@angular/material/core';

export class DefaultErrorStateMatcher implements ErrorStateMatcher {
    isErrorState(control: FormControl | null, form: FormGroupDirective | NgForm | null): boolean {
        return !!(control && control.invalid && (control.dirty || control.touched));
    }
}
```

3. In `app.module` import in **providers**:
```ts
import{ErrorStateMatcher}from'@angular/material/core';
import{DefaultErrorStateMatcher}from'./validators/default-error-state.matcher';

@NgModule({

providers: [
	{ provide: ErrorStateMatcher, useClass: DefaultErrorStateMatcher }
],

```

4. Re-Serve the app.

Back to [[0 - Project Steps]]