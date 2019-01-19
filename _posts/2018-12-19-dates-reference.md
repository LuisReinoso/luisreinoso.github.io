---
layout: post
title: "Date Object - Referencia"
description: "Referencia impresión date object"
categories: [javascript]
tags: [date, reference]
---

Esta referencia se basa en mostrar el valor de retorno para los métodos del objeto Date. Considerando que la fecha será la siguiente:
```javascript
const fecha = new Date("2018/12/19")
```

getDate() mes entre ```1-31```
```javascript
fecha.getDate()
19
```

getDay() dia entre ```0-6```
```javascript
fecha.getDay()
3
```

getFullYear() año ```YYYY```
```javascript
fecha.getFullYear()
2018
```

getHours() entre ```0-23```
```javascript
fecha.getHours()
0
```

getMilliseconds() entre ```0-9999```
```javascript
fecha.getMilliseconds()
0
```

getMinutes() entre ```0-59```
```javascript
fecha.getMinutes()
0
```

getMonth() entre ```0-11```
```javascript
fecha.getMonth()
11
```

getSeconds() entre ```0-59```
```javascript
fecha.getSeconds()
0
```

getTime() ```milliseconds```
```javascript
fecha.getTime()
1545195600000
```

toDateString()
```javascript
fecha.toDateString()
'Wed Dec 19 2018'
```

toISOString()
```javascript
fecha.toISOString()
'2018-12-19T05:00:00.000Z'
```

toJSON()
```javascript
fecha.toJSON()
'2018-12-19T05:00:00.000Z'
```

toString()
```javascript
fecha.toString()
'Wed Dec 19 2018 00:00:00 GMT-0500 (-05)'
```

toTimeString()
```javascript
fecha.toTimeString()
'00:00:00 GMT-0500 (-05)'
```

toUTCString()
```javascript
fecha.toUTCString()
'Wed, 19 Dec 2018 05:00:00 GMT'
```

**Referencias**

* [Date Object w3school](https://www.w3schools.com/jsref/jsref_obj_date.asp)
