19-03-2023
23:55
Authors: Roman Barannik 
***
Tags: #stub #angular #ngrx
***
# Counter

### actions.ts

```ts
import { Action, createAction, props } from “@ngrx/store”;
export const Increment = createAction(  
  ‘increment’,  
  props<{payload: number}>()  
)
```

### reducer.ts

```ts
const initialState = 0
export const countReducer = createReducer(  
  initialState,  
  on(Increment, (state: any,action: any) => {  
    return state += action.payload  
  })  
)
```

### app.module.ts

```ts
StoreModule.forRoot({count : countReducer})
```

### component.ts

```ts
this.store.dispatch(Increment({payload: 10}))
```
