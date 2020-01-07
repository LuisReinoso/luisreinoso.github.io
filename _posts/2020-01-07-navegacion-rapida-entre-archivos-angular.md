---
layout: post
title: "Cómo navegar rápidamente entre archivos de proyectos de Angular en VSCode."
description: "La manera de acelerar el desarrollo en tus proyectos de Angular en VSCode"
categories: [angular]
tags: [angular]
---
En base a mi experiencia esto depende de dos factores:
- la estructura del proyecto.
- el editor de texto que uses.

Para este post se usa el siguiente entorno:
- **editor de texto**: VSCode
- **sistema operativo**: Linux
- **proyecto**: [inventario-app](https://github.com/LuisReinoso/inventario-app)

## Estructura del proyecto

Partiendo de esta estructura
```code
e2e/                         
src/                         
|- app/                      
|  |- core/                  
|  |- shared/                
|  |- app.component.*        
|  |- app.module.ts          
|  |- app-routing.module.ts  
|  +- ...                    
|- assets/                   
|- environments/             
|- theme/                    
|- translations/             
|- index.html                
|- main.scss                 
|- main.ts                   
|- polyfills.ts              
+- test.ts                   
```

### Estructura de carpeta `/src`
```code                    
src/                         
|- app/                      
|  |- bodega/                 crud bodega
|  |- core/                   funcionalidad principal
|  |- inicio/                 pantalla principal
|  |- login/                  login
|  |- main-nav/               barra de navegación
|  |- producto/               crud producto
|  |- registro/               sign in
|  |- shared/                 funcionalidad compartida
|  |- usuario/                crud usuario
|  |- app.component.*         
|  |- app.module.ts          
|  |- app-routing.module.ts                
```

### Estructura módulos
Lo ideal es dividir en módulos cada uno de los funcionalidades de tu aplicación
dentro de cada módulo tener: 
- components
- servicios locales
- module file
- routing module file

```code                    
src/                         
|- app/                      
|  |- bodega/                          crud bodega
|  |  |- components/                   componentes de bodega
|  |  |  |- bodega-dialog              componente dialogo
|  |  |- bodega.component.ts               componente principal de bodega
|  |  |- bodega.module.ts                 módulo bodega
|  |  |- bodega-routing.module.ts         módulo routing bodega       
```

### Nombre de los archivos/carpetas
Realmente el nombre de los archivos recomiendo sea según la funcionalidad que este realice.

### Editor de texto
El editor de texto te puede ayudar principalmente con sus atajos de teclado y los extensiones disponibles en el.

## Atajos de teclado
**Nota** Los atajos aquí presentados pueden variar de sistema operativo y en posteriores versiones de VSCode

Para ver los [atajos del teclado de VSCode](https://code.visualstudio.com/docs/getstarted/keybindings)

- Buscar archivo: Simplemente pones en nombre del feature que buscas.
  <kbd>Ctrl</kbd> + <kbd>p</kbd>

  ![](/static/img/posts/navegacion_rapida_vscode.png)

- Abrir o cerrar panel lateral: Permite más espacio para ver el archivo
  <kbd>Ctrl</kbd> + <kbd>b</kbd>

  * Abierto

  ![](/static/img/posts/barra_lateral_abierto_vscode.png)

  * Cerrado

  ![](/static/img/posts/barra_lateral_cerrado_vscode.png)

## Extensiones

- [vscode-angular2-files](https://github.com/ivalexa/vscode-angular2-files)
  Desde la interfaz te permite crear modulos, componentes, entre otros. 

- [vscode-ng-language-service](https://github.com/angular/vscode-ng-language-service)
  Plugin que permite utilizar autocompletado y checkeo de errores en el template.
  **Nota**: Ten encuenta que debes tener en tu proyecto ```@angular/language-service >=v9.0.0```

- [angular2-switcher](https://github.com/infinity1207/angular2-switcher)
  Cambia entre archivos .ts .scss/.css .spec

## Lectura recomendada
- [Guía estilo Angular](https://angular.io/guide/styleguide)