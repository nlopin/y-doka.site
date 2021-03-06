---
title: <form>
name: form
autor: vladimir
co-autors:
  - ABatickaya
designers:
contributors:
summary:
  - form
  - <form>
  - тэг
  - тег
  - action
  - method
  - форма
---

## Кратко

Добавляет на страницу форму, которую может заполнить пользователь. Например, «Имя», «Фамилия», «Email». Данные формы отправляются на сервер по кнопке «Отправить».

## Пример

```html
<form action="" method="get" class="form-example">
  <div class="form-example">
    <label for="name">Введите имя: </label>
    <input type="text" name="name" id="name" required />
  </div>
  <div class="form-example">
    <label for="email">Введите email: </label>
    <input type="email" name="email" id="email" required />
  </div>
  <div class="form-example">
    <input type="submit" value="Отправить" />
  </div>
</form>
```

## Как это понять

Сайты используют формы, чтобы собрать какую-то информацию у пользователя. Это может быть форма заказа в онлайн-магазине или форма обратной связи. Пользователь заполняет поля или выбирает нужную опцию в списке и нажимает «Отправить».

## Как пишется

Стилизовать `<form>` можно с помощью CSS.

На странице можно сделать сколько угодно форм. Но одновременно пользователь сможет отправить только одну заполненную форму.

## Атрибуты

- `accept-charset` — задаёт кодировку, в которой сервер принимает данные из формы. Самая распространённая кодировка — `UTF-8`. Можно указать один вариант или несколько. Например, `accept-charset="UTF-8 Windows-1251"` и так далее. В этом случае названия нужно разделять пробелами. Здесь можно задать значение по умолчанию: `accept-charset="UNKNOWN"`. Тогда кодировка будет такой, какая используется на странице с формой.
- `action` — здесь мы пропишем ссылку на программу, которая обработает форму. Это может быть полная URL-ссылка, а может быть относительная, типа `html/sendform`. Если не укажешь атрибут `action`, то страница будет просто обновляться каждый раз, когда нажимаешь кнопку «Отправить».
- `autocomplete` — включает или выключает автозаполнение для формы. Браузер может подставить данные, которые пользователь сохранил ранее, например, пароль, номер банковской карты или адрес. Если у пользователя в настройках браузера отключена функция автозаполнения, то этот атрибут уже ни на что не повлияет. Атрибут `autocomplete` можно задать и для конкретных элементов. Есть два значения:
- `on` — значение по умолчанию. Включает автозаполнение для этой формы;
- `off` — выключает автозаполнение. Например, если форма собирает уникальные данные, типа капчи («Введите слово с картинки»).
- `enctype` — определяет, в какой кодировке — то есть виде — мы получим данные из формы. Этот атрибут обязательно надо ставить, если через форму отправляются файлы, в остальных случаях не обязательно. Есть три варианта кодировки:
- `application/x-www-form-urlencoded` — это значение по умолчанию. Данные будут кодироваться так, что пробелы превратятся в знак `+`, а символы вроде кириллицы переведут в шестнадцатеричное значение. Например, так будет выглядеть имя Степан: `%D0%A1%D1%82%D0%B5%D0%BF%D0%B0%D0%BD` 🤡;
- `multipart/form-data` — вариант, который надо указать, если через форму отправляются файлы. В этом случае данные не кодируются;
- `text/plain` — в этом случае пробелы меняются на `+`, а остальные символы передаются без изменений.
- `method` — определяет, каким способом мы получим данные, которые ввёл пользователь. Есть два варианта:
  - `get` — ответы пользователя прикрепляются к URL в формате «параметр=значение», например «твой имейл=name@yandex.ru». Выглядит это так: `yandex.ru/form?name=Max&email=name@yandex.ru`. То есть, параметр — это что вы спрашиваете у пользователя, а значение — его ответ. Пары «параметр=значение» разделяются знаком `&`. Вариант `method="get"` используется по умолчанию, но у него есть ограничение: URL не должен получиться длиннее, чем 3000 символов.
  - `post` — данные из формы пакуются в тело формы и отправляются на сервер. В этом случае нет ограничений по объёму данных, поэтому этот способ подойдёт для заполнения базы данных или отправки файлов.
- `name` — уникальное имя формы. Пользователь его не увидит, зато скрипты смогут найти нужную форму.

