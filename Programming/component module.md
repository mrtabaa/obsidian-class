- [ ] Create `component.module.ts` by `ng g m modules/component`
- [ ] Move it from its parent folder `component` to the `modules` folder. 
- [ ] Under `moduels` folder => you can delete the empty `component` folder. 
- [ ] Move all your components from `app.module.ts` like below: **(Do NOT move `AppComponent`!)**
- [ ] Import all missing imports.
```ts
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';
import { AppRoutingModule } from '../app-routing.module';
import { BrowserAnimationsModule } from '@angular/platform-browser/animations';
import { FormsModule, ReactiveFormsModule } from '@angular/forms';
import { MaterialModule } from './material.module';

import { LoginComponent } from '../components/account/login/login.component';
import { RegisterComponent } from '../components/account/register/register.component';
import { HomeComponent } from '../components/home/home.component';
import { NavbarComponent } from '../components/navbar/navbar.component';
import { NoAccessComponent } from '../components/no-access/no-access.component';
import { NotFoundComponent } from '../components/not-found/not-found.component';
import { HttpClientModule } from '@angular/common/http';


const components = [
  NotFoundComponent,
  NoAccessComponent,
  NavbarComponent,
  LoginComponent,
  RegisterComponent,
  HomeComponent
];

@NgModule({
  declarations: [components],
  imports: [
    CommonModule,
    AppRoutingModule, // also in app.module.ts
    BrowserAnimationsModule, // also in app.module.ts
    FormsModule, // Remove from app.module.ts
    ReactiveFormsModule, // Remove from in app.module.ts
    HttpClientModule, // Remove from in app.module.ts
    MaterialModule // Remove from in app.module.ts
  ],
  exports: [components]
})
export class ComponentModule { }

```
- [ ] Add `ComponentModule` to `app.module.ts` => `imports:`
- [ ] Delete all moved components from `app.module.ts`
- [ ] `ng serve` again

Back to [[client Cleanup]]