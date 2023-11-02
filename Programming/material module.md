- [ ] Create `material.module.ts` by `ng g m modules/material`
- [ ] Move it from its parent folder `material` to the `modules` folder. 
- [ ] Under `moduels` folder => you can delete the empty `material` folder. 
- [ ] Move all your materials from `app.module.ts` like below:
- [ ] Import all missing imports.
```ts
import { NgModule } from '@angular/core';
import { MatToolbarModule } from '@angular/material/toolbar';
import { MatIconModule } from '@angular/material/icon';
import { MatButtonModule } from '@angular/material/button';
import { MatFormFieldModule } from '@angular/material/form-field';
import { MatInputModule } from '@angular/material/input';

@NgModule({
  exports: [
    MatToolbarModule,
    MatIconModule,
    MatButtonModule,
    MatMenuModule,
    MatFormFieldModule,
    MatInputModule,
  ]
})
export class MaterialModule { }

```
- [ ] Add `MaterialModule` to `app.module.ts` => `imports:`
- [ ] Delete all moved materials from `app.module.ts`
- [ ] `ng serve` again

Back to [[client Cleanup]]