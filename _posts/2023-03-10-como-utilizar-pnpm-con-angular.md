---
title: Como utilizar pnpm con Angular
date: 2023-03-10 00:46:00 Z
permalink: "/how-to-use-angular/"
categories:
- angular
- javascript
tags:
- pnpm
- npm
- JavaScript
- package manager
- dependency installation
- disk space
- development experience
- CI/CD
- installation speed
- symbolic links
- configuration options
- Angular CLI
- pnpm-lock.yaml
- package-lock.json
- shamefully-hoist
layout: post
---

## Introducción

`pnpm` es un gestor de paquetes de javascript el cual una de sus mejores ventajas **es reducir el tiempo de instalación de las dependencias**

## Instalación de pnpm

`npm install -g pnpm`

## Configuración con angular

### Proyecto nuevo

- Utilizar el angular CLI con pnpm para crear un nuevo proyecto
  `pnpm --package=@angular/cli dlx ng new amazing-project --package-manager pnpm`\\

- El angular CLI nos preguntara las opciones de configuración y finalmente instala el proyecto
  ![Install Angular with pnpm.png](/uploads/Install%20Angular%20with%20pnpm.png)

Al abrir el proyecto podemos ver el archivo `pnpm-lock.yaml`
![pnpm-lock-file.png](/uploads/pnpm-lock-file.png)

### Proyecto existente con npm

- Ejecuta el comando de `pnpm install` y automáticamente creara el archivo `pnpm-lock.yaml`

- Luego de eso borrar el archivo `package-lock.json`
  `rm package-lock.json`

- Ejecutar `pnpm start` para confirmar que todo funciona correctamente

En caso de que el proyecto no funcione hay la opción de instalar las dependencias respetando las diferentes versiones requeridas por los paquetes mediante
`pnpm install --shamefully-hoist=true`

### Comparando la instalación de pnpm y npm en un proyecto nuevo

Considerando:

- hemos instalado por primera vez el proyecto utilizando npm y pnpm.

- existen los archivos `package-lock.json` y `pnpm-lock.yaml`

- la carpeta node_modules no se encuentra en el proyecto

#### Instalación con npm

Duración: 14 segundos
![npm install.gif](/uploads/npm%20install.gif)

#### Instalación con pnpm

Duración: 2.2 segundos
![pnpm install.gif](/uploads/pnpm%20install.gif)

## Por qué pnpm es mas rápido?

Debido a que pnpm almacena las dependencias en un solo sitio y crea enlaces simbólicos a la carpeta node_modules según se necesite, de esta forma evitar descargar los paquetes y reutiliza los preexistentes en la computadora.

## Conclusiones

- La instalación de un proyecto es definitivamente mas rápido con pnpm que con npm

- La experiencia de desarrollo mejora al esperar menos tiempo en instalar las dependencias

- Reducir el tiempo de instalación también reduce el costo por servicios de CI/CD

## Referencias

- [pnpm motivation](https://pnpm.io/motivation#saving-disk-space-and-boosting-installation-speed)
- [pnpm shamefully-hoist](https://pnpm.io/npmrc#shamefully-hoist)

- [pnpm install](https://pnpm.io/cli/install)
