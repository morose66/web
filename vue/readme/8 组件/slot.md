# 使用slot分发内容
在子组件中使用特殊的<slot>元素就可以为这个子组件开启一个插槽
* 单个slot
* 具名slot：给slot指定一个name后可以分发多个内容
* 注意 v-slot 只能添加在一个 \<template>

# 作用域插槽
让插槽内容能够访问子组件中才有的数据  
--既可以复用子组件的slot，又可以slot内容不一致  
作用域插槽的内部工作原理是将你的插槽内容包括在一个传入单个参数的函数里：
```
function (slotProps) {
  // 插槽内容
}
```
这意味着 v-slot 的值实际上可以是任何能够作为函数定义中的参数的 JavaScript 表达式。你也可以使用 ES2015 解构来传入具体的插槽 prop，如下：
```
<current-user v-slot="{ user }">
  {{ user.firstName }}
</current-user>
```