- `novalidate` — если добавить этот атрибут, то браузер не будет проверять, корректно ли введён адрес почты или URL для тегов `<input type="email">` и `<input type="url">` соответственно. Обычно браузер проверяет, не пропустили ли вы `@` или `.ru`.

## Подсказки

💡 Никогда не используй `method="get"`, если хочется отправить конфиденциальные данные, потому что их можно легко прочитать в URL-ссылке, которая получится.

💡 Вариант `method="get"` удобен тем, что полученный URL с ответами можно сохранить в закладки. Например, пользователь может заполнить форму и поделиться ссылкой с результатами с кем-нибудь ещё.

## Ещё примеры

Вот простая форма:

```html
<!-- Эта форма отправит значение методом GET — мы получим URL с ответом -->
<form action="" method="get">
  <label for="GET-name">Имя первого гостя:</label>
  <input id="GET-name" type="text" name="name" />
  <input type="submit" value="Сохранить" />
</form>

<!-- Эта форма отправит данные методом POST -->
<form action="" method="post">
  <label for="POST-name">Имя второго гостя:</label>
  <input id="POST-name" type="text" name="name" />
  <input type="submit" value="Сохранить" />
</form>

<!-- Форма с булетами в рамочке -->
<form action="" method="post">
  <fieldset>
    <legend>Выберите прожарку</legend>
    <input type="radio" name="rare" id="radio" />
    <label for="radio">Rare</label>
    <input type="radio" name="medium" id="radio" />
    <label for="radio">Medium</label>
    <input type="radio" name="welldone" id="radio" />
    <label for="radio">Well Done</label>
  </fieldset>
</form>
```

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="html,result" data-user="max-grachev" data-slug-hash="VOwQPM" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="&amp;lt;form&amp;gt;">
  <span>See the Pen <a href="https://codepen.io/max-grachev/pen/VOwQPM">
  &lt;form&gt;</a> by Max Grachev (<a href="https://codepen.io/max-grachev">@max-grachev</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

Попробуем отправить данные, которые введёт пользователь, на почту. Для этого, вместо URL-ссылки, мы пропишем `action="mailto:html@yandex.ru"`. Ключевое слово `mailto:` позволяет отправить что угодно на электронную почту. Не забудь добавить атрибут `enctype="text/plain"` в теге `<form>`, чтобы письмо отображалось корректно:

```html
<html>
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>Встроим в тег FORM атрибут action</title>
  </head>
  <body>
    <form
      [action="mailto:html@yandex.ru](mailto:action=%22mailto:html@yandex.ru)"
      enctype="text/plain"
    >
      <div class="form-example">
        <label for="name">Ваше имя</label>
        <input type="text" name="name" id="name" required />
      </div>
      <div class="form-example">
        <label for="order">Что вы хотите заказать?</label>
        <input type="text" name="order" id="order" required />
      </div>
      <p><input type="submit" value="Сделать заказ" /></p>
    </form>
  </body>
</html>
```

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="html,result" data-user="max-grachev" data-slug-hash="dEydvz" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="&amp;lt;form&amp;gt; email">
  <span>See the Pen <a href="https://codepen.io/max-grachev/pen/dEydvz">
  &lt;form&gt; email</a> by Max Grachev (<a href="https://codepen.io/max-grachev">@max-grachev</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

## В работе

{% include "autors/ABatickaya/in-work.njk" %}\*

🛠 Формы — очень часто встречающийся элемент на сайтах. С их помощью пользователю предлагается оформить подписку, отправить запрос на цену, записаться на приём к врачу, авторизоваться на сайте и так далее.

Посвяти время детальному изучению форм. В том числе тому, как их стилизовать. Это отдельная боль. Стилизовать разные поля формы крайне муторно. А чтобы сделать это кроссплатформенно, нужно изрядно набить руку.

{% include "autors/vladimir/in-work.njk" %}\*

🛠 Я не помню, когда последний раз отправлял форму не на ajax. Это удобнее, потому что через ajax можно отправить в фоновом режиме практически любую форму, пока клиент занимается на сайте чем-то другим. А после успешной отправки вывести ему сообщение, что данные успешно отправлены. По мне это намного удобнее, чем каждый раз его отправлять на другую страницу, используя `<form>`. Плюс есть плюшки типа анимации и обработки ошибок.

{% include "autors/vladimir/autor.njk" %}
