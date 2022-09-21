### 命名

#### 常用命名统一

 - 使用有意义的名词、简短、且具有可读性
 - 命名一般以一个或者两个单词组成，不得超过三个单词
 - 目录、函数方法、props使用小驼峰
 - 常量声明使用驼峰式或全大写声名，全大写多个单词时使用下划线隔开

```javascript

  // 变量声明
  let name;
  let orderName;

  // 常量声明
  const url;
  const URL;
  const baseUrl;
  const BASE_URL;

  // 方法声明
  current(){}
  defaultConfig(){}

```
 
 - CSS采用统一使用BEM进行命名
 - 导入及注册组件时，遵循 PascalCase(单词首字母大写命名) 约定
 - 在页面中使用组件需要前后闭合，并以短线分隔如 **<date-picker></date-picker>**

#### 常用单词约定

 - 出现以下命名，必须使用这些单词
 
```
  
   - 容器    container                       - 教室     classRoom
   - 内容    content                         - 课程     course
   - 菜单    menu                            - 班级     class
   - 搜索    search                          - 项       item
   - 图片    pic                             - 行       row 
   - 标志    logo                            - 列       col
   - 列表    list                            - 注册     register
   - 导航    nav                             - 报名     enroll
   - 选项    options                         - 报表     report
   - 提示    msg                             - 页面主体  main
   - 标签    tags                            - 显示     show
   - 确认    confirm                         - 隐藏     hide
   - 取消    cancel                          - 数据     data
   - 删除    del                             - 结果     res
   - 关键字  keyword(全小写，是一个单词)       - 异常     err
   
   状态
   - 禁用：disabled
   - 激活：active
   - 是否可见：visible （组件判断显示隐藏必须要使用visible，多个存在时在前面添加组件名称前缀）
   - 默认：default
   - 选中：checked

```


#### 目录、文件命名
 - 目录与和文件遵循命名统一规范
 - 目录文件夹命名统一以 页面名/index.js 
 - 目录结构遵循以下规则

```
page
└── setting                            setting页面
├── account
│      ├── components              account页面下的子组件文件夹
│      ├── mixins                  account页面下的混入文件夹
│      ├── index.scss              account页面的样式
│      └── index.vue               account页面的入口.vue 文件
│
├── components                     setting下的子组件文件夹
├── mixins                         setting下的混入文件夹
├── index.scss                     setting的样式
└── index.vue                      setting的入口文件

```

### 注释规范

- 为了便于维护，所有手写的文件，不包括 css,sass，统一需要在文件顶部添加以下注释模板，必须填入相关页面名称，复杂的页面要补充说明

```javascript
/****************************************************************************\

所属模块:优惠券模块—[XX子模块]
页面名称:XXX页
创建时间:
维护人: 
*┌────────────────────────────────────┐
    *│　此技术信息为本公司机密信息，未经本公司书面同意禁止向第三方披露．│
    *│　版权所有：×××××××有限公司　　　　　　　　　　　│
*└────────────────────────────────────┘
\***************************************************************************/
```
- 变量、常量、声明、引用的注释
```javascript

/**********
 *vue data的注释
 **********/
data:{
  // 上传的附件对象
  uploadList: {},
  // 部门数据列表
  departmentList: [],
  // 接收人集合
  receiverList: [],
  // 抄送人集合
  copyList: [],
  // 邮件标题
  title: ""
}

/**********
 *引用注释
 **********/
// 请求文件
import { request } from "../../tools/http.js";
// 加载动画组件
import smallLoading from "../components/smallLoading.vue";
// 查看视频组件
import videoPlay from "./videoPlay";
// 写邮件公用方法mixin
import mixin from "../mixin/writeCommon.js";
// 文件查看时判断类型的mixin
import fileView from "../mixin/fileView.js";
// 文件上传mixin
import fileUpload from "../mixin/fileUpload.js";
// 查看图片组件
import reviewImage from "../../../jerri-ui/src/components/imgViews";

/**********
 *变量注释
 **********/
// 邮件详情内容
let mailContents = "";

/**********
 *常量注释
 **********/
// 最大长度
const MAX_LEN = 10;

``` 

