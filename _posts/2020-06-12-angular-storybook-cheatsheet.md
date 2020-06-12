---
layout: post
title: "Angular storybook cheatsheet"
description: "Quickly reference how to use angular story book"
categories: [angular]
tags: [angular]
---
## Installation

```console
npm install -g @storybook/cli
```

Go to angular project then execute

```console
sb init
```

* Remove angular stories examples

## Create a new story.

  ```console
  ng g component test
  ```

  ### Create story file
  ```test.stories.ts``` It should have stories before `ts` extension

  ```typescript
  export default {
  title: 'Ideario Components',
  component: IdearioComponent,
  decorators: [
    moduleMetadata({ // imports
      imports: [CommonModule]
      })
    ]
  };
  ```

## Add module decorator

```typescript
export const test = () => ({
  component: TestComponent,
  ...,
  moduleMetadata: {
    imports: [],
    declarations: [],
    providers: []
  },
});
```

## Add props (inputs/outputs)
```typescript
export const buttonWithProps = () => ({
  component: Button,
  props: {
    text: 'save',
    onClick: action('click this button'),
  },
});
```
## Add ng-content
```typescript
export const withContent = () => ({
  component: Button,
  template: `
  <ideario-button>
    <span>Super text</span>
  </ideario-button>
  `,
  moduleMetadata: {
    declarations: [IdearioButtonComponent]
  },
});
```
## Fixing commons  errors
On `.storybook` folder


#### 100% height
Add to `preview-body.html` file

```html
<style>
  #root {
    height: 100%;
  }
</style>
```


### On Ionic
#### Page on blank
https://github.com/storybookjs/storybook/issues/7703

```html
<style>
  html:not(.hydrated) body {
    display: block !important;
  }

</style>
```

#### No render components

Add to `preview-head.html` file
```html
<script nomodule="" src="https://unpkg.com/@ionic/core@latest/dist/ionic/ionic.js"></script>
```