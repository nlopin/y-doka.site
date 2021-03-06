---
title: Комментарий в CSS
name: css-comments
autor: ABatickaya
co-autors:
  - furtivite
designers:
contributors:
summary:
  - комментарии
---

## Кратко

Комментарии в CSS нужны, чтобы комментировать отдельные куски кода или быстро временно отключать свойства без удаления их из кода.

Комментарии не влияют на работу остального кода, а значит невозможно увидеть их, не заглядывая в файл со стилями.

Часто комментарии используются для визуального отделения блоков стилей друг от друга. Например, чтобы отделить стили для шапки сайта от стилей для остальной страницы.

## Пример

В CSS существует два вида комментариев: однострочные и многострочные

```css
/*
	Я многострочный комментарий.
	Внутри меня можно переносить текст на новые строки и он всё равно будет скрыт.
*/

.selector {
  text-align: center; // с однострочный комментарий
}
```

## Как пишется

Многострочный комментарий оформляется при помощи двух пар символов, `/*` и `*/`:

```css
/* Любой текст */
```

По желанию или в соответствии с принятым в вашей команде кодстайлом после открывающих символов можно перенести текст на новую строку, а закрывающую пару поставить на новой строке. Как-то так:

```css
/*
	Я помню чудное мгновенье:
	Передо мной явилась ты,
	Как мимолетное виденье,
	Как гений чистой красоты.
*/
```

Многострочные комментарии ещё иногда называют **блочными**.

Если нужно закомментировать какое-то свойство внутри CSS-правила, то пригодится однострочный комментарий. К тому же он проще оформляется, понадобится всего лишь две наклонные черты:

```css
// Однострочный комментарий
```

## Как это понять

Если вы пишете многострочный комментарий, то у него обязательно должно быть начало и конец. Открывать блок комментария нужно при помощи `/*`, а закрывать блок комментария при помощи зеркальной конструкции `*/`.

С однострочными комментариями всё проще, их нужно только открыть, а закрывать не нужно. `//` и погнали. Но за этой простотой скрывается большой подводный камень — с помощью однострочных комментариев можно закомментировать только куски кода. Если поместить после открывающих чёрточек текст, то интерпретатор не воспримет его как код, посмотрит как бы сквозь него и закомментирует следующую за текстом команду в коде.

С помощью однострочных комментариев можно закомментировать только куски кода

## Ещё пример

Как выглядит закомментированное свойство:

```css
.selector {
  // height: 100%;
  width: 100%;
}

.selector {
  /* height: 100%; */
  width: 100%;
}

.selector {
  // вот так уже нельзя
  height: 100%;
  width: 100%;
}
```

А вот так можно закомментировать целый блок:

```css
/* .selector {
	width: 100%;
	height: 100%;
} */
```

А так принято отделять стили для разных частей страницы друг от друга:

```css
/* Header */
.header {
  display: flex;
}
/* End Header*/

/* Footer */
.footer {
  .background-color: pink;
}
/* End Footer */
```

В таком коротком куске кода комментарии избыточны и смотрятся грязно. Но когда файл со стилями состоит из тысяч строк, то такая навигация удобна.

## Подсказки

💡 Не злоупотребляй комментариями. Не нужно пояснять всё подряд. Пиши комментарий только там, где без подсказки никак не понять что происходит.

💡 Но и не игнорируй комментарии. Не молчи там, где есть что сказать. Например, ты использовал `!important` в коде (напомним, что это крайне нежелательная практика), но в данном случае он крайне важен и необходим. Поясни своё решение чтобы следующий разработчик не сломал всё, удалив нежелательный элемент.

💡 Чтобы в редакторе быстро закомментировать или раскомментировать строку нажми `Ctrl` + `/` или `Cmd` + `/`.

## В работе

🛠 Иногда в процессе разработки нужно быстро проверять какую-то гипотезу. Не хочется сгоряча удалять блок кода, вымученного кровью и потом. Просто закомментируй подозрительные строки. Если причина не в них, то расскомментируешь. Удалить всегда успеешь.

🛠 Удаляй все закомментированные свойства перед деплоем — публикацией проекта. Комментарии — утилитарная штука. Они полезны, но сильно загружают код и затрудняют его чтение. Если это не информационные комментарии, а следы экспериментов — удаляй их.

🛠 Иногда можно встретить в начале файла своеобразное оглавление, поясняющее в какой части файла искать стили для того или другого блока. Если у вас очень большой файл, то стоит попробовать такой подход. Он может оказаться удобным.

{% include "autors/furtivite/in-work.njk" %}

🛠 Как всегда, стоит удалить все те комментарии, которые не должен видеть заказчик или пользователь конечного продукта, перед деплоем. Все, что неактуально, решено, касается внутренних процессов в вашей компании и не будет использоваться в дальнейшем — смело под нож!

{% include "autors/ABatickaya/autor.njk" %}
