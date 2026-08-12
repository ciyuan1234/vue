# 第 1 课：创建应用与模板语法

## 本节要点

### 1. 引入 Vue
```html
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
```
这是 CDN 方式，适合快速体验。实际工程开发中会使用 Vite 脚手架（后续课程会学习）。

### 2. 创建应用
```js
const { createApp } = Vue
createApp({
  data() { ... },   // 数据
  methods: { ... }  // 方法
}).mount('#app')    // 挂载到 DOM
```
- `createApp` 创建应用实例
- `.mount('#app')` 将应用挂载到 `id="app"` 的元素上，挂载点内部的内容由 Vue 接管
- `data()` 返回的对象是响应式数据源，模板里可直接使用

### 3. 模板语法
| 语法 | 作用 | 示例 |
|------|------|------|
| `{{ }}` | 文本插值 | `{{ name }}` |
| `v-html` | 渲染真实 HTML（慎用，防 XSS） | `<div v-html="htmlContent">` |
| `v-bind` / `:` | 绑定属性 | `:src="picUrl"` |
| `v-if` / `v-else` | 条件渲染 | `<p v-if="isVip">` |
| `v-for` | 列表渲染 | `<li v-for="item in list">` |
| `@` / `v-on` | 事件绑定 | `@click="toggleVip"` |

### 4. 常用缩写
- `v-bind:href` → `:href`
- `v-on:click` → `@click`

### 5. 响应式原理（一句话版）
当 `data` 中的数据变化时，Vue 会自动更新页面上用到它的所有位置——这就是"响应式"，不需要手动操作 DOM。

## 动手练习
1. 在 `data` 里加一个 `age` 字段，在页面上用 `{{ }}` 显示出来
2. 给列表再加一门课程
3. 把图片换成你自己的头像链接

## 遇到的坑
- 挂载点 `#app` 必须存在，否则 Vue 找不到渲染位置
- 模板里不要写复杂逻辑，只写表达式（`v-if="a + b > 10"` 可以，但不要写 `v-if="functionCall()"` 这种带副作用的）
