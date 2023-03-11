---
title: How to use pnpm with Angular
date: 2023-03-10 00:46:00 Z
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
permalink: /how-to-use-angular/
lang: en
---

## Introduction

`pnpm` is a JavaScript package manager that has one of its best advantages **in reducing dependency installation time**.

## Installing pnpm

`npm install -g pnpm`

## Configuring with Angular

### New Project

- Use the Angular CLI with pnpm to create a new project
  `pnpm --package=@angular/cli dlx ng new amazing-project --package-manager pnpm`\\

- The Angular CLI will ask us for configuration options and finally install the project
  ![Install Angular with pnpm.png](/uploads/Install%20Angular%20with%20pnpm.png)

When we open the project we can see the `pnpm-lock.yaml` file
![pnpm-lock-file.png](/uploads/pnpm-lock-file.png)

### Existing Project with npm

- Run the `pnpm install` command and it will automatically create the `pnpm-lock.yaml` file

- After that, delete the `package-lock.json` file
  `rm package-lock.json`

- Run `pnpm start` to confirm that everything is working correctly

If the project does not work, there is the option of installing dependencies respecting the different versions required by the packages using
`pnpm install --shamefully-hoist=true`

### Comparing pnpm and npm installation in a new project

Considering:

- we have installed the project for the first time using npm and pnpm.

- there are the `package-lock.json` and `pnpm-lock.yaml` files

- the node_modules folder is not in the project

#### Installation with npm

Duration: 14 seconds
![npm install.gif](/uploads/npm%20install.gif)

#### Installation with pnpm

Duration: 2.2 seconds
![pnpm install.gif](/uploads/pnpm%20install.gif)

## Why is pnpm faster?

Because pnpm stores dependencies in a single location and creates symbolic links to the node_modules folder as needed, thus avoiding downloading packages and reusing pre-existing ones on the computer.

## Conclusions

- Project installation is definitely faster with pnpm than with npm

- The development experience improves by waiting less time to install dependencies

- Reducing installation time also reduces cost for CI/CD services

## References

- [pnpm motivation](https://pnpm.io/motivation#saving-disk-space-and-boosting-installation-speed)
- [pnpm shamefully-hoist](https://pnpm.io/npmrc#shamefully-hoist)

- [pnpm install](https://pnpm.io/cli/install)
