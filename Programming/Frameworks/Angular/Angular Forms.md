07-03-2023
18:59
Authors: Roman Barannik 
***
Tags: #stub #angular #typesript #html 
***
### Какие есть типы форм в angular?

В Angular есть два вида форм: стандартные (Template-driven) и реактивные (Reactive)

#### Стандартные

```html
<form>
  <div>
    <label>Логин</label>
    <input
      type="text"
      [(ngModel)]="loginForm.login"
      required
    />
  </div>
  <div>
    <label>Пароль</label>
    <input
      type="password"
      [(ngModel)]="loginForm.password"
      required
    />
  </div>
  <button (click)="printForm()">Войти</button>
</form>
```

```ts
loginForm: any = {
  login: 'Логин по умолчанию',
  password: '',
}

printForm(){
    console.log(this.loginForm);
}
```

#### Реактивные


```html
<form [formGroup]="buyTicketForm" novalidate>
  <div>
    <label>Passenger</label>
    <input type="text" formControlName="passenger" />
  </div>

  <div>
    <label>Age</label>
    <input type="number" formControlName="passengerAge" />
  </div>

  <div formGroupName="passengerContacts">
    <div>
      <label>Telegram</label>
      <input type="text" formControlName="telegram" />
    </div>

    <div>
      <label>Whatsapp</label>
      <input type="text" formControlName="whatsapp" />
    </div>
  </div>
</form>
```

```ts
@Component({
  selector: 'reactive-form-example',
  templateUrl: './reactive-form-example.component.html',
})
export class ReactiveFormExampleComponent {
  buyTicketForm: FormGroup

  constructor() {
    this._createForm()
  }

  private _createForm() {
    this.buyTicketForm = new FormGroup({
      passenger: new FormControl(null),
      passengerAge: new FormControl(null),

      passengerContacts: new FormGroup({
        telegram: new FormControl(null),
        whatsapp: new FormControl(null),
      }),
    })
  }
}
```


Основные поля объекта реактивной формы Angular:

-   `controls` — поля, включая вложенные `FormGroup`;
-   `errors` — содержит ошибки валидации;
-   `status` — строка, определяющая правильность заполнения формы, значение либо `VALID`, либо `INVALID`;
-   `valid` — `true`, если форма валидна;
-   `invalid` — `true`, если форма невалидна;
-   `pristine` — `true`, если не было взаимодействия с полями;
-   `touched` — `true`, если одно из полей становилось активным (получало фокус);
-   `dirty` — `true`, если пользователь заполнил хотя бы одно из полей;
-   `value` — значение формы в виде объекта;
-   `statusChanges` — позволяет отслеживать изменение статуса валидности;
-   `valueChanges` — позволяет отслеживать изменение значения.

Реактивные формы позволяют обращаться к отдельному полю используя метод `get()`, которому передается в виде строки наименование поля.

```ts
this.loginForm.get('login') // поле 
this.loginForm.get('address') // вложенная группа
this.loginForm.get('address.city') //поле вложенной группы
```

Также возможно получение полей с помощью

```ts
this.loginForm.controls['login'] // поле
this.loginForm.controls['address'] // вложенная группа
this.loginForm.controls['address.city'] // поле вложенной группы
```

Отслеживание изменений формы осуществляется через подписку на `valueChanges` `Observable`. Функция обработчик принимает параметром значение формы.

```ts
this.loginForm.valueChanges.subscribe((v) => {
  console.log(v)
})
```

Использовать `valueChanges` можно применительно к отдельному полю.

```ts
this.loginForm.get('login').valueChanges.subscribe((v) => {
  console.log(v)
})
```

Для отслеживания изменения статуса поля или формы в целом "подписывайтесь" на `statusChanges`.

```ts
this.loginForm.statusChanges.subscribe((status) => {
  console.log(status)
})
```

### Асинхронная валидация форм

Асинхронная валидация позволяет проверять формы на основе асинхронных операций, таких как HTTP-запросы или операции ввода-вывода. В Angular это можно делать с помощью `AsyncValidatorFn`, который возвращает либо промис, либо Observable.

```ts
import { AbstractControl, AsyncValidatorFn } from '@angular/forms';
import { Observable } from 'rxjs';
import { map } from 'rxjs/operators';

export function forbiddenNameValidator(nameRe: RegExp): AsyncValidatorFn {
  return (control: AbstractControl): Promise<{ [key: string]: any } | null> | Observable<{ [key: string]: any } | null> => {
    const forbidden = nameRe.test(control.value);
    return forbidden ? of({ 'forbiddenName': { value: control.value } }) : null;
  };
}
```

```ts
import { Component } from '@angular/core';
import { FormBuilder, Validators } from '@angular/forms';
import { forbiddenNameValidator } from './forbidden-name.directive';

@Component({
  selector: 'app-example',
  template: `
    <form [formGroup]="form">
      <input formControlName="name">
    </form>
    <div *ngIf="name.errors.forbiddenName">Name cannot be {{name.errors.forbiddenName.value}}</div>
  `,
})
export class ExampleComponent {
  form = this.fb.group({
    name: ['', [Validators.required], [forbiddenNameValidator(/bob/i)]]
  });

  get name() { return this.form.get('name'); }

  constructor(private fb: FormBuilder) { }
}

```

Здесь идет проверка на соответствие регулярному выражению