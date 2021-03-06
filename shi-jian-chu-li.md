### v-on指令

```
<div v-on:click="fn"></div>
```

v-on后加':'加事件名来给元素绑定事件, 这里的'click'可以是任何js原生支持的事件, '='后面跟着对应的方法名.

### 定义方法

vue中所有的方法都定义在methods下,

```
new Vue({
    el: '#app',
    data: {
        count: 0
    },
    methods: {
        fn: function(){
            this.count++;
        }
    }
});
```

### 简写

```
<div v-on:click="fn"></div>
// 等价于
<div @:click="fn"></div>
```

v-on可以简写为@, 简单很多吧, 后面的例子中**v-on**都会**@**表示.

### 内联js逻辑

```
new Vue({
    el: '#app',
    data: {
        count: 0
    }
});
```

```
<button @click="count+1">加1</button>
```

当一些**逻辑比较简单**的时候, 我们可以不再methods中定义方法, 而是在模板的事件绑定中直接在'='后写上逻辑.

### $event

代表绑定事件元素的event对象.

注意这只是原生html标签是上$event才表示event, 如果是自定义组件是不同的.

### 测验:

做一个按钮, 每次点击+1或者计算器

### 事件修饰符

简单的说就是可以在模板中是用v-on的时候, 通过在"v-on"后加".xxx", 实现**event.preventDefault\(\) **或 **event.stopPropagation\(\)等常见操作.**

```
<!-- 阻止单击事件冒泡 -->
<a v-on:click.stop="doThis"></a>

<!-- 提交事件不再重载页面 -->
<form v-on:submit.prevent="onSubmit"></form>

<!-- 修饰符可以串联 -->
<a v-on:click.stop.prevent="doThat"></a>

<!-- 只有修饰符 -->
<form v-on:submit.prevent></form>

<!-- 添加事件侦听器时使用事件捕获模式 -->
<div v-on:click.capture="doThis">...</div>

<!-- 只当事件在该元素本身 (比如不是子元素) 触发时触发回调 -->
<div v-on:click.self="doThat">...</div>
```

事件修饰符有5个:

.stop: 阻止事件冒泡

.prevent: 阻止浏览器默认行为, 比如页面滚动等.

.capture: 翻转事件传播方向, 本来事件是按照最内元素到外元素执行的, 叫事件冒泡,capture正好相反, 让元素从外到内传播事件.

.self 元素只在绑定的元素上执行

.once: 绑定的事件只执行一次, 之后失效.

### 键值修饰符\(键盘\)

在监听键盘事件时，我们经常需要监测常见的键值。Vue 允许为 v-on 在监听键盘事件时添加关键修饰符：

```
<!-- 只有在 keyCode 是 13 时调用 vm.submit() -->
<input v-on:keyup.13="submit">
```

记住所有的 keyCode 比较困难，所以 Vue 为最常用的按键提供了别名：

```
<!-- 同上 -->
<input v-on:keyup.enter="submit">
<!-- 缩写语法 -->
<input @keyup.enter="submit">
```

全部的按键别名：

.enter/.tab/.delete \(捕获“删除”和“退格”键\)/.esc/.space/.up/.down/.left/.right

### 按钮修饰符\(鼠标\)

用来响应每一个鼠标按键

```
<!-- 鼠标右键触发 -->
<input v-on:click.right="submit">
```

全部的修饰符: .left/.right/.middle

### 修饰键\(鼠标+键盘\)

```
<!-- Alt + C -->
<input @keyup.alt.67="clear">
<!-- Ctrl + Click -->
<div @click.ctrl="doSomething">Do something</div>
```

关于mac和windows下的区别, 由于不常用, 不在此展开介绍, 有兴趣的同学可以翻看[文档](https://cn.vuejs.org/v2/guide/events.html#修饰键)



