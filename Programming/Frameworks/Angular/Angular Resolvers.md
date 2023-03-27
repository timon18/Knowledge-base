27-03-2023
18:07
Authors: Roman Barannik
***
Tags: #stub #angular #javascript #typesript 
***
# Angular Resolvers

### Что это

Резолверы помогают загружать данные при загрузке компонента (например чтобы не рисовалась пустая верстка, а появлялась сразу с заполненными данными)

Сам резолвер: 

```ts
@Injectable({ providedIn: 'root' })
export class HeroResolver implements Resolve<Hero> {
  constructor(private service: HeroService) {}

  resolve(
    route: ActivatedRouteSnapshot,
    state: RouterStateSnapshot
  ): Observable<any>|Promise<any>|any {
    return this.service.getHero(route.paramMap.get('id'));
  }
}
```

**app.routing.module.ts**

```ts
@NgModule({
  imports: [
    RouterModule.forRoot([
      {
        path: 'detail/:id',
        component: HeroDetailComponent,
        resolve: {
          hero: HeroResolver
        }
      }
    ])
  ],
  exports: [RouterModule]
})
export class AppRoutingModule {}
```

**component.ts**

```ts
export class HeroDetailComponent implements OnInit {
  readonly hero$ = this.route.data.pipe(
    map((data: { hero: Hero }) => data.hero)
  );

  constructor(
    private route: ActivatedRoute,
  ) {}
}
```
