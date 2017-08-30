# You-Dont-Need-jQuery

## 选择器查询
``` javascript
// jQuery
$('selector');

//Native
element = document.querySelectorAll('selector');
element = document.querySelector(selectors);
```
element 是一个 element 对象（DOM 元素）。
selectors 是一个字符串，包含一个或是多个 CSS 选择器 ，多个则以逗号分隔。

## class查询
``` javascript
// jQuery
$('.class');
// Native
element = document.querySelectorAll('.class');
element = document.getElementsByClassName(sepectors);
```

## id查询
``` javascript
// jQuery
$('#id');

// Native
element = document.querySelector('#id');
element = document.getElementById('id');
```

## 后代查询
``` javascript
// jQuery
$el.find('li');

// Native
el.querySelectorAll('li');
```

## 兄弟及上下元素

### 兄弟元素
``` javascript
// jQuery
$el.siblings();

// Native - latest, Edge13+
[...el.parentNode.children].filter((child) =>
  child !== el
);
// Native (alternative) - latest, Edge13+
Array.from(el.parentNode.children).filter((child) =>
  child !== el
);
// Native - IE10+
Array.prototype.filter.call(el.parentNode.children, (child) =>
  child !== el
);
```
### 上一个元素
```javascript
// jQuery
$el.prev();

// Native
el.previousElementSibling;
```

### 下一个元素
``` javascript
// next
$el.next();

// Native
el.nextElementSibling;
```

## Closest 获得第一个祖先元素
``` javascript
// jQuery
$el.closest(queryString);

// Native - Only latest, NO IE
el.closest(selector);

// Native - IE10+
function closest(el, selector) {
  const matchesSelector = el.matches || el.webkitMatchesSelector || el.mozMatchesSelector || el.msMatchesSelector;

  while (el) {
    if (matchesSelector.call(el, selector)) {
      return el;
    } else {
      el = el.parentElement;
    }
  }
  return null;
}
```