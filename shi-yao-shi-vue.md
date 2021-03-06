## vue是什么?

概括的说vue是一个js框架,  可以让你的代码脱离凌乱的dom操作api, 给了你一套规范, 让你的代码更容易维护,  代码可复用性更高, 可以做出app体验的页面, 这里先不多说, 后面会有和jq代码的对比来让我们更了解vue.

## 为什么学vue?

通过招聘网站数据和用人单位的反馈, 我们发现在北上广等一线城市从2016年起对前端程序员的要求都会加入一项叫"会vue/react/angular任意框架者优先", 到了2017年我们再看, 所有的企业都已经把这个"优先"变成了必须. 如果你期望去北上广发展, 你得学vue, 如果你是在校大学生想要毕业入职一线互联网公司你也的学vue, 其实即便是大三的学生也可以用把自己的设计构思结合vue来做一个spa当做毕业设计.

[拉钩网](https://www.lagou.com/jobs/3461022.html) [高思教育](https://www.lagou.com/jobs/3681535.html) [百度](https://www.lagou.com/jobs/3739554.html)

再看哈尔滨, 2017年开始越来越多的前端人员和企业知道vue, 而且也给vue画上了高薪的等号. 哈尔滨现在是前端需求爆发的初期, 如果有工作经验的同学现在看哈尔滨的招聘信息能看出来前端岗位每年都在增加, 同时薪资也在越来越高.

[公司1](#) [公司2](#)

## 为什么vue一类的框架越来越受企业欢迎?

对于创业公司一般起步的产品都是信息类\(比如知乎/微博/商城类, 并没有太多对底层硬件的依赖的应用\)的ios+安卓客户, 用vue类的框架可以做出spa页面, 然后只需要套壳就可以生成ios/安卓客户端,  同时只需要维护一套代码即可, 大大缩短了上线时间, 对于创业公司可谓下对了药, 要知道创业初期老板可是最着急上线的.

对于已经有成熟的互联网公司, 他们更看重的是用户体验,  自然对产品的流畅程度有了更高的要求, 套壳应用的性能受所在手机的浏览器性能的影响, 在复杂操作的页面自然不能和原生比, 好消息是随着前端技术的不断探索, 借助nodejs前端们可以让js生成ios/安卓的代码,比如阿里的weex, fb的react-native都可以直接用原生js的语法生成原生应用, 这里的weex就是淘宝用vue的api设计的.

最近火的微信小程序, 其代码就是js. 微信小程序的api也是按照vue来设计的, 也就是学会了vue, 学weex和小程序就会非常快. 之所以这2者在用vue的api也正是因为vue设计的api比较易懂上手快.

### vue和jq有什么区别?

接下来我们写2个例子对比下vue和jq的不同.  vue是一个框架, 可以让你写更少的代码, 同时代码更容易维护和迭代, 在vue中我们只需要做数据的处理, 不做dom的操作, 控制显示隐藏.

jq:

```Vue
<div id="app">       
    <div id="dialog">xxx</div>
    <button onclick="toggle">显示/隐藏</button>
</div>
```

```js
$(function(){
    var $dialog = $('#dialog');
    var $button = $('#button');

    function toggle(){
        var isVisible = $dialog.is(':visible');
        if(isVisible){
            $dialog.hide();
        } else {
            $dialog.show();
        }
    };
});
```

vue:

```
<div id="app">   
    <div v-show="">xxx</div>
    <button v-on="toggle">显示/隐藏</button>
</div>
```

```js
new Vue({
    el: '#app',
    data: {
        isVisible: false
    },
    methods: {
        toggle: function(){
            this.isVisible = !this.isVisible;
        }
    }
})
```

### vue和jq的增删改查对比

**vue:**  
[https://jsfiddle.net/\_russell997/kmb0q8og/9/](https://jsfiddle.net/_russell997/kmb0q8og/9/)

**jq:**

[https://jsfiddle.net/\_russell997/wjb5atk8/12/](https://jsfiddle.net/_russell997/wjb5atk8/12/)

## vue让你的代码可复用

vue最核心的概念就是组件, 就是把js/css/html抽象成一个标签, 这样通过标签上自定义的属性就可以在页面进行控制这个封装的组件.

[对话框组件](https://jsfiddle.net/yyx990803/mwLbw11k/?utm_source=website&utm_medium=embed&utm_campaign=mwLbw11k)

只看调用组件部分

```html
<div id="app">
  <button id="show-modal" @click="showModal = true">Show Modal</button>
  <!-- 调用组件 -->
  <modal v-if="showModal" @close="showModal = false">
    <h3 slot="header">custom header</h3>
  </modal>
</div>
```

## 大公司的vue产品

京东金融/新浪金融/饿了么等, 看下[新浪金融](http://jr.sina.cn/public/sina_finance/index.html#/index), j新浪金融是我一前同事做的, 他是今年3月开始学的vue, 6月去了新浪, 去了就开始主导金融频道的前端开发, 2个月上线了这个spa\(无刷新页面\), 同时带其小组的其他3个前端学会用vue.

学习用vue之前他本来就是很优秀的前端, jq/css3/都很熟练, 所以说上手vue基本很容易, 所以大家如果有jq的经验那么学vue会更简单, 而且现在一旦学会了vue在前端里基本就是20%的程序员, 一般公司都会让你去带队.

对比jq要操作dom, vue完全不需要, 不用记住那么多jq操作dom的api\(只需要学会几个js的api即可,getBoundingClientRect/querySelector等等\), 只需要做数据处理就行, 这样我们上手写代码的质量就很高\(上面的2个例子\),  哪个单位不想要写代码质量高/可维护的程序员.

## jq还用不用了?

如果单位还需要兼容ie低版本的浏览器, jq用来做交互少的活动页面最适合, 比如[fullpage](https://alvarotrigo.com/fullPage/#firstPage)类型的广告页面和企业官网. 如果只是兼容高版本浏览器的活动页可以直接用原生js, 这样我们页面的体积会更小\(**vue**: 28.96kb min+gzip / **jquery-3.2.1.min** : 30.63kb min+gzip\), 因为高版本浏览器支持querySelector\(\)和css3动画.  
在vue学习初期, 最有些不愿放弃用jq的2个原因就是如何获取dom尺寸信息和异步请求,获取元素的位置/尺寸等, 可以用js原生的getBoundingClientRect\(\), 异步请求\(ajax\)用axios.js\(1k min+gzip\), 懂了这2个只是点, jq就可以完全不用了, 我这2年的开发都没用再用过jq了.

## jq有那么多插件, vue有吗?

可能大家会担心, vue的组件有没有jq的插件那么丰富, 实际上vue的组件有很多, 完全可以覆盖所有开发需求, 比如现在最火的[饿了么桌面端组件库](http://element.eleme.io/)和[移动端组件库vux](https://vux.li/#/), 以及一些vue[官方收集的组件库](https://github.com/vuejs/awesome-vue), 如果上述组件仍然不能满足需求, 你也可以在vue的项目引入jq插件, 当然这是在是在不得不的情况下, vue可以和jq同时被调用, 但是为了规范, jq的代码也要写在vue指定的地方\(mounted钩子中, 意思就是vue/组件加载后运行此处代码\);

```javascript
new Vue({
    el: '#mount-node',
    mounted: function{
        $('body').css({background: '#ccc'});
    }
});
```

## 现在还有react/angular, 为什么选择vue?

在座有心的应该知道现在除了vue还有react/angular2大数据驱动框架. 我说下为什么没选择学他们.  
从上手程度上讲, vue有一个标签叫做渐进式框架, 渐进式的意思就是我们可以把vue直接通过浏览器script标签在html中引入, 可以当做一个js插件来使用\(可以和jq并存\), 方便大家慢慢深入了解学习vue, 如果对vue有了解的同学知道, 整套vue开发还有其他技术点\(webpack/scss/es6\), 不过我们可以渐进的各个击破.  
反观react上手需要学习jsx语法, angular上手需要学习ts, 虽然angular支持标准的js, 但是官网的教程都是基于ts的, 所以想用好angular还要同时学好ts.

#### react

```javascript
<script crossorigin src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
class HelloMessage extends React.Component {
  render() {
    return (
      <div>
        Hello {this.props.name}
      </div>
    );
  }
}

ReactDOM.render(
  <HelloMessage name="world" />,
  mountNode
);
```

#### angular2基于\(ngserver\)

```javascript
import { Component } from '@angular/core';
@Component({
  selector: 'mount-node',
  template: `<h1>Hello {{name}}</h1>`
})
export class AppComponent { name = 'world'; }
```

#### vue

```javascript
<script src="https://unpkg.com/vue"></script>
new Vue({
    el: '#mount-node',
    template: '<h1>Hello {{name}}</h1>',
    data: {
        name: 'world'
    }
});
```

所以总结一下选择vue就是因为他学习曲线平缓, 而后期高度3大框架一致, 均有router/state管理/ssr\(服务端渲染\)/vnode\(虚拟dom\)等概念. 学会vue后如果想学react/angular都会变的简单, 因为3者核心的概念一致, 跟甚至想学微信小程序也会变得简答, 因为**微信**小程序的语法和概念和vue相似度90%以上.  
更详尽的对比可以看vue官网的[一篇文章](https://cn.vuejs.org/v2/guide/comparison.html)

说在最后: 这个时代的前端框架不会有什么一统江湖, 因为3大框架的卖点不同, vue卖点是上手简单, 知乎上大v对他的口碑好, 作者[尤雨溪](https://baike.baidu.com/item/尤雨溪/2281470?fr=aladdin)和这几个前端大v关系都不错, 所以可以放心vue在大公司的推广; react卖点是fb出品, 且fb上很多网站都是基于react的, 不怕项目突然死亡, 不过前段时间的react开源协议问题也在知乎头条上热了3天, 百度/阿里等大公司都说要放弃使用react了, 最后还是fb回头是岸继续免费react, 取消因为公司业务逻辑和fb相同而侵权的问题, 才平息风波, 虽说vue是个人开发的, 但是你知道吗jq也是个人开发的, [John Resig](https://baike.baidu.com/item/John Resig/6336344?fr=aladdin), 所以我觉得vue也很稳定, 毕竟作者已经全职开发vue并且建立了团队, 他每个月通过vue可以赚到2/3w美金, angular卖点是概念亲服务端开发人员, 因为他的创建者是java程序员.

最终很难有个框架能一统江湖, 所以我们学哪个都一样, 大公司不同的部门对3大框架的选择都不一样, 所以任何一个精通了, 都会给你开通去大公司的门. 而且由于3者概念基本一致, 学会了任何一个再去学另一个都会很简单.

## 关于IE6/7/8

淘宝/天猫都已经不再支持ie6/7, 我最近2年工作单位也都不在要求支持ie6/7, 虽说要要求支持ie8, 但是如果你去的单位要求vue, 那么自然他只要求兼容到ie9, 再者现在企业都是主移动端开发, 手机浏览器vue都支持. pc端后台单位都不会要求兼容ie的, 谷歌好使就行.

## 学点nodejs

仔细看招聘信息都会发现用人单位特别青睐会服务端的前端, 当然不是要前端去写后端逻辑, 只是了解写概念,多亏了nodejs, 前端不需要学新的语法就可以写服务端的应用, 而且对自己前端工作也非常有利, 所以我会通过教大家用mock.js结合express来写一些服务端代码来模拟真实接口返回数据.

在企业工作的时候, 前端可以在和服务端商定数据结构后, 自己写出假数据来进行单元测试, 而不需要等待后端, 效率大大提升, 这是任何领导都喜欢的事情.

## 只学vue吗?

#### scss

当我们学会了使用vue,  我们会发现程序可以写的更好, 比如我们可以使用**scss**把css变成有逻辑的支持变量的, 让我们做皮肤变的非常简单.

```scss
$color:#69c;
.modal{
    .modal-header{
        color: $color
    }
    .modal-body{
        color: $color
    }

    .modal-footer{
        color: $color
    }
}
```

#### es6

知道吗? 原来写js代码可以写的更简单, 我写一篇关于[es6常用api的小总结](https://github.com/383514580/Notes/blob/master/ES6提升效率的几个小技巧.md)

#### webpack

自从nodejs出现了, 前端工具异常的火爆, 有百度的解决方案fis, 以及使用更灵活的grunt/gulp, 不过当webpack出现后慢慢成为了唯一的主流, vue/react/angular3者官网的脚手架工具都是基于webpack的. webpack让我们可以把js/css/image/font等资源统统当做js来管理, 让代码更规范, 管理更简单.  
补充: 更神奇的是, 以后写代码在也**不需要f5**了\(编译下组件库展示\), 通过scoket技术可以让**代码热更新**.

## 编码规范

虽然vue可以让代码的可读性变的更高, 但是我们还是建议大家写注释让文档更清晰, 所以届时会给大家一套完善的代码标准.

## 学会了做什么?

做一个商城前台spa和一个前后台spa\(基于饿了么组件库\), 中间也会穿插教大家做几个常见的表单组件.

## 学习如何提问

在企业工作的时候, 很可能产生的问题大家都不会, 这时候就要知道如何在网上求助, 国内的sf是个回答前端问题速度最快质量最高的平台, 所以后期会教大家如何在sf上提问, 以及如何标准的描述问题, 让别人一下就看懂你的问题, 回答你.

### [提交issues](https://github.com/383514580/vue-book/blob/master/shi-yao-shi-vue.md)

### 



