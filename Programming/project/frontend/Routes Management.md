#### Eager loading
Placing paths in `app.routes.ts` as before:

**Pros**:  Fast init time. It's already downloaded in the bundle. 
**Const**: 
* Slower app startup with larger bundle.
* Not modular in feature folders. A messy route file. 

#### Lazy loading
Placing paths under each feature like: 
	`features` => `order` => `routes.ts`,
	`features` => `message` => `routes.ts`,	
	etc. 

**Pros**:
* Faster app startup with smaller bundle.
* Modular in feature folders. Clean route files.
**Const**: 
* Slow init time. It has to download on navigation. **(only on the first load. After that it's fast)** 
 
##### Steps
1. Create `routes.ts` file for each feature. 
 
For example in `order` feature
`routes.ts`
```ts
import { Routes } from '@angular/router';
import { OrderListComponent } from './order-list/order-list.component';
import { OrderDetailComponent } from './order-detail/order-detail.component';
import { authGuard } from '../../core/guards/auth.guard';

export const orderRoutes: Routes = [
  {
    path: '',
	runGuardsAndResolvers: 'always', // Always check authGuard to make sure the user is still logged in
	canActivate: [authGuard],
    children: [
		{ path: '', component: OrderListComponent }, // /orders
	    { path: ':id', component: OrderDetailComponent } // /orders/123
	]
  }
];
```

2. Register this path in the `app.routes.ts` in the root along with other paths. (3rd item)
```ts
import { Routes } from '@angular/router';
import { HomeComponent } from './features/home/home.component';
import { LoginComponent } from './features/auth/login/login.component';

export const routes: Routes = [
  {
    path: '',
    component: HomeComponent // ✅ eagerly loaded
  },
  {
    path: 'login',
    component: LoginComponent // ✅ eagerly loaded
  },
  {
    path: 'order',
    loadChildren: () =>
      import('./features/order/routes').then(m => m.dashboardRoutes) // ✅ lazy loaded
  }
];
```