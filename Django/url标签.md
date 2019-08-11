# url标签
- a标签在进行跳转的时候，可以直接添加/book这样的
```html
<a href="/book">
```
- 这样在跳转时，会自动在当前url后面添加/book
- 但是这样会有一个问题，就是修改的时候两边都要修改。
- 所以django提供了url和反转一样提供映射


- url标签
```
{%url 'name'%}
```
- 实例：
```
<ul class="mune-ul">
    <li><a href="{% url 'home:link' %}">Links</a></li>
    <li><a href="{% url 'book:book_home' %}">Books</a></li>
    <li><a href="{% url 'home:note' book_id='1' %}">Notes</a></li>
    <li><a href="{% url 'home:home' %}">Home</a></li>
</ul>
```

- 注意：
    - url后面有空格
    - 名称要引号
    - 名称要与urls文件中的name=相同
    - context传参数 在后面加空格然后参数名=