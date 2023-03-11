---
title: Que es storybook y como utilizarlo en Angular?
date: 2023-02-08 00:00:00 Z
categories:
  - angular
tags:
  - angular
layout: post
description:
  Storybook permite desarrollar la parte interfaz grafica de manera aislada,
  aprende como utilizarlo en Angular aqui.
---

Storybook es un entorno de desarrollo para construir componentes de interfaz de usuario. Te permite desarrollar tus componentes de forma aislada, lo que significa que **no tienes que preocuparte por el resto de tu aplicación cuando trabajas en un componente específico**.

Aqui una visión general de cómo utilizar Storybook en Angular.

## Instalacion

La forma más rápida es ejecutando el siguiente comando
`npx storybook init`

Y agregando al `angular.json` en la section de architect

```
{
  ...
  "architect": {
    ...
    "storybook": {
      "builder": "@storybook/angular:start-storybook",
      "options": {
        "browserTarget": "angular-cli:build",
        "port": 6006
      }
    },
    "build-storybook": {
      "builder": "@storybook/angular:build-storybook",
      "options": {
        "browserTarget": "angular-cli:build"
      }
    }
  }
}

```

## Convirtiendo tu componente en una historia

Lo primero que tienes que hacer es crear un nuevo archivo llamado `header.stories.ts` en la carpeta del componente que deseas realizar.

Una vez hecho esto, puedes importar tu componente en el archivo y luego escribir tu historia. Una historia es simplemente una función que devuelve el componente sobre el cual quieres trabajar. Por ejemplo, si quisiéramos trabajar en un componente header, nuestra historia podría ser así

```typescript
import { moduleMetadata } from '@storybook/angular';
import { HeaderComponent } from './header.component';
import { Story, Meta } from '@storybook/angular/types-6-0';

export default {
  title: 'Layout/Header',
  component: HeaderComponent,
} as Meta;

const Template: Story<HeaderComponent> = (args: HeaderComponent) => ({
  component: HeaderComponent,
  props: args,
});

export const header = Template.bind({});
header.args = {};
```

## Creación de múltiples historias para un componente

A menudo resulta útil **crear varias historias para un mismo componente**, de modo que pueda ver cómo se comporta en diferentes situaciones. Por ejemplo, es posible que desee probar el header con un diferentes textos.

```typescript
export const headerWithText = Template.bind({});
header.args = {
  today: '27-03-2021',
};

export const headerWithoutText = Template.bind({});
header.args = {
  today: '',
};
```

Cada argumento permitido dentro del `args` es parte un input dentro del componente

```typescript
import { Component, ChangeDetectionStrategy, Input } from '@angular/core';

@Component({
  selector: 'app-header',
  templateUrl: './header.component.html',
  styleUrls: ['./header.component.scss'],
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class HeaderComponent {
  @Input() today = '';
}
```

De esta forma podemos ver como se comporta el header en con diferentes textos

## Conclusiones

- Desarrollar componentes de forma aislada sin preocuparte de la aplicación
- Probar componentes en diferentes estados (por ejemplo, con diferentes datos)
- Ver cómo se comporta los componentes en diferentes navegadores y tamaños de pantalla
- Documentar componentes para que otros desarrolladores entiendan fácilmente cómo utilizarlo

## Enlaces

- [Storybook - Angular guide](https://storybook.js.org/docs/guides/guide-angular/)
- [Intro to storybook](https://www.learnstorybook.com/intro-to-storybook/angular/en/get-started/)
