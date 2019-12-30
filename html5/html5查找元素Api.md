## HTML5查找元素的 Api


### 旧有选择元素 API


- `getElementById()` 根据指定的 `id` 特性值查找并返回元素。 `<div id='foo'>` `getElementById('foo')`

- `getElementsByName()` 返回所有 `name` 特性为指定值的元素。 `<input type='text' name='foo'>` `getElementsByName('foo')`

- `getElementByTagName()` 返回所有标签名称与指定值相匹配的元素 `<input type='text'/>` `getElementsByTagName('input')`


### HTML5 新增 Selectors API

selectors 是根据 css 里面的选择器来选择获取元素的。CSS树查找会比DOM树查找速度要更快。

- `querySelector()` 根据指定的选择器规则，返回在页面中找到的第一个匹配元素。 `querySelector('input.error')` 参数可以填多个选择器，不过满足其中一个就会返回元素。

- `querySelectorAll()` 根椐指定规则返回页面中所有相匹配的元素。 `querySelector('#results td')`， 参数也是可以填多个选择器，需要同时满足匹配才会返回。