07-03-2023
19:12
Authors: Roman Barannik
***
Tags: #stub #angular #typesript #html
***
### FormBuilder

В качестве альтернативы можно создать реактивную форму (и настоятельно рекомендуется) с Angular `FormBuilder`.

Его использование помогает избежать повторений и повышает читабельность кода.

```ts
@Component({
  selector: 'reactive-form-example',
  templateUrl: './reactive-form-example.component.html',
})
export class ReactiveFormExampleComponent {
  buyTicketForm: FormGroup

  constructor(private fb: FormBuilder) {
    this._createForm()
  }

  private _createForm() {
    this.buyTicketForm = this.fb.group({
      passenger: '',
      passengerAge: '',
    })
  }
}
```

Поддерживается вложенность

```ts
this.buyTicketForm = this.fb.group({
  passenger: '',
  passengerAge: '',
  passengerContacts: this.fb.group({
    telegram: '',
    whatsapp: '',
  }),
})
```



