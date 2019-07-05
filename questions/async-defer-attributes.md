<!-- ### What are `defer` and `async` attributes on a `<script>` tag? -->

### <code>script</code> 标签上 <code>defer</code> 与 <code>defer</code> 属性的区别？

#### Answer

<!-- If neither attribute is present, the script is downloaded and executed synchronously, and will halt parsing of the document until it has finished executing (default behavior). Scripts are downloaded and executed in the order
they are encountered. -->

如果两个属性都不存在，则同步下载并执行脚本，并停止解析文档，直到它完成执行（默认行为）。脚本会按照遇到的顺序下载并执行。

<!-- The `defer` attribute downloads the script while the document is still parsing but waits until the document has finished parsing before executing it, equivalent to executing inside a `DOMContentLoaded` event listener. `defer` scripts will execute in order. -->

<code>defer</code>属性在文档仍在解析时下载脚本，但在执行之前一直等到文档完成解析，相当于在<code>DOMContentLoaded</code>事件监听器内执行。所有<code>defer</code>脚本将按顺序执行之后触发<code>DOMContentLoaded</code>。

<!-- The `async` attribute downloads the script during parsing the document but will pause the parser to execute the script before it has fully finished parsing. `async` scripts will not necessarily execute in order. -->

<code>async</code>属性在解析文档时下载脚本，但会在完全解析之前暂停解析器执行脚本。<code>async</code>脚本不一定按顺序执行。

注：以上属性仅在<code>script</code>具有<code>src</code>属性时有效。（例如非内联）

```html
<script src="myscript.js"></script>
<script src="myscript.js" defer></script>
<script src="myscript.js" async></script>
```

#### Good to hear

<!-- * Placing a `defer` script in the `<head>` allows the browser to download the script while the page is still parsing, and is therefore a better option than placing the script before the end of the body.
* If the scripts rely on each other, use `defer`.
* If the script is independent, use `async`.
* Use `defer` if the DOM must be ready and the contents are not placed within a `DOMContentLoaded` listener. -->

* 在<code><head></code>中放置一个<code>defer</code>脚本允许浏览器在页面仍在解析时下载脚本，因此比在<code></body></code>前放置脚本更好；
* 如果<code>scripts</code>的执行需要依赖彼此，可以使用<code>defer</code>；
* 如果<code>scripts</code>的执行各自独立，可以使用<code>async</code>；
* 如果<code>scripts</code>的执行必须需要<code>DOM</code>已经解析完成，但是又不必须在<code>DOMContentLoaded</code>的事件侦听器中，可以使用<code>defer</code>。

##### Additional links

<!-- Whenever possible, link a more detailed explanation. -->

* [async vs defer attributes](http://www.growingwiththeweb.com/2014/02/async-vs-defer-attributes.html)

<!-- tags: (html) -->

<!-- expertise: (1) -->
