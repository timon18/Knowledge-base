20-03-2023
15:47
Authors: Roman Barannik
***
Tags: #stub #angular 
***
# Lazy Loading

Ленивая загрузка позволяет уменьшить время загрузки страницы за счет откладывания времени загрузки отдельных частей приложения. Например, вы посещаете приложение интернет-магазина, которое состоит из списка товаров и корзины. Очевидно, что вам не нужны изображения товаров, которые сейчас находится за пределами экрана; очевидно так же, что вам не нужно грузить все данные о содержимом корзины до тех пор, пока пользователь не перешёл к ней.

### Angular Lazy Loading

Ленивая загрузка в Angular основана на более поздней загрузке некоторых модулей. 

##### app.routing.module.ts

```ts
const routes: Routes = [{
  path: 'lazy', loadChildren: () => import('./lazy-module/lazy-module.module').then((m) => m.LazyModuleModule)
}];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
```

##### lazy.module.ts

```ts
const routes: Routes = [{
path: '', component: LazyComponent
}]

@NgModule({
  declarations: [
    LazyComponent
  ],
  imports: [
    CommonModule,
    RouterModule.forChild(routes)
  ],
  exports: [RouterModule]
})
```

##### app.component.html 

```html
<h1>main</h1>
<button routerLink="/lazy">lazy route</button>
<router-outlet></router-outlet>
```

И из `app.module.ts` можно удалить `lazy.module.ts` 