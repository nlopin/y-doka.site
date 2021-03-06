---
title: if...else
name: if-else
autor: N_Lopin
co-autors:
designers:
contributors:
summary:
  - условие
  - условный переход
  - ветвление
  - выбор
---

## Кратко

Управляющая конструкция. В зависимости от условия выбирает, какой блок кода выполнить.

## Как пишется

- Выполнить один, либо другой блок кода, в зависимости от условия:

```jsx
if (условие) {
  console.log("выполнится, если условие истинное(true)")
} else {
  console.log("выполнится, если условие ложное (false)")
}
```

- Выполнить блок кода, если условие истинное, либо пропустить его:

```jsx
if (условие) {
  console.log("выполнюсь, если условие истинное")
}
```

- Выполнить блок кода, у которого условие истинное и находится выше всего в списке, остальные проверки проигнорировать:

```jsx
if (условие1) {
  ...
} else if (условие2) {
  ...
} else if (условие3) {
  ...
} else {
  ... // выполнится, если все условия выше были ложными
}
```

## Как понять

Зачем нужны управляющие конструкции, читайте в статье [«Порядок выполнения»](/posts/js/doka/execution-order).

В разработке много задач, в которых нужно по-разному обрабатывать данные. Все эти примеры описываются фразой «если ..., то ...»:

- _если_ пользователь вошел в систему, _то_ показать содержание почтового ящика. В противном случае — форму логина
- _если_ сумма покупки больше 2000₽, то почитать скидку 10%
- _если_ покупка оплачена, то показать экран успеха. В противном случае — экран с ошибкой

Фразой «если ...» определяется _условие._ Если условие выполняется, то мы выполняем часть, описанную фразой «то...». Если условие не выполняется, то нужно смотреть на фразу «В противном случае ...», когда она есть.

Если мы хотим решать подобные задачи с помощью кода, то язык программирования должен содержать аналогичные конструкции. Конструкция должна выбирать, какой код выполнять, в зависимости от условия. Такая конструкция называется `if...else`. Она предоставляет возможность _ветвления_.

По аналогии с русским языком, конструкция содержит _условие_ и _блоки кода_, которые будут выполняться в зависимости от условия. Блоки кода иногда называют _ветками_:

```jsx
if (условие) {
  // блок кода, выполнится если условие выполняется
} else {
  // блок кода, выполнится в противном случае
}
```

![Схема работы if...else](/assets/images/posts/js/execution-order/conditional.png)

Пример ниже выведет на печать слово «Привет», если во всплывающее окно ввести «Друг» и «Я тебя не знаю» в противном случае:

```jsx
let phrase = prompt("Скажи слово друг и заходи")

if (phrase === "Друг") {
  alert("Привет")
} else {
  alert("Я тебя не знаю")
}
```

### Условие

Для того, чтобы хорошо понимать if, нужно разобраться с понятием _условие_. Условие — это выражение, которое JavaScript вычислит в значение.

В самом простом случае, условие должно вычисляться в логический тип данных: `true`, либо `false`. Такие выражения получаются при использовании операторов сравнения `==`, `===`, `>`, `<`, `>=`, `<=`, `!==`, `!=`.

Например:

```jsx
if (price >= 2500) {
  price = price * 0.9 // применяем скидку, если цена больше 2500 рублей
}

if (foundItems === 0) {
  console.log("Ничего не найдено")
} else {
  console.log("печатаем результаты поиска")
}

if (user.isAdmin) {
  // сокращенная запись user.isAdmin === true
  console.log("Привет, админ!")
} else {
  console.log("Привет, пользователь!")
}
```

Выражения в условии можно комбинировать с помощью [логических операторов](/posts/js/doka/logic-operators).

В более сложном случае условие будет вычисляться в какой-либо другой тип: число, строку, массив, объект и т.д. В этом случае JavaScript будет приводить получившееся значение к логическому типу.

Какой из блоков кода выполнится?

```jsx
let foundItems = 0

if (foundItems) {
  console.log("Ничего не найдено")
} else {
  console.log("печатаем результаты поиска")
}
```

Чтобы понять, какой блок кода выполнится, нужно запомнить правила преведения разных типов к логическому. Важное правило:

> Все, что не приводится к `false`, будет `true`

Осталось запомнить 7 значений, которые приводятся к `false`:

- `false`
- `0`
- `""`
- `null`
- `undefined`
- `NaN`
- `0n`(тип BigInt)

Зная это правило, мы поймем, что в примере выше есть баг: мы будем писать «Ничего не найдено» всегда, кроме случая, когда в перменной `foundItems` окажется `0`. Тогда мы попытаемся напечатать результаты поиска.

### Вариации

#### `if` без `else`

Если мы хотим выполнить действие, когда условие верно, но в противном случае не делать ничего, то достаточно написать только `іf` без блока `else`:

```jsx
// напечатаем приветствие только Виктору, для других не делаем ничего
if (username === "Виктор") {
  console.log("Привет, Витёк! Эта пасхалка для тебя")
}
```

#### `if ... else if ... else`

Задача может содержать больше чем два случая. Для ее решения можно собирать `if...else` в цепочки:

Например, в зависимости от статуса пользователя менять размер скидки:

```jsx
let discount = 0
if (userStatus === "VIP") {
  discount = 25
} else if (userStatus === "priveleged") {
  discount = 15
} else if (userStatus === "clubMember") {
  discount = 5
}
```

В этом случае выполнится тот блок кода, условие которого истинное и находится выше по коду. Остальные условия будут проигнорированы.

Когда условий становится много, то страдает читаемость кода. В этом случае лучше писать [switch](/posts/js/doka/switch), но он подходит не всегда.

## В работе

🛠 Если нужно сохранить в переменную одно, либо другое значение, в зависимости от условия, то можно это сделать двумя путями.

Простой:

```jsx
let value = 1 // значение по умолчанию
if (day === "Tuesday") {
  value = 50
}
```

С использованием тернарного оператора (короткая запись `if..else`):

```jsx
let value = day === "Tuesday" ? 50 : 1 // во вторник значение 50, во всех остальных случаях 1
```

Тернарный оператор стоит использовать только если выражение короткое. В противном случае такой код будет плохо читаться.

🛠 Частый паттерн — установить значение по умолчанию, если в переменной нет значения. Можно сделать так:

```jsx
let value = 0 // значение по умолчанию

if (externalValue) {
  value = externalValue // установить значние, если в externalValue что-либо хранится
}
```

Код можно сократить, воспользовавшись операцией логического ИЛИ `||`:

```jsx
let value = externalValue || 0 // если externalValue не объявлен, то значение установится в 0
```
