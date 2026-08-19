---
title: "Mock ActivatedRoute in Angular tests: params and queryParams"
date: 2019-03-08 00:00:00 Z
redirect_from:
- "/angular/2019/03/08/how-to-mock-activated-route-in-angular.html"
categories:
- angular
tags:
- angular
- activatedroute
- activatedroute data
- activated route
- activatedroute example
- activatedroute get params
- activatedroute mock
- activatedroute params empty
- activatedroute unit test
- activatedroute url
- queryParams
- params
- read params from url
- mock use value
- No provider for ActivatedRoute
layout: post
description: "Fix the 'No provider for ActivatedRoute' error in your unit tests. Working example that mocks params and queryParams so the component reads the URL as it does in production."
---

Example applied to **queryParams** and **params** of ActivatedRoute

In this example we have a common use of ActivatedRoute. **Read params from url**
`example.component.ts`
```typescript
import { ActivatedRoute } from '@angular/router';
export class ExampleComponent implements OnInit {

  constructor(private activateRoute: ActivatedRoute) {
    this.activatedRoute.params.subscribe(params => {
      if (params['id_params']) {
        ...
      }
    });

    this.activatedRoute.queryParams.subscribe(params => {
      if (params['id_query_params']) {
        ...
      }
    });
  }

}
```

**Mock is on useValue**. Set same params of activatedRoute.params or activatedRoute.queryParams inside convertToParamMap


`example.component.spec.ts`
```typescript
import { ExampleComponent } from './example.component';
import { ActivatedRoute, convertToParamMap } from '@angular/router';
import { of } from 'rxjs';
...

describe('ExampleComponent', () => {
  let component: ExampleComponent;

  beforeEach(async(() => {
    TestBed.configureTestingModule({
      imports: [...],
      providers: [
        {
          provide: ActivatedRoute,
          useValue: { // Mock
            queryParams: of(
              {
                id_params: 'id_params_test'
              }
            ),
            params: of(
              {
                id_query_params: 'id_query_params_test'
              }
            )
          }
        }
      ],
      declarations: [ExampleComponent]
    }).compileComponents();
  }));
});
```
Common error related that this post solve:
* No provider for ActivatedRoute
