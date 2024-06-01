## 原生前端登录表单

```html
<!DOCTYPE html>
<html>
  <head>
    <title>登录页面</title>
  </head>
  <body>
    <div class="login-container">
      <h1>登录</h1>
      <form>
        <input type="text" placeholder="用户名" />
        <input type="password" placeholder="密码" />
        <input type="submit" value="登录" />
      </form>
    </div>
  </body>
  <style>
      * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
      }

      body {
        background-color: #f2f2f2;
        font-family: Arial, sans-serif;
      }

      .login-container {
        width: 400px;
        height: 300px;
        margin: auto;
        background-color: #fff;
        border-radius: 10px;
        box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
        padding: 20px;
        display: flex;
        left: 50%;   /* div整体居中*/
        top: 50%;   /* div整体居中*/
        position: absolute;  /* div整体居中*/
        align-items: center;
        justify-content: center;
        transform: translate(-50%,-50%);/* div整体居中*/
        flex-direction: column;
      }

      h1 {
        margin-bottom: 20px;
        color: #333;
      }

      input[type="text"],
      input[type="password"] {
        width: 100%;
        padding: 10px;
        margin-bottom: 10px;
        border: none;
        border-radius: 5px;
        box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.2);
      }

      input[type="submit"] {
        width: 100%;
        background-color: #4CAF50;
        color: #fff;
        padding: 10px;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        transition: all 0.3s ease;
      }

      input[type="submit"]:hover {
        background-color: #3e8e41;
      }
    </style>
</html>
```



## css代码详解

这段HTML代码包含了CSS样式，用于设置页面的外观和布局。具体说来，它定义了以下样式：

- `*`：通配符，用于选择所有元素。
- `box-sizing: border-box;`：设置盒模型为 border-box，即将 padding 和 border 计算在内，不影响元素的宽度和高度。
- `margin: 0; padding: 0;`：将页面中所有元素的外边距和内边距都设为0。
- `body`：选择网页中的 body 元素。
- `background-color: #f2f2f2;`：设置背景颜色为灰色。
- `font-family: Arial, sans-serif;`：设置字体为 Arial 或其他无衬线字体。
- `.login-container`：选择 class 为 login-container 的元素。
- `width: 400px; height: 300px;`：设置容器的宽度和高度。
- `margin: auto;`：将元素水平居中。
- `background-color: #fff;`：设置容器的背景色为白色。
- `border-radius: 10px;`：设置容器圆角为10像素。
- `box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);`：设置容器的阴影效果。
- `padding: 20px;`：设置容器内部的 padding 为20像素。
- `display: flex;`：将容器设置为弹性布局
- `left: 50%; top: 50%;`：将元素的左上角定位在页面的中心位置。
- `position: absolute;`：将元素的定位类型设置为绝对定位。
- `align-items: center; justify-content: center;`：将子元素垂直和水平都居中。
- `transform: translate(-50%, -50%);`：将元素向左上方移动自身宽度和高度的一半，以使其完全居中。
- `flex-direction: column;`：设置主轴方向为垂直方向。
- `h1`：选择页面中的 h1 元素。
- `margin-bottom: 20px; color: #333;`：设置标题的下边距为20像素，颜色为深灰色。
- `input[type="text"], input[type="password"]`：选择类型为 text 和 password 的 input 元素。
- `width: 100%; padding: 10px; margin-bottom: 10px;`：设置输入框的宽度为100%，内边距为10像素，下边距为10像素。
- `border: none; border-radius: 5px; box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.2);`：去除输入框的边框，设置圆角为5像素，添加一个轻微的阴影效果。
- `input[type="submit"]`：选择类型为 submit 的 input 元素。
- `background-color: #4CAF50; color: #fff;`：设置按钮的背景色为绿色，文字颜色为白色。
- `padding: 10px; border: none; border-radius: 5px; cursor: pointer; transition: all 0.3s ease;`：设置按钮的内边距为10像素，去除边框样式，设置圆角为5像素，将鼠标指针样式设置为手形，添加过渡效果。
- `input[type="submit"]:hover`：当鼠标悬停在按钮上时。
- `background-color: #3e8e41;`：将按钮的背景色更改为深绿色。