- 注释用语标明

```javascript

  @param {String} @name 校区名称    // 用于注释参数名称
  @return {String} 方法返回值    // 用于注释返回值内容
  @author ×××    // 开发者名字 建议中文
  @desc  实现xx功能   // 开发描述
  @date  2020年10月1日 00:00:00   // 开发时间节点
  @Todo 功能已经实现，不过性能可能仍需要优化  // 待办事项标记
  @Deprecated  不推荐这么写，由于时间问题，赶着上线；后面再改  // 代码如果临时没办法或赶时间这么写，记得标注，方便其他开发者维护
  @Mark  此方法/函数，预留实现XX功能，目前可能不需要，暂时先标记 // 事项标记

```

- 多重 if 判断语句必须添加注释


### VUE规范

#### 基础规范

- v-for 时需要有id时一定使用id定义 key 值
- 组件必须声明 name
- 通过 class 去改变元素样式，避免直接操作样式(除非需要动态计算属性)
- 禁止 v-if 和 v-for 嵌套使用
- 组件模板应该只包含简单的表达式,禁止出现复杂的表达式
- input 输入框必须添加 .trim 过滤前后空格

#### 基本结构（通过vscode代码块统一）
 
 ``` javascript
<!--
/*************************************************************************** 
所属模块: 模块—[子模块]
页面名称: XXX页
创建时间: 2020年10月08日 09:35:58
维护人: ××××
*┌────────────────────────────────────────────────────────────┐
*│  此技术信息为本公司机密信息，未经本公司书面同意禁止向第三方披露．
*│  版权所有：×××××××××有限公司                             
*└────────────────────────────────────────────────────────────┘
***************************************************************************/
-->

<template>
 <div></div>
</template>

<script>
export default {
 name:'name',
 components: {},
 mixins: [],
 data() {
    return {}
 },
 created() {},
 mounted() {},
 methods: {}
}
</script>
<!-- 声明语言，并且添加scoped -->
<style scoped lang='scss'>
</style>

 ```

#### 生命周期声明顺序

  ``` javascript
    - components
    - mixins
    - props
    - data
    - computed
    - filter
    - watch
    - created
    - mounted
    - activited
    - update
    - beforeRouteUpdate
    - metods
 ```

#### 标签属性排序

属性的排序必须按照以下顺序

 - 1). v-自定义指令
 - 2). 静态属性
 - 3). 动态属性
 - 4). 监听事件 


#### Mixin定义

- 抽取公用mixin时，私有属性使用 `MX_` 前缀。并附带一个命名空间

```javascript
/* 反例 */
let myGreatMixin = {
  data:{
    return {
      name:''      
    }
  },
  methods: {
    update: function() {
      // ...
    }
  }
}

/* 正例 */
let myGreatMixin = {
  data:{
    return {
      MX_myGreatMixin_name:''      
    }
  },
  methods: {
    MX_myGreatMixin_update: function() {
      // ...
    }
  }
}
```

- 在添加全局混入时，需要以 `__global__` 前缀为名称开头 

```js
//  注入全局混入
Vue.mixin({
 computed: {
   ...mapGetters({
     __global__schoolId: "schoolId",
   }),
 },
});

created() {
 this.__global__schoolId;
}
```

#### Props 规范

- 组件 props 原子化
- 使用 type 属性校验类型

```javascript

/* 反例 */
props: ['type']

/* 正例 */
props: {
  type: {
    type: String,
    required: true
  }
}

```

#### 路由配置

- 路由目录划分三个文件(文件夹)
```

    │— router                         vue-router vue路由的配置文件
    │    ├── currRoute                当前路由信息
    │    ├── index                    路由初始化
    │    └── routes                   路由配置信息(根据视图继续拆分路由)
    
```

- 路由配置默认导出页面所有路由 如果页面较多 可以继续拆分模块 routes 导入所有模块在导出

