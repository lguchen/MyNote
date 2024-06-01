```vue
<style scoped> </style>
```

scoped 属性是 [HTML5](https://so.csdn.net/so/search?q=HTML5&spm=1001.2101.3001.7020) 中的新属性，是一个布尔属性。如果使用该属性，则样式仅仅应用到 style 元素的父元素及其子元素。

**作用**：实现组件的私有化，不对全局造成样式污染，表示当前style属性只属于当前模块。

**原理**：scoped会在DOM结构及css样式上加上唯一性的标记【data-v-something】属性，即CSS带属性[选择器](https://so.csdn.net/so/search?q=选择器&spm=1001.2101.3001.7020)，以此完成类似作用域的选择方式，从而达到样式私有化，不污染全局的作用。

scoped使用虽然方便但是我们需要慎用，因为在我们需要修改公共组件（三方库或者项目定制的组件）的样式的时候，scoped往往会造成更多的困难，需要增加额外的复杂度。

以elementUI为例，在使用scoped会出现 CSS 设置不起效的问题，无法通过 CSS 修改组件的样式。可以使用下面的方法来解决。

（1）使用 >>> 可以穿透 scoped 属性，修改其他第三方组件的样式。
```css
外层 >>> 第三方组件{} 如：.name-input >>> .el-input_inner{}
```

