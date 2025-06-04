## Create a workspace and projects

#### Creations
1. Create a workspace named `frontend` without a project
```bash
ng new frontend --create-application=false
```

2. Create our apps/libraries inside the `frontend` workspace
	Only an `app` has an `angular.json`. Libraries cannot run by themselves. 
```bash
cd frontend

ng g app client

ng g app landing

ng g lib ui

ng g lib tool
```

2. Create a component in `landing`
```bash
ng g c components/login --project=landing
```

#### Assign ports and serve
All Angular projects run on port `4200` by default. Now we have two project and we must change one of them to prevent port conflict on serve. 
1. Consider `client` as default with port `4200`
2. Change `landing` port to `4201` using `angular.json`:
```js
"projects": {
  "landing": {
    "architect": {
      "serve": {
        "options": {
          "port": 4201
        }
      }
    }
  }
}

```
3. Run both projects:
```bash
ng s --project=client

ng s --project=landing
```
Now `client` runs on `4200`
And `landing` runs on `4201`



## Install `Angular Material`
```bash
ng add @angular/material --project=client

ng add @angular/material --project=landing
```
Note: Libraries like `ui` which don't need to be set on `angular.json` and use the root packages. So we don't need to install `Material` on them

## Create components/services in the `Ui` library

##### Create components/services in `client` app:
* Create `OrderComponent`:
```bash
ng g c features/order/order --project=client
```
* Create `OrderService`:
```bash
ng g s features/order/order --project=client
```

##### Create components/services in libraries
* Create a `UiButtonComponent` in the `ui` library to use it in the `client` app
```ts
ng g c ui-button --project=ui --prefix=ui
```

* Create `ToolsHelperService` in the `tools` library to use in the `client` app
```bash
ng g s tools-helper --project=tools --prefix=tools
```

Notes: 
2. `--prefix=ui` renames the component's selector from `app-button` to `ui-button`. These components' names do not conflict with our app's components. 
3. `--project=ui` generates the component inside the `ui` project. 
```ts
// projects/ui/src/lib/button/button.component.ts
import { MatButtonModule } from '@angular/material/button';

@Component({
  standalone: true,
  selector: 'ui-button',
  imports: [CommonModule, MatButtonModule],
  template: `
    <button mat-button [color]="color">
      <ng-content></ng-content>
    </button>
  `,
})
export class UIButtonComponent {
  @Input() color: 'primary' | 'accent' | 'warn' = 'primary';
}
```
4. Import `ui-button` to use in the `client` or `landing` apps


###### List of the items to be created in the `Ui` library

These components are shared, design-driven, and domain-agnostic — ideal for a `ui` library:

- ✅ **Modals**
- ✅ **Cards**
- ✅ **Dialogs**
- ✅ **Form field wrappers**
- ✅ **Toasts**
- ✅ **Custom buttons with icon/loader**
- ✅ **Layout components** (e.g., `ui-section`, `ui-container`)
