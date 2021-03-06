# Установка

Установить

`npm install vue-bootstrap-elements`

`yarn add vue-bootstrap-elements`

Подключить

`require('vue-bootstrap-elements');`

# Вводная

Мне нравится настраиваемость фреймворка bootstrap, его унифицированность и предсказуемое поведение.
Но мне не нравится следующая из этого многословность, необходимость написания нескольких строк кода для задания простого текстового поля, что я и решаю отдельными компонентами. Настраиваемость реализована через атрибуты. Такая реализация придает выразительности и понятности коду, что сказывается наилучшим образом при написании кода.

> Краткость - сестра таланта.

Дополнительно, я реализовал снипеты для быстрого набора кода. Через некоторое время и планирую реализовать специальное расширение, которое бы давало подсказки для ввода кода и предлагало бы возможные атрибуты для компонентов пакета и только для них, не предлагая для других компонентов.

Пример:
```
<card title="Форма" row>
  <field :column="[12, 6]" label="Поле 1" v-model="text_1" />
  <field :column="[12, 6]" label="Поле 2" v-model="text_2" />
  <field column="12" button right value="Отправить" />
</card>
```

# Реализованные компоненты:
* row
* collumn
* grid
* card
* field
* TableEdit

## Компонент row
Компонент, помогающий создавать сетку.
### Центрирование
Атрибут `center` реализует центрирование контента. 
Возможно указание для каких мониторов выполнять выравнивание. 
Пример: `{sm: 12, md: 4, lg: 2}`

## Компонент collumn
Реализует элемент колонки. Базируется на 
```
<div class="col-12"></div>
```
### Размер
Атрибуты `sm`, `md`, `lg` указывают размер колонки при различной ширине монитора.

### Отступы
Атрибут `offset` указывает отступы. Значения задаются объектом. Пример: `{sm: 0, md: 0, lg: 0}`.

### Выравнивание
Атрибуты `left`, `center` и `right` помогают выравнять контент с помощью добавления классов `text-left`, `text-center` и `text-right`.

## Компонент grid
Компонент `gird` реализует функционал нескольких компонентов сразу: `row` и `collumn`.
В атрибуте `col` указывается количество колонок в сетке.
Сами колонки указываются в соответсвующих слотах. Пример имени слота для первой колонки: `col-1`.
Атрибуты `sm`, `md`, `lg` указывают размер колонок. Одно значение задает один размер для колонок. Несколько значений, разделенных пробелами задают соответствеющие размеры колонок. 
Пример: 
```
<grid col=2 sm="8 4">
  <div slot="col-1">Колонка 1</div>
  <div slot="col-2">Колонка 2</div>
</grid>
```
Атрибут `center` реализует центрирование контента. Возможно указание для каких мониторов выполнять выравнивание. 
Пример: `{sm: 12, md: 4, lg: 2}`

## Компонент card
Компонент `card` базируется на коде 
```
<div class="card">
  <div class="card-body"></div>
</div>
```
Пример использования:
```
<card title="Заголовок" @close="event">
  Какой-то контент
</card>
```
### Заголовок
Указать заголовок возможно через атрибут `title`.
Так же возможно указание напрямую в основном слоте (т.е. между открывающим и закрывающим тегом card) в коде.

### header и footer
Задать части `heade`r и `footer` возможно через атрибуты либо через слоты.

### Сетка
Для упрощения работы в Vue DevTool возможно указать атрибут `row`, что автоматически укажет класс row для элемента card-body

### Центрирование
Атрибут `center` добавляет класс text-center, что центрирует контент компонента.

### Кнопка "закрыть"
При указании события `@close` автоматически добавится значок закрытия.

## Компонент field
Компонент `field` реализует поле для воода данных (input, textarea, button).
Для указания типа поля необходимо указать любой из атрибутов `text`, `textarea`, `select`, `button` `password`, `email`, `number` или `numeric`.

### select
Для указания данных списка необходимо указать атрибут `options`.
Он может быть простым массивом строк или же массивом объектов с полями `id` и `text` (или же `title`).
Пример `select`:
```
<field select v-model="pole" :options="['item 1', 'item 2', 'item 3']">
```

### number
Синоним `numeric`. Могут быть дополнительные атрибуты `max` и `min`.

### Стандартые атрибуты
`placeholder`, `disabled`, `type`. 
Атрибут `type` принимает значения: `text`, `textarea`, `select`, `button` `password`, `email`, `number`.

### Подпись
Атрибут `label` добавляет подпись к полю. При этом к родителю (локальному) добавляется класс `form-group`.
Пример:
```
<field value="Значение" label="Подпись">
```

### Размер
Атрибуты `sm` И `lg` задают соответствующие размеры поля ввода.
```
<field v-model="Значение" label="Подпись" sm>
```

### Цвет
Атрибуты: `primary`, `secondary`, `danger`.
Для Кнопок можно добавить атрибут `outline`.

### Дополнительный контент
Атрибуты `prepend` и `append` добавляют дополнительный контент перед и после поля ввода (реализовано только input)

### Колонки
Атрибут `column` задает дополнительные классы `sm-#`, `md-#`, `lg-#`. 
Примеры: `column=1`, `:column="[12 4 2]"`

## TableEdit
Компонент редактируемая таблица. Разрабатывается. Код не еще устоялся.

# Лицензия
MIT