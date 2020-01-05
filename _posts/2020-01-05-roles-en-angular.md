---
layout: post
title: "Roles en Angular"
description: "Cómo agregar roles en angular"
categories: [angular]
tags: [angular]
---
# Roles Angular

Usar ngx-permissions para validar roles usuarios
https://github.com/AlexKhymenko/ngx-permissions

Instalar
```console
npm install ngx-permissions  --save
```

Agregar al app.module

```typescript
import { NgxPermissionsModule } from 'ngx-permissions';
...
@NgModule({
  imports: [
    NgxPermissionsModule.forRoot(),
  ]
  ..
```

En método login
```typescript

import { NgxRolesService } from 'ngx-permissions';

constructor(private rolesService: NgxRolesService){}

login() {
  this.servicioAuthenticar(user).subscribe((credencialesDelUsuario) => {
    this.rolesService.addRole(credencialesDelUsuario.rol, []);
  })
}
```

para validar rutas para que accedan según usuario ```NgxPermissionsGuard```
**fuente**: [rutas](https://github.com/AlexKhymenko/ngx-permissions#usage-with-routes)
```typescript
// permite a differente de tipo rol Externo
{
      path: 'ciudad',
      component: 'CiudadComponent',
      canLoad: [NgxPermissionsGuard],
      data: {
        permissions: {
          except: 'Externo' // Externo es el rol que viene de la base de datos
        }
      }
    },
```

para validar en la vista ```*ngxPermissionsOnly```
**fuente**: [controlling-access-in-views](https://github.com/AlexKhymenko/ngx-permissions#controlling-access-in-views)
```html
<ng-container *ngxPermissionsOnly="['Administrador']">
  <button
    type="button"
    (click)="obtenerNombre()"
  >
    Obtener nombre
  </button>
</ng-container>
```