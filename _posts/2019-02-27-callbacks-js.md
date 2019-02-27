---
layout: post
title: "callbacks: ejemplo mundo real lodash - findIndex"
description: "Learn from source code: Repaso conceptos javascript callbacks usando lodash findIndex"
categories: [javascript, learn from source code]
tags: [callbacks, source code, javascript, lodash]
---
El callback es una función que se pasa como argumento de otra función.

Un ejemplo sencillo sería el siguiente
```javascript
// funcion hola mundo
function holaMundo(nombre) {
    console.log('Hola ' + nombre);
}

// funcion principal - primer orden
function saludoEstudiantes(nombresEstudiantes, callback) {
    if (nombresEstudiantes.length > 0) {    
        for (let indice = 0; indice < nombresEstudiantes.length; indice++) {
            callback(nombresEstudiantes[indice]);
        }
    }
}

// llamar el saludo usando como parametro una funcion
const nombresEstudiantes = ['Juan', 'Andrea'];
saludoEstudiantes(nombresEstudiantes, holaMundo);
```

Usualmente los callback tienen dos parametros:
- error: se refiere a un string que representa el valor del error
- callback: la función a ejecutar.

El ejemplo anterior quedaría

```javascript

// funcion hola mundo
function holaMundo(error, nombre) {
    if (error) {
        console.error(error);
        return;
    }
    console.log('Hola' + nombre);
}

// funcion principal - primer orden
function saludoEstudiantes(nombresEstudiantes, callback) {
    if (nombresEstudiantes.length > 0) {    
        for (let indice = 0; indice < nombresEstudiantes.length; indice++) {
            callback(null, nombresEstudiantes[indice]);
        }
    } else {
        callback('Error numero de estudiantes', null);
    }
}

// llamar el saludo usando como parametro una funcion
const nombresEstudiantes = ['Juan', 'Andrea'];
saludoEstudiantes(nombresEstudiantes, holaMundo);
```

Un ejemplo del mundo real sería:
https://github.com/lodash/lodash/blob/master/.internal/baseFindIndex.js
El cual tiene de parámetro un **predicate**: una función que tiene 3 parámetros (**objeto**, **indice**, **arreglo**) pasado a otra función **baseFindIndex**
```javascript
// retorna el indice del objeto que tenga de nombre mario
function predicado(objeto) {
    return objecto == 'Mario';
}
const nombres = ['Pablo', 'Mario', 'Ana'];
_.findIndex(nombres, predicado);
```
Resultado
```bash
1
```

**Referencias**

* [Callback MDN](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function)
