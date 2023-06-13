# vue

```
vue：一个构建用户界面的渐进式框架
渐进式(主张更少)

vue擅长开发单页应用
 单页: 只有一个完整的html页面, 其余页面都是div片段

只要修改data数据, vue会响应式将数据同步到视图(页面)

插值
<h1>{{变量}}</h1>

属性绑定
 v-bind:属性名="vue的data数据"
 v-bind:属性名 可以简写为 :属性名

 条件渲染
  v-if: true ==> 添加节点, false ==> 移除节点
  v-show: true ==> 显示节点, false ==> 隐藏节点

  v-show: 不管true或者false, 页面始终要渲染节点, 具有更高的初始化渲染
  v-if: 如果初始化为false, 则不会渲染节点, 具有更高的切换渲染

  如果用户频繁切换一个节点的显示或者隐藏, 建议使用v-show

  事件绑定
  v-on:事件类型="方法"
  v-on:事件类型 可简写为 @事件类型

  v-for: 列表渲染
    v-for="自定义变量名 in data的数据"
      比如：v-for="item in xxx"
      
    v-for="(自定义变量名, 自定义下标名) in data的数据"
      比如：v-for="(item, index) in xxx"

  v-model: 双向数据绑定

v-text
v-once
v-html
v-cloak
v-pre

计算属性(非常重要): 监听data数据变化(过滤data数据)

  强制更新: this.$forceUpdate();

侦听器
  data: {
    a: 'a',
    userInfo: {
      username: ''
    }
  }

  watch: {
    a(a, b) {},
    userInfo(a, b) {

    },
    ['userInfo.username'](a, b) {

    }

  }

class与style
  :class="'a'"
  :class="{active: true}"
  :class="['a', true ? 'b' : 'c', {active: true}]"

  :style="{width: '100px', height: '200px'}"
  :style="[{width: '100px', height: '100px'}, {backgroundColor: '#ddd'}]"


事件处理
  修饰符
  .stop ==> 阻止事件冒泡
  .prevent ==> 阻止浏览器默认行为
  .capture ==> 捕获阶段触发事件
  .self ==> 触发自身事件
  .once ==> 一次性事件(事件只会触发一次)
  .passive ==> 不会等待onscroll停下再触发, 提高移动端的onscroll的流畅度

  键盘事件
   .enter
   .space
   .y
   .f1
  组合键事件
   .ctrl.y
   .shift.y
   .alt.y
   .ctrl.shift.y
   .ctrl.alt.y
   .ctrl.shift.alt.y


  作业：进度条
    移动端事件
      touchstart
      touchmove
      touchend
      touchcancel


  生命周期：vue在不同阶段会执行不同的函数

    1、beforeCreate: 在实例的data数据生成之前执行, 此时还没有获取vue编译范围的元素, 只在初始化执行一次

    2、created: 在实例的data数据生成之后执行, 此时还没有获取vue编译范围的元素, 只在初始化执行一次, 可在这个钩子发起ajax请求

    3、beforeMount: 在实例的data数据生成之后, 此时获取vue编译范围的元素, 但是视图没有绑定vue的data的数据, 只在初始化执行一次

    4、mounted: 在实例的data数据生成之后, 此时获取vue编译范围的元素, 视图已经绑定vue的data的数据, 只在初始化执行一次

    5、beforeUpdate: data的数据同步到视图之前执行

    6、updated: data的数据同步到视图之后执行

    7、beforeDestroy销毁之前, 侦听器, 事件监听都销毁了

    8、destroyed, 销毁之后


  v-model

  vue的设计模式
    MVVM
      M: Model(模型) ==> 定义数据,
      V: View(视图) ==> 页面 ==> 显示数据
      VM: View Model(视图模型) ==> 将Model同步到View, 将View的输入数据同步到Model


    课后了解：MVC设计模式

  过滤器: 用于格式化数据
    全局定义过滤器
      Vue.filter('过滤器名称', () => {})

    局部定义过滤器
      filters: {
        过滤器名称() {}
      }

  
  作业
    1、定义一个处理千分位的全局过滤器
    2、星级评分, 参考链接https://vant-contrib.gitee.io/vant/v2/#/zh-CN/rate

    (1)点击星星评分

    (2)假设总分为10分, 每一颗星为2分, 当前电影总评分为9.6

  周三: 组件(极其重要)


var a = 145421.124;
a.toLocaleString();
在微信小程序中, 苹果手机支持toLocaleString(), 安卓不支持toLocaleString()

  组件: html, css, js集合体
    可反复使用, 复用

  父子组件通讯
    data数据只能从父组件流向子组件
    子组件触发自定义事件通知父组件更改数据


    组件的props的对象写法
    props: ['属性1', '属性2']
    props: {
      属性1: {
        //String, Number, Boolean, Array, Object
        //type: String
        type: 属性的类型,
        default: 默认值
      },

      属性2: {
        type: Object,
        default() {
          return {};
        }
      }
    }

    组件插槽: 可在组件内部分发内容
    <my-box>
      <div></div>
    <my-box>

    v-slot: 可简写为 #
    <div v-slot:a></div>
    <div #a></div>

    无名插槽
    <slot></slot>

    具名插槽
    <slot name="插槽名称"></slot>


    插槽作用域: 组件可以利用<slot></slot>将组件内部的data数据往外暴露
    

    通过<script src="vue.js"></script>
    自定义事件不能写驼峰式: this.$emit('updateTime')

  vue脚手架 + vue-router

  搭建vue脚手架环境
    1、安装Node.js
    2、全局安装vue脚手架
    npm i -g @vue/cli
    或者
    cnpm i -g @vue/cli

    安装cnpm
    npm i -g cnpm

  查看vue脚手架的版本
  vue -V
  或者
  vue --version

  创建vue项目
  vue create 项目名称

  分析vue脚手架创建的项目
  vr
  |- node_modules 保存第三方依赖包目录
  |- public 公共文件目录
    |- favicon.ico 浏览器的标签显示的图标
    |- index.html vue项目根页面(宿主页面)
  |- src 开发目录
    |- assets 静态文件目录(存在图片、视频、音频....)
    |- components 公共组件目录
    |- router 路由配置目录
    |- views 视图目录(配置路由的组件)
    |- App.vue 根组件
    |- main.js vue项目的入口文件
  |- .browserslistrc 浏览器配置
  |- .gitigonre git仓库的忽略文件配置
  |- babel.config.js 将es6转es5
  |- jsconfig.json vue配置, src路径的别名@, 输出目标js为es5...
  |- package.json 项目描述文件
  |- README.md 项目说明
  |- vue.config.js vue打包配置
  
  

注意文件追踪

运行项目
  npm run serve

打包项目
  npm run build

跳转路由
  1、声明式导航
  <router-link to="路由路径"></router-link>

  2、编程式导航(建议使用)
  组件实例.$router.push('路由路径')
  组件实例.$router.push({path: '路由路径'})

  //推荐此种写法
  组件实例.$router.push({name: '路由名称'})

返回上一级
this.$router.go(-1);

嵌套路由
  二级路由
  三级路由

vue页面参数：一般用于向服务器请求数据的参数
  路由参数: 需要在路由配置的路由路径定义参数 比如 path: /detail/:参数1/:参数2..., 在跳转路由时, 需要添加params字段, this.$router.push({name: '', params: {参数名1: 值, 参数名2: 值}})
  查询查询参数: 无需要在路由配置的路由路径定义参数, 在跳转路由时, 需要添加query字段, this.$router.push({name: '', query: {参数名1: 值, 参数名2: 值}})
  

vue的ajax解决方案
  axios: 基于promise封装的ajax

  在vue中, 使用vue-axios

  安装axios
  npm i axios --save

  安装vue-axios
  npm i vue-axios --save

  路由守卫
    两个全局守卫
      全局前置守卫 beforeEach
      全局后置守卫 afterEach

    路由独享守卫
      进入路由之前：beforeEnter

    组件内守卫
      进入组件之前: beforeRouteEnter
      组件离开之前: beforeRouteLeave
      组件路由参数发生改变之前: beforeRouteUpdate

  keep-alive 

  

```