```javascript
import aRouters from "./a";
import bRouters from "./b";

// 路由配置规则
const routes = [
  {
    path: "/c",
    name: "c",
    component: () => import(`@views/c`),
  },
  ...aRouters,
  ...bRouters,
];

export default routes;
```

- 路由元信息配置

目前我们业务系统存在着三种特殊页面 分别通过路由元信息去控制处理

```javascript
meta: {
    // 是否需要开启全局白屏loading
    loading: false,
    // 是否需要获取外框token
    token: false,
    // 是否需要获取审批流token 获取审批流token的时候默认不获取外框token
    afToken: true,
}
```

- 全局路由守卫

用于控制白屏的 loading 是否需要开启,默认是开启,可以通过配置路由元信息设置不开启

```javascript
// 全局路由守卫
router.beforeEach(async ({ meta }, from, next) => {
  // 没有设置loading为false都需要开启白屏loading
  if (meta.loading !== false) {
    // 开启全局loading
    new Vue().$loading(true, true);
  }

  next();
});
```

- 入口文件

通过导入当前路由信息来判断是否需要获取外框 token 是否需要获取审批流 token 获取后才初始化页面

```javascript
// 判断当前页面是否需要token  是否需要获取审批流token
import { frameToken, afToken } from "./router/currRoute";

(async () => {
  const vm = new Vue({ router, render: (h) => h(App) });

  if (afToken) {
    // 获取审批流token
  }

  // 需要token的页面才获取
  frameToken && (await vm.$frame.getToken());

  vm.$mount("#app");
})();
```

#### API规范

组件内引入请求统一名称为api，需要引入公用接口的，则在接口层进行混入即可

```
/**
* 组件
*/ 

// 后台接口  
import * as api from "@api/standardDocument/permissions.js";

/**
* 接口层
*/ 

// 基础地址
import { API_URI } from "@api/BASE_URL";
// 请求
import { http } from "@utils/http";

// 导入公司接口
import { getCompany } from "@api/common";
// 导入分类接口
import { getCategory } from "@api/common";
// 导出公司接口
export const getCompanyList = getCompany;
// 导出分类接口
export const getCategoryList = getCategory;
```


### Javascript 规范

- 禁止使用 var，function，统一使用 ES6 语法

- 禁止使用保留字作为变量名或者函数名

- 代码禁止存在空的、无意义的代码块

- 禁止使用 == 与 != ， 必须使用完全等于 === 或 !== 

- 禁止直接使用 undefined 进行变量判断，使用 typeof 和字符串'undefined'对变量进行判断

```javascript
/* 反例 */
if (person === undefined) {
}

/* 正例 */
if (typeof person === 'undefined') {
}
```

- 在 if / else / for / do / while 语句中，即使只有一行，也不得省略块 {...}

```javascript
/* 反例 */
if (condition) callFunc()

/* 正例 */
if (condition) {
  callFunc()
}
```

- 静态字符串一律使用单引号或反引号，动态字符串使用反引号

```javascript
/* 反例 */
let a = 'foobar'
let b = 'foo' + a + 'bar'

/* 正例 */
let a = 'foobar'
let b = `foo${a}bar`
```

- 数组成员对变量赋值时，使用解构赋值

```javascript
let arr = [1, 2, 3, 4]
/* 反例 */
let first = arr[0]
let second = arr[1]

/* 正例 */
let [first, second] = arr
```

- 使用 parseInt 时，必须指定进制

```javascript
/* 反例 */
parseInt(str)

/* 正例 */
parseInt(str, 10)
```

- 滚动事件必须做节流;

- 有使用参数拼接的必须使用字符串模板;

- 短路运算右侧不能超过 1 个表达式;

- 使用addEventListener时，禁止使用匿名函数，使用时必须先移除，防止重复执行

 ~~~ javascript

    /* 反例 */
    window.addEventListener('message',()=>{
      /** something **/
    });

    /* 正例 */
    let func = ()=>{
      /** something **/
    }
    window.removeEventListener('message',func);
    window.addEventListener('message',func);

  ~~~
