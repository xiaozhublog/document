# 本项目Vue+element实现后台管理系统
本页实际为对于项目的准备，开发思路的整理。如有建议欢迎[issues](https://github.com/xiaozhublog/admin-element-template/issues)

# 一、各版本列表 
[^_^]: (插件名称-功能-选型原因)

> ["vue": "^2.6.11"](https://cn.vuejs.org/)
>> 功能：基础框架  
>> 优点：国人之作，上手快，博主暂时只会这个，O(∩_∩)O哈哈~。

> [@vue/cli 4.3.1](https://cli.vuejs.org/zh/)
>> 功能：官方脚手架  
>> 优点：Vue.js 开发的标准工具。

> ["element-ui": "^2.14.1"](https://element.eleme.cn/#/zh-CN)
>> 功能：UI框架  
>> 优点：有大厂背书，生态圈优异，社区活跃。

> ["vue-router": "^3.2.0"](https://router.vuejs.org/zh/)
>> 功能：官方路由  
>> 优点：infinity。

> ["vuex": "^3.4.0"](https://vuex.vuejs.org/zh/)
>> 功能：状态管理模式  
>> 优点：infinity。

> ["normalize.css": "^8.0.1"](https://github.com/necolas/normalize.css/)
>> 功能：重写CSS  
>> 优点：与许多CSS重置不同，保留有用的默认值。
        规范各种元素的样式。
        更正错误和常见的浏览器不一致问题。
        通过细微的修改来提高可用性。
        使用详细注释说明代码的作用。
# 二、目录结构
````JavaScript
├── public                     # 静态资源
│   │── favicon.ico            # favicon图标
│   └── index.html             # html模板
├── src                        # 源代码
│   ├── api                    # 所有请求
│   ├── assets                 # 主题 字体等静态资源
│   ├── components             # 全局公用组件
│   ├── directive              # 全局指令
│   ├── icons                  # 项目所有 svg icons
│   ├── layout                 # 全局 layout
│   ├── router                 # 路由
│   ├── store                  # 全局 store管理
│   ├── styles                 # 全局样式
│   ├── utils                  # 全局公用方法
│   ├── views                  # views 所有页面
│   ├── App.vue                # 入口页面
│   ├── main.js                # 入口文件 加载组件 初始化等
├── .eslintrc.js               # eslint 配置项
├── .gitignore                 # git 配置项
├── babel.config.js            # Babel 配置
├── jsconfig.json              # JavaScript服务提供的功能选项
├── package-lock.json          # 安装的各个npm package的具体来源和版本号
├── package.json               # package.json
├── README.md                  # 项目说明
└── vue.config.js              # vue-cli 配置
````
# 三、风格指南
本项目遵照[Vue官方风格指南](https://cn.vuejs.org/v2/style-guide/),[Code Guide by @AlloyTeam](http://alloyteam.github.io/CodeGuide/#project-naming)，[vue-element-admin](https://panjiachen.gitee.io/vue-element-admin-site/zh/guide/advanced/style-guide.html#风格指南)
## 命名规则
1. ### 目录
+ 文件夹全部以小写命名,有复数结构时，要采用复数命名法。（做到见名知意，英文差可以翻译，选取名词）  
2. ### 文件
    + ①、Component  
     所有的Component文件都是以大写开头 (PascalCase).但除了 index.vue(一般为入口文件)。例：
        * @components/Breadcrumb/index.vue
        * @components/charts/Line.vue 
        * @views/tables/normal/Table.vue
    + ②、JS 文件  
     所有的.js文件都遵循横线连接 (kebab-case)。例：
        * @/utils/open-window.js
    + ②、Views  
     在views文件下，代表路由的.vue文件都使用横线连接 (kebab-case)，代表路由的文件夹也是使用同样的规则。例：
        * @/views/svg-icons/index.vue
        * @/views/svg-icons/require-icons.js
1. ### 代码
    + ①、Class  
     类名使用小写字母，以中划线分隔。例：
     ```javascript
        .element-content {
                ...
        }  
     ```
     + ②、ID  
     id采用驼峰式命名。例：
     ```javascript
        #myDialog {
                ...
        } 
     ```
     + ③、变量、函数、混合、placeholder  
     scss中的变量、函数、混合、placeholder采用驼峰式命名。例：
     ```javascript
        /* 变量 */
        $colorBlack: #000;

        /* 函数 */
        @function pxToRem($px) {
                ...
        }

        /* 混合 */
        @mixin centerBlock {
        ...
        }

        /* placeholder */
        %myDialog {
        ...
        } 
     ```
## Vscode+Eslint+插件
1. 所有的配置文件都在 .eslintrc.js 中,本项目引用[vue-element-admin](https://panjiachen.gitee.io/vue-element-admin-site/zh/guide/advanced/eslint.html#配置项)。还有各种各样的配置信息，详情见 [ESLint](https://eslint.org/docs/rules/) 文档。 
首先安装 eslint 插件  
安装并配置完成 ESLint 后，我们继续回到 VSCode 进行扩展设置，依次点击 文件 > 首选项 > 设置 打开 VSCode 配置文件,添加如下配置  
````JavaScript
    {
        "files.autoSave": "off",
        "eslint.validate": [
        "javascript",
        "javascriptreact",
        "vue",
        ],
        "eslint.run": "onSave",
        "editor.codeActionsOnSave": {
                "source.fixAll.eslint": true
        },
        "workbench.iconTheme": "material-icon-theme"
    }
````
这样每次保存的时候就可以根据根目录下.eslintrc.js 你配置的 eslint 规则来检查和做一些简单的 fix。  
自动修复
````JavaScript
    npm run lint -- --fix
````
2. vscode插件  
> * Vetur----语法错误检查,语法高亮,代码自动补全
> * Eslint----能够检测代码语法问题，与格式问题，对项目代码风格统一至关重要
> * Auto Close Tag----	自动闭合HTML标签
> * Auto Rename Tag----修改HTML标签时，自动修改匹配的标签
> * Beautify css/sass/scss/less----css/sass/less格式化
> * Bracket Pair Colorizer----语法错误检查,语法高亮,代码自动补全
> * Material Icon Theme----文件与文件夹图标
> * Path Intellisense----路径完成提示
> * Vue 3 Snippets----Vue代码提示
## 四、书写规范
1. ### script结构
格式如下图，根据使用情况进行删减，顺序按照Vue生命周期顺序。
````JavaScript
<script>
export default {
  name: 'Home',
  components: {},
  data() {
    return {
      message: 'Xiaozhublog.com'
    }
  },
  beforeCreate: function() {
    console.group('beforeCreate 创建前状态===============》')
    // this.$el                         undefined
    // this.$data=>[object Object]      undefined
    // this.message=>Xiaozhublog.com    undefined
  },
  created: function() {
    console.group('created 创建完毕状态===============》')
    // this.$el                         undefined
    // this.$data=>[object Object]      已经被初始化
    // this.message=>Xiaozhublog.com    已经被初始化
  },
  beforeMount: function() {
    console.group('beforeMount 挂载前状态===============》')
    // this.$el                         已经被初始化
    // this.$data=>[object Object]      已经被初始化
    // this.message=>Xiaozhublog.com    已经被初始化
  },
  mounted: function() {
    console.group('mounted 挂载结束状态===============》')
    // this.$el                         已经被初始化
    // this.$data=>[object Object]      已经被初始化
    // this.message=>Xiaozhublog.com    已经被初始化
  },
  beforeUpdate: function() {
    console.group('beforeUpdate 更新前状态===============》')
    // 这里指的是页面渲染新数据之前(也就是页面上还没有看到文字或图片)
  },
  updated: function() {
    console.group('updated 更新完成状态===============》')
  },
  beforeDestroy: function() {
    console.group('beforeDestroy 销毁前状态===============》')
  },
  destroyed: function() {
    console.group('destroyed 销毁完成状态===============》')
  },
  methods: {
    // 方法
  }
}
</script>
```` 

2. ### Style结构
在样式开发过程中，有两个问题比较突出：
+ 全局污染 —— CSS 文件中的选择器是全局生效的，不同文件中的同名选择器，根据 build 后生成文件中的先后顺序，后面的样式会将前面的覆盖；  
+ 选择器复杂 —— 为了避免上面的问题，我们在编写样式的时候不得不小心翼翼，类名里会带上限制范围的标示，变得越来越长，多人开发时还很容易导致命名风格混乱，一个元素上使用的选择器个数也可能越来越多，最终导致难以维护。  
+ 每个单独文件都使用scoped，只要加上 scoped 这样 css 就只会作用在当前组件内了。使用 scoped 后，父组件的样式将不会渗透到子组件中。不过一个子组件的根节点会同时受其父组件的 scoped CSS 和子组件的 scoped CSS 的影响。这样设计是为了让父组件可以从布局的角度出发，调整其子组件根元素的样式。  
+ 相关的属性声明按右边的顺序做分组处理，组之间需要有一个空行。更多详情参看[CodeGuide--CSS-属性声明顺序](http://alloyteam.github.io/CodeGuide/#css-declaration-order)
+ 如下：
````JavaScript
<style lang="scss" scoped>
  .home{
    //   布局类型
    display: block;
    float: right;
    
    //   位置信息
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 100;

    //  盒模型
    border: 1px solid #e5e5e5;
    border-radius: 3px;
    width: 100px;
    height: 100px;

    //  字体颜色
    font: normal 13px "Helvetica Neue", sans-serif;
    line-height: 1.5;
    text-align: center;
    //   背景相关
    color: #333;
    background-color: #f5f5f5;
    //   其他
    opacity: 1;
  }
</style>
````
3. ### .vue结构
* 不同组件用div包裹。便于后期样式调试。增加适当注释。
4. ### router
* [路由懒加载](https://router.vuejs.org/zh/guide/advanced/lazy-loading.html)  
路由详情说明会在路由文件中，详细说明。
````JavaScript
//当打包构建应用时，JavaScript 包会变得非常大，影响页面加载。如果我们能把不同路由对应的组件分割成不同的代码块，然后当路由被访问的时候才加载对应组件，这样就更加高效了。
const Foo = () => import( /* webpackChunkName: "group-foo" */ './Foo.vue')
const Bar = () => import( /* webpackChunkName: "group-foo" */ './Bar.vue')
const Baz = () => import( /* webpackChunkName: "group-foo" */ './Baz.vue')
const routes = [{
    path: '/foo',
    component: Foo
  },
  {
    path: '/foo',
    component: Foo
  },
  {
    path: '/foo',
    component: Foo
  },
]

const router = new VueRouter({
  routes
})
````


    



































