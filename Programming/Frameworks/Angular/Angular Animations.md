28-04-2023
10:58
Authors: Roman Barannik 
***
Tags: #stub #javascript #typesript #angular 
***
# Angular Animations

### Пример анимации модалки сбоку

```ts
@Component({
  selector: 'modal',
  templateUrl: './modal.component.html',
  styleUrls: ['./modal.component.scss'],
  animations: [
    trigger('expandedModal', [
      transition(':enter', [
        style({ 'margin-left': '-700px' }),
        animate('0.5s ease-out', style({ 'margin-left': '0' }))
      ])
    ])
  ]
})
```

```html
<form [formGroup]="infoForm" *ngIf="this.infoForm" [@expandedModal]>
</form>
```
