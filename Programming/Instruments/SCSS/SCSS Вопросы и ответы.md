16-03-2023
18:14
Authors: Roman  Barannik
***
Tags: #stub #css #scss
***
# SCSS Вопросы и ответы

### Какую проблему решает Mixin в scss?

Миксины позволяют создать отдельные наборы css правил для их повторного переиспользования. Решает проблему дублирования кода, уменьшает временные затраты на разработку.

```scss

```
@mixin reset-list {
  margin: 0;
  padding: 0;
  list-style: none;
}

@mixin horizontal-list {
  @include reset-list;

  li {
    display: inline-block;
    margin: {
      left: -2px;
      right: 2em;
    }
  }
}



