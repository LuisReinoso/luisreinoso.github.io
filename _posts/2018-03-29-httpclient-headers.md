---
layout: post
title: "HttpClient - Headers"
description: "Uso de headers en con HttpClient"
categories: [angular]
tags: [angular, http]
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
