28-03-2023
15:19
Authors: Roman Barannik
***
Tags: #stub #angular #javascript #typesript 
***
# Routing

### Обработка ошибок роутинга

В Angular ошибки маршрутизации можно обрабатывать с помощью механизма обработчиков ошибок. Обработчик ошибок - это специальная функция, выполняющаяся, когда возникает ошибка при навигации по маршрутам.

```ts
import { Injectable, ErrorHandler } from '@angular/core';
@Injectable()
export class CustomErrorHandler implements ErrorHandler {
  handleError(error: any) {
    // your error handling code here
  }
}
```

**app.module.ts**

```ts
import { NgModule, ErrorHandler } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { RouterModule } from '@angular/router';
import { CustomErrorHandler } from './custom-error-handler';

@NgModule({
  imports: [
    BrowserModule,
    RouterModule.forRoot([
      // your routes here
    ])
  ],
  providers: [
    { provide: ErrorHandler, useClass: CustomErrorHandler }
  ]
})
export class AppModule { }

```

