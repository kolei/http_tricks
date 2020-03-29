# Фичи верстки

* [Динамический бутстрап-алерт](#Динамический-бутстрап-алерт)
* [DataTable](#DataTable)

## DataTable

<details>
<summary>добавление класса в созданную строку</summary>

```js
// метод node() возвращает добавленную ноду
let node = table.row.add(
  [item.id, item.name, `${item.firm_name} (${item.firmId})`, item.parser_yandex]
).draw().node();

// 4-й ячейке строки добавляется атрибут
$(node).find('td').eq(3).attr('contenteditable', 'true');

// для строки (tr) задается класс
$(node).addClass('non-active');
```

</details>

<details>
<summary>редактируемая ячейка с отслеживанием изменений при выходе</summary>

```js
//let node = table.row.add([...]).draw().node(); - см предыдущую фичу

var that = $(node).find('td').eq(3);

that.attr('contenteditable', 'true');
that.attr('old-value', item.parser_yandex);
that.focusout(()=>{
  var old_value = $(that).attr('old-value') || '';
  var new_value = $(that).text();
  if(old_value!=new_value){
    console.log('wow');
  }
});
```

</details>

## Динамический бутстрап алерт

<details>
<summary>

* создается в js-коде
* автоматически уничтожается через 5 сек
* расположен вверху экрана

</summary>

```css
#alert_placeholder {
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 100;
}
```

```http
<div id="alert_placeholder"></div>
```

```js
function show_alert(message,alerttype) {
  $('#alert_placeholder').append(`<div id="alertdiv" class="alert ${alerttype}"><a class="close" data-dismiss="alert">×</a><span>${message}</span></div>`);
  setTimeout(function() {
    $("#alertdiv").remove();
  }, 5000);
}
```

</details>
