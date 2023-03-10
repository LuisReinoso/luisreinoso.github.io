---
title: python virtual environments
date: 2019-03-05 00:00:00 Z
categories:
- python
tags:
- python
- python virtual environment
- python create virtual environment
- python virtualenv
- virtualenv
layout: post
description: Referencia rápida para la creación de python virtual environments
---

Crea entornos virtuales de python para manejar los paquetes de forma local, de esta forma cuando hagas la instalación de otros paquetes en forma global no afecte tu entorno local.

## Instalación paquetes global
Se instlan de forma global cuando ejecutas directamente el sobre el comando python
```console
python -m pip install nombre_paquete
```

## Instalación paquetes local

### Python 2.x
#### Requerimientos
Instalación virtualenv
```console
python -m pip install virtualenv
```

#### Crear environment
```console
virtualenv nombre_entorno --python=python2.7
```
**nota**: el argumento --python indica la version de python a ser instalada

#### Ingresar en el environment
```console
source nombre_entorno/bin/activate
```
Como resultado debes tener
```console
(nombre_entorno)$
```
Ahora instalas
```console
# individualmente
pip install nombre_paquete
# instalación requirements
pip install -r requirements.txt
```
### Python 3.x
#### Crear environment
```console
python3 -m venv nombre_entorno
```
#### Ingresar en el environment
```console
source nombre_entorno/bin/activate
```
Como resultado debes tener
```console
(nombre_entorno)$
```
Ahora instalas
```console
# individualmente
pip install nombre_paquete
# instalación requirements
pip install -r requirements.txt
```