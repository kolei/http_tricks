# Фичи верстки

<details>

<summary>Динамический бутстрап-алерт</summary>

Создается в js-коде, автоматически уничтожается через 5 сек

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
