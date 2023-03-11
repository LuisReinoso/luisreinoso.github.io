---
title: Como usar images en Chat GPT
date: 2023-02-28 00:00:00 Z
categories:
  - chat GPT
  - prompt engineering
tags:
  - chat GPT
  - openAI
layout: post
description: Conoce cómo utilizar imágenes en Chat GPT con un ejemplo.
---

## Explicacion

Para utilizar imagenes en ChatGPT utilizaremos la sintaxis de Markdown ya que esta puede mostrar una imagen desde una URL

```
![DESCRIPTION](IMAGE_URL)
```

Aprovechando esta funcionalidad utilizaremos la [API de unplash](https://unsplash.com/developers) para generar imagenes dado un texto.

Especificamente esta URL donde podemos obtener una imagen basado en el texto `https://source.unsplash.com/400x400/?[texto a reemplazar]`

## Ejemplo

Para demostrar este metodo se creara un juego de adivinar el animal, el ChatGpt nos dara una serie de pistas sobre el animal que debemos adivinar, y nosotros responder con el nombre del animal.

El prompt a ser utilizado sera:

```
Actua como un juego interactivo para adivinar un animal, dame una pista a la vez, espera por mi respuesta para continuar con la siguiente pista, cuando adivine el animal devuelve un mensaje de "Felicitaciones" ![FotoAnimal](https://source.unsplash.com/800x400/?[animal]) reemplaza [animal] con el nombre del animal adivinado en ingles
```

> Actua como un juego interactivo para adivinar un animal, dame una pista a la vez, espera por mi respuesta para continuar con la siguiente pista, cuando adivine el animal devuelve un mensaje de "Felicitaciones" ![FotoAnimal](https://source.unsplash.com/800x400/?[animal]) reemplaza [animal] con el nombre del animal adivinado en ingles

![](/static/img/posts/adivina_animal_inicio.png)

Una vez adivinado el resultado se puede observar la imagen

![](/static/img/posts/adivina_animal_fin.png)
