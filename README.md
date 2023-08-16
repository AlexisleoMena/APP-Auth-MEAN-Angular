# AuthApp

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 16.0.2.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.


## Comandos
```
ng g m auth --routing
ng g m dashboard --routing
ng g c dashboard/layouts/dashboardLayout --skip-selector

cd auth
mkdir guards layouts pages interfaces components services

cd pages
ng g c loginPage --skip-selector
ng g c registerPage --skip-selector

cd layouts
ng g c authLayout --skip-selector

cd services
ng g s auth

```
## Definir rutas
```auth-routing.module.ts
const routes: Routes = [
  {
    path:'',
    component: AuthLayoutComponent,
    children: [
      {path: 'login', component: LoginPageComponent },
      {path: 'register', component: RegisterPageComponent},
      {path: '**', redirectTo: 'login'},
    ]
  }
];
```
```app-routing.module.ts
const routes: Routes = [
  {
    path:'',
    component: DashboardLayoutComponent,
    // children:[]
  }
];
```

```dashboard-routing.module.ts
const routes: Routes = [
  {
    path:'auth',
    loadChildren: () => import('./auth/auth.module').then(m => m.AuthModule),
  },
  {
    path:'dashboard',
    loadChildren: () => import('./dashboard/dashboard.module').then(m => m.DashboardModule),
  },
  {
    path: '**',
    redirectTo: 'auth'
  }
];
```

## Reemplazar contenido de app.component.html por <router-outlet/>
## Agregar <router-outlet/> al contenido de layout.component.html por 
## Diseño de la pantalla de login: https://gist.github.com/Klerith/df3ab2d62b5b20f11fd5db28b06ebb3b

## Importar ReactiveFormsModule en auth.module.ts  (posibilita injeccion en components), crear myForm y conectarlo con el login-page.component.html

## AuthService!!!

## Crear .env
```
cd src
touch environments/environment.ts
```
## Utilizar la variables en AuthService
## Importar HttpClientModule en el modulo app e inyectarlo en servicio auth
## Escribir login de auth Service e inyectar el servicio en loginPageComponent

## Instalar sweetalert2
```
npm i sweetalert2
```

## Inyectar AuthService en dashboard-layout.component.ts

## Angular schemmatics : Crear isAuthenticated Guard
```
  click derecho sobre guards
  Angular: Generate another schematic
  guards
  isAuthenticated
  functional
  true
  CantActivate

```

## Crear metodo checkAuthStatus en servicio auth, para verificar el token en /check-token

## Crear metodo finishedAuthcCheck en app.component.ts