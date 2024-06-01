#### 前端调用百度地图api报错： 

```html
api?v=2.0&ak=4pCGzY7p3OGfqZe3YlLQFg4BGTjqjUhE:1 A parser-blocking, cross site (i.e. different eTLD+1) script, https://api.map.baidu.com/getscript?v=2.0&ak=4pCGzY7p3OGfqZe3YlLQFg4BGTjqjUhE&services=&t=20230104104957, is invoked via document.write. The network request for this script MAY be blocked by the browser in this or a future page load due to poor network connectivity. If blocked in this page load, it will be confirmed in a subsequent console message. See https://www.chromestatus.com/feature/5718547946799104 for more details.
```

修改api引用url，api改成getscript就行
//修改前

```html
<script type="text/javascript" src="https://api.map.baidu.com/api?v=2.0&ak=####################"></script>
```

//修改后

```html
<script type="text/javascript" src="https://api.map.baidu.com/getscript?v=2.0&ak=##########################"></script>
```

