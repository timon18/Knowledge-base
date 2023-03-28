27-03-2023
13:33
Authors: Roman Barannik
***
Tags: #stub #angular #javascript #typesript  
***
# Angular Modules

### Что это

Angular **модуль** - это класс с декоратором `@NgModule()` который служит изолирующей логической объединяющей структурой для компонентов, директив, фильтров и сервисов. Все перечисленные сущности определяются и конфигурируются с помощью `@NgModule()`

Angular приложение имеет модульную архитектуру и состоит, по крайней мере, из одного главного, или корневого, модуля. Все остальные относятся к второстепенным.

---

### Модульность самого Angular'а

Сама библиотека `@angular` также модульная:

-   `BrowserModule`
-   `CommonModule`
-   `FormsModule`
-   `ReactiveFormsModule`
-   `HttpClientModule`;
-   `RouterModule`.

---

### Структура модуля

Ключевая роль при создании Angular модуля у декоратора `@NgModule()`, принимающего конфигурационный объект со свойствами:

-   `imports` - массив, где указывается список импортируемых второстепенных модулей;
-   `exports` - массив компонентов, директив и фильтров, которыми пользуются другие модули, если они импортируют текущий;
-   `declarations` - массив компонентов, директив и фильтров;
-   `entryComponents` - массив создаваемых динамически компонентов;
-   `bootstrap` - массив, в котором указывается компонент для загрузки;
-   `providers` - массив сервисов

---

### Типы модулей

`CoreModule` - общепринятое название для модуля, используемого исключительно для поставки сервисов. Он не содержит в себе компонентов, директив и фильтров.

```ts
@NgModule({
  imports: [],
  declarations: [],
  providers: [],
})
export class CoreModule {
  static forRoot(): ModuleWithProviders {
    return {
      ngModule: CoreModule,
      providers: [
        AuthService,
        LoggerService,
        SettingsService,
      ],
    }
  }
}
```

`SharedModule` - общепринятое название для Angular модуля, служащим единым хранилищем для компонентов, директив и фильтров, которыми пользуются другие модули.

```ts
@NgModule({
  imports: [
    CommonModule,
    FormsModule,
    ImageCropperModule,
    ScrollbarModule,
    SlickModule,
    SlickModule.forRoot(),
  ],
  exports: [
    CommonModule,
    ImageCropperModule,
    ScrollbarModule,
    SlickModule,
    AppLangsComponent,
    AppTabFilterComponent,
    AppFileUploadComponent,
    ComponentPreloaderDirective,
  ],
  declarations: [
    AppLangsComponent,
    AppTabFilterComponent,
    AppFileUploadComponent,
    ComponentPreloaderDirective,
  ],
})
export class SharedModule {}
```

В нужном модуле

```ts
@NgModule({
    imports: [
        CoreModule.forRoot(),
        SharedModule
    ]
})
```

### Lazy loading modules

**app.routing.module.ts**

```ts
const routes: Routes = [
  {
    path: 'items',
    loadChildren: () => import('./items/items.module').then(m => m.ItemsModule)
  }
];
```