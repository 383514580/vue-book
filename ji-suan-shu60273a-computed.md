### 

### 什么是计算属性?

经过开发者逻辑计算后返回的一个**属性值**, 调用方式和调用data上的属性一样.

### 为什么用计算属性?

之前我们在讲解`v-bind`时候说data上定义的变量都可以在模板中直接调用, 但是当表达式比较复杂的时候就不建议直接写在模板中了, 而是放在计算属性中, 代码更优雅.

```
new Vue({
    el: '#app',
    data: {
        message: 'Hello World'
    },
    computed: {
        reverseMessage: function(){
            return this.message.split('').reverse().join('');
        }
    }

})
```

```
<div id="app">
    <p>表达式返回: {{message.split('').reverse().join('')}}</p>
    <p>计算属性返回: {{reverseMessage}}</p>
</div>
```

每当**this.message**发生变化, reverseMessage会自动重新计算新值, 绑定计算属性的元素也会响应变化.

**注意: **计算属性是通过函数定义的返回值, 为了帮助记忆提取2个关键词**函数/return.**

### 缓存

当参与计算的属性没有发生变化, 那么计算属性是自动缓存的, 无论是在模板还是js中调用计算属性他都不会重新计算, 这相比绑定表达式多次调用会被多次计算相比性能更优,试想想如果我们计算属性内部的逻辑是处理1000条产品信息.建议大家实际开发中优先使用计算属性.

### 只读的计算属性

刚刚我们说了计算属性是**有返回值的函数, **所以一般情况下他都是只读的**, **但是有些特殊情况也需要对计算属性赋值, 比如**v-mode**l绑定了计算属性那么就有写操作了, 这时候计算属性就不只是一个简单的有返回值的函数\(Function\)了, 而是一个对象\(Object\), 对象的**get**属性对应**有返回值的函数, **而**set去响应对计算属性写的操作: **

```
new Vue({
    el: '#app',
    data: {
        message: 'Hello World'
    },
    computed: {
        reverseMessage: {
            get: function(){
                return this.message.split('').reverse().join('');
            },

            set: function(value){
                alert('写操作');
            }
        }
    }

})
```

大家留意, 虽然可以对写操做进行响应, 但是就想标题说的**计算属性是只读的, **所以在**set**中一般我们做的并不是去改变计算属性的值, 而是去操作其他属性, 比如后面章节的自定义组件**v-model/vuex**中都会经常用到这个set,  现阶段只要知道有这个**set**就可以, 后续章节会慢慢给大家展开.

### 测验

实现一个autocomplete的input框

