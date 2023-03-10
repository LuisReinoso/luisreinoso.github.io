---
title: KeyValue - Pipe
date: 2018-10-19 00:00:00 Z
categories:
- angular
tags:
- angular
- pipe
layout: post
description: Uso de KeyValue Pipe Angular
---

Con keyvalue puedo iterar sobre un objeto en combinación de un ngFor

example.component.ts

{% highlight typescript linenos %}
import { Component } from '@angular/core';

@Component({
  selector: 'app-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.scss']
})
export class ExampleComponent {
  
  // key se lo denomina a la llave del objeto
  semana: {[key: string]: string};

  constructor() {
    this.semana = {
        L: 'Lunes',
        M: 'Marte',
        MI: 'Miercoles',
        J: 'Jueves',
        V: 'Viernes',
        S: 'Sabado',
        D: 'Domingo'
    }
  }
}
{% endhighlight %}

Creo un select en base a un objeto

example.component.html

{% highlight html linenos %}
{% raw %}
<select class="form-control">
    <option *ngFor="let dia of semana | keyvalue" value="{{dia.key}}">{{dia.value}}</option>
</select>
{% endraw %}
{% endhighlight %}

**Referencias**

* [KeyValuePipe Angular](https://angular.io/api/common/KeyValuePipe)
