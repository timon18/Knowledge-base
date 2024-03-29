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

nav ul {
  @include horizontal-list;
}
```

##### Аргументы

Миксины также могут принимать аргументы, что позволяет настраивать их поведение при каждом вызове. Аргументы указываются в правиле `@mixin` после имени миксина в виде списка имен переменных, заключенного в круглые скобки. Затем миксин должен быть включен с таким же количеством аргументов в форме выражений SassScript. Значения этих выражений доступны в теле миксина как соответствующие переменные.

```scss
@mixin rtl($property, $ltr-value, $rtl-value) {
  #{$property}: $ltr-value;

  [dir=rtl] & {
    #{$property}: $rtl-value;
  }
}

.sidebar {
  @include rtl(float, left, right);
}
```

---

### Что такое Бэм? Какие там есть сущности?

БЭМ (Блок, Элемент, Модификатор) — компонентный подход к веб-разработке. В его основе лежит принцип разделения интерфейса на независимые блоки. Он позволяет легко и быстро разрабатывать интерфейсы любой сложности и повторно использовать существующий код, избегая «Copy-Paste».

##### Блок

Функционально независимый компонент страницы, который может быть повторно использован. В HTML блоки представлены атрибутом `class`.

Особенности:

-   Название блока характеризует смысл («что это?» — «меню»: `menu`, «кнопка»: `button`), а не состояние («какой, как выглядит?» — «красный»: `red`, «большой»: `big`).

**Пример**

```css
<!-- Верно. Семантически осмысленный блок `error` -->
<div class="error"></div>
```

<div class="error"></div>
```css
<!-- Неверно. Описывается внешний вид -->
<div class="red-text"></div>
```

-   Блок не должен влиять на свое окружение, т. е. блоку не следует задавать внешнюю геометрию (в виде отступов, границ, влияющих на размеры) и позиционирование.
-   В CSS по БЭМ также не рекомендуется использовать селекторы по тегам или `id`.

Таким образом обеспечивается независимость, при которой возможно повторное использование или перенос блоков с места на место.

##### Элемент

Составная часть блока, которая не может использоваться в отрыве от него

Особенности:

-   Название элемента характеризует смысл («что это?» — «пункт»: `item`, «текст»: `text`), а не состояние («какой, как выглядит?» — «красный»: `red`, «большой»: `big`).

-   Структура полного имени элемента соответствует схеме: `имя-блока__имя-элемента`. Имя элемента отделяется от имени блока двумя подчеркиваниями (`__`).

```scss
<!-- Блок `search-form` -->
<form class="search-form">
    <!-- Элемент `input` блока `search-form` -->
    <input class="search-form__input">

    <!-- Элемент `button` блока `search-form` -->
    <button class="search-form__button">Найти</button>
</form>
```

##### Модификатор

Cущность, определяющая внешний вид, состояние или поведение блока либо элемента.
Особенности:
-   Название модификатора характеризует внешний вид («какой размер?», «какая тема?» и т. п. — «размер»: `size_s`, «тема»: `theme_islands`), состояние («чем отличается от прочих?» — «отключен»: `disabled`, «фокусированный»: `focused`) и поведение («как ведет себя?», «как взаимодействует с пользователем?» — «направление»: `directions_left-top`).
-   Имя модификатора отделяется от имени блока или элемента одним подчеркиванием (`_`).
-   Структура полного имени модификатора соответствует схеме:   `имя-блока_имя-модификатора` или `имя-блока__имя-элемента_имя-модификатора`.

```scss
<!-- Блок `search-form` имеет булевый модификатор `focused` -->
<form class="search-form search-form_focused">
    <input class="search-form__input">

    <!-- Элемент `button` имеет булевый модификатор `disabled` -->
    <button class="search-form__button search-form__button_disabled">Найти</button>
</form>
```

##### Ключ-значение

-   Используют, когда важно значение модификатора. Например, «меню с темой оформления `islands`»: `menu_theme_islands`.
-   Структура полного имени модификатора соответствует схеме: `имя-блока_имя-модификатора_значение-модификатора` или `имя-блока__имя-элемента_имя-модификатора_значение-модификатора`.

```scss
<!-- Блок `search-form` имеет модификатор `theme` со значением `islands` -->
<form class="search-form search-form_theme_islands">
    <input class="search-form__input">

    <!-- Элемент `button` имеет модификатор `size` со значением `m` -->
    <button class="search-form__button search-form__button_size_m">Найти</button>
</form>
```