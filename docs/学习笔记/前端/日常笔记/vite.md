# Vue3+TypeScript+Vuetify+Vite 实现动态主题切换



## Vue3+TypeScript+Vuetify+Vite 实现动态主题切换

### 创建项目

- 创建一个 Vite 项目

```
npm create vite@latest
```

- 输入项目名称

```
? Project name: vue3-ts
```

- 选择vue

```
? Select a framework: » - Use arrow-keys. Return to submit.
    vanilla                                                
>   vue                                                    
    react                                                  
    preact                                                 
    lit                                                    
    svelte
```

- 选择ts

```
? Select a variant: › - Use arrow-keys. Return to submit.
    JavaScript
❯   TypeScript
    Customize with create-vue ↗
    Nuxt ↗
```

下一步就是创建完了。

### 安装Vuetify

- 我们进到项目里面安装vuetify

```
vue add vuetify
```

- 选择Vite Preview (Vuetify 3 + Vite)

```
✔  Successfully installed plugin: vue-cli-plugin-vuetify

? Choose a preset:
  Vuetify 2 - Configure Vue CLI (advanced)
  Vuetify 2 - Vue CLI (recommended)
  Vuetify 2 - Prototype (rapid development)
❯ Vuetify 3 - Vite (preview)
  Vuetify 3 - Vue CLI (preview)
```

- 安装完成

```
✔  Successfully invoked generator for plugin: vue-cli-plugin-vuetify
```

- 启动服务器

```
npm run dev
```

访问: http://localhost:3000/

![图片](https://mmbiz.qpic.cn/mmbiz_png/wZydIHGg4BKSKlibJRCWLVCPCnyfE0vOzNKvkAXcaWv68PJSgEgr71zL5etGecmosBnEtfJqAzaVWysGhcgOPug/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)image.png

### 动态主题切换

在`App.vue`文件里：

```
<template>
  <v-app :theme="theme">
    <v-main>
      <v-btn @click="toggleTheme">点击切换主题</v-btn>
      <HelloWorld/>
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
import {ref} from 'vue'
import HelloWorld from './components/HelloWorld.vue'

const theme = ref('light')
const toggleTheme = () => theme.value = theme.value === 'light' ? 'dark' : 'light'
</script>
```

![图片](https://mmbiz.qpic.cn/mmbiz_png/wZydIHGg4BKSKlibJRCWLVCPCnyfE0vOz8F09p5xFtHJLG2yxu9WTEDtSVibmEvmSIWH1YQ60ibIXOhLmiag7ZUhDw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)image.png

### 自定义主题

我们可以在`vuetify.ts`文件里面配置主题颜色：

```
//vuetify.ts
import { createVuetify } from 'vuetify'

const light = {
    dark: false,
    colors: {
        background: '#808080',
        surface: '#6200EE',
        primary: '#6200EE',
        'primary-darken-1': '#3700B3',
        secondary: '#03DAC6',
        'secondary-darken-1': '#018786',
        error: '#B00020',
        info: '#2196F3',
        success: '#4CAF50',
        warning: '#FB8C00',
    }
}

const dark = {
    dark: true,
    colors: {
    }
}

export default createVuetify({
    theme: {
        defaultTheme: 'light',
        themes: {
            light,
            dark
        }
    }
})
```

效果：

![图片](https://mmbiz.qpic.cn/mmbiz_png/wZydIHGg4BKSKlibJRCWLVCPCnyfE0vOzrmzMVHCEIE3iaFfwVhYSWk7x7zWDDsSKjZXQZV3Brt00wF2uc8R2ibxw/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)