# vue-project

```
vue项目

  vant: 基于vue的移动端框架
  elementUI: 基于vue的PC端框架

  vue + vue-router + vant

  安装vant2.x
  npm i vant@latest-v2 -S

  安装babel-plugin-import插件
  babel-plugin-import 是一款 babel 插件，它会在编译过程中将 import 的写法自动转换为按需引入的方式
  npm i babel-plugin-import --save-dev

  在项目根目录的babel.config.js文件写入以下代码
    module.exports = {
      presets: [
        '@vue/cli-plugin-babel/preset'
      ],
      plugins: [
        ['import', {
          libraryName: 'vant',
          libraryDirectory: 'es',
          style: true
        }, 'vant']
      ]
    }
  
  移动端适配
    rem: 相对于html元素的字体大小

  postcss-pxtorem 是一款 PostCSS 插件，用于将 px 单位转化为 rem 单位
  安装postcss-pxtorem
  npm i postcss-pxtorem --save-dev

  //如果运行项目时出现错误, 降级安装
  npm i postcss-pxtorem@5.1.1 --save-dev

  lib-flexible 用于设置 rem 基准值
  安装lib-flexible
  npm i lib-flexible --save-dev

  在项目根目创建postcss.config.js, 并写入以下代码
  以iphone6屏幕作为标准设计稿
    module.exports = {
      plugins: {
        'postcss-pxtorem': {
          rootValue: 37.5,
          propList: ['*'],
        },
      },
    };

在main.js导入flexible.js
import 'lib-flexible/flexible'



axios的拦截器

  请求之前拦截器
  
  响应之前拦截器


我的服务器接收POST请求参数


  //本服务器不接受post请求的对象传参
  this.axios({
    method: 'post',
    //参数
    data: {
      id: 'a001',
      age: 20
    }
  })


  //本服务器可接受post请求的对象序列化传参
  this.axios({
    method: 'post',
    data: 'id=a001&age=20'
  })

```



