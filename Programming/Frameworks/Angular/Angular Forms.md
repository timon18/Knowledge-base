07-03-2023
18:59
Authors: Roman Barannik 
***
Tags: #stub #angular
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


