---
title: HttpClient - Headers
date: 2018-03-29 00:00:00 Z
categories:
- angular
tags:
- angular
- http
layout: post
description: Uso de headers en con HttpClient
---

Poner headers con el uso de HttpClient se realiza de la siguiente manera:

{% highlight typescript linenos %}
import { Injectable } from '@angular/core';
import { HttpClient, HttpHeaders } from '@angular/common/http';

@Injectable()
export class CabeceraService {

  private headers: HttpHeaders;

  constructor(private http: HttpClient) {
    
   this.headers = new HttpHeaders({
      'Content-Type': 'application/json',
    });

  }

  solicitud(): Observable<any> {
    return this.http.get('http://localhost/getDatos', {headers: this.headers});
  }
}
{% endhighlight %}