# vuex



```

vuex: 状态管理(组件data数据的管理)
  什么场景下使用vuex
    当组件之间传值比较复杂时, 可以使用vuex来解决

vuex五大核心概念
  state: 类似组件的data

  mutations: 用于修改state, 类似组件的方法methods, 没有异步操作

  actions: 用于提交mutations, 类似组件的方法methods, 具有异步操作

  getters: 过滤state数据, 类似组件的computed
  
  modules


  引用state需要写在组件的计算属性中
  引用getters需要写在组件的计算属性中
  引用mutations需要写在组件的方法中
  引用actions需要写在组件的方法中


  actions内部可以调用actions

  辅助函数, 简化引用vuex的state、mutations、actions、getters的写法, 可用可不用
    mapState()
    mapMutations()
    mapActions()
    mapGtters()
    

写法一：testAction(){
	this.$store.dispatch('testAction');
	// 调用testAction
}
写法二：..mapActions(['testAction','changeTitle'])
	//调用changeTitle
写法三：..mapActions({
	changeT:'changeTitle',
	changeTi(dispatch,payload) {
		//dispatch: 提交actions的方法
		//payload: 参数
		dispatch('changeTitle',payload)
	}
})

```

# 事件的监听和取消

```
例如：
mounted(){
    // 开始滑动监听
    window.addEventListener("scroll", this.scroll, true);
},
destroyed() {
    // 关闭监听
    window.removeEventListener("scroll",this.scroll,true);
},
methods:{
	scroll(){
            if (document.documentElement.scrollTop > 184) {
              this.$refs.fix.style.position = "fixed";
              this.$refs.fix.style.top = "0px";
              this.$refs.fix.style.left = "0px";
              this.$refs.fix.style.zIndex = "9";
            } else if(document.documentElement.scrollTop < 184){
              this.$refs.fix.style.position = "relative";
              this.$refs.fix.style.zIndex = "0";
            }
	},
}
```







