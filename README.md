<p align="center"><img width="140"src="https://raw.githubusercontent.com/SortableJS/Vue.Draggable/master/logo.svg?sanitize=true"></p>
<h1 align="center">Vue.Draggable</h1>

[![CircleCI](https://circleci.com/gh/SortableJS/Vue.Draggable.svg?style=shield)](https://circleci.com/gh/SortableJS/Vue.Draggable)
[![Coverage](https://codecov.io/gh/SortableJS/Vue.Draggable/branch/master/graph/badge.svg)](https://codecov.io/gh/SortableJS/Vue.Draggable)
[![codebeat badge](https://codebeat.co/badges/7a6c27c8-2d0b-47b9-af55-c2eea966e713)](https://codebeat.co/projects/github-com-sortablejs-vue-draggable-master)
[![GitHub open issues](https://img.shields.io/github/issues/SortableJS/Vue.Draggable.svg)](https://github.com/SortableJS/Vue.Draggable/issues?q=is%3Aopen+is%3Aissue)
[![npm download](https://img.shields.io/npm/dt/vuedraggable.svg)](https://www.npmjs.com/package/vuedraggable)
[![npm download per month](https://img.shields.io/npm/dm/vuedraggable.svg)](https://www.npmjs.com/package/vuedraggable)
[![npm version](https://img.shields.io/npm/v/vuedraggable.svg)](https://www.npmjs.com/package/vuedraggable)
[![MIT License](https://img.shields.io/github/license/SortableJS/Vue.Draggable.svg)](https://github.com/SortableJS/Vue.Draggable/blob/master/LICENSE)

> 文档来源于[官方文档](https://github.com/SortableJS/Vue.Draggable),  因为官网文档为英文文档, 看的吃力, 而且在网上也并未查询到相关中文文档，所以本人使用翻译工具与查阅相关资料进行逐行翻译, 如有不足请指正~
>
> 谨作学习使用。

Vue组件（Vue.js 2.0）或指令（Vue.js 1.0）允许拖放并与视图模型阵列同步。

基于并提供 [Sortable.js](https://github.com/RubaXa/Sortable) 的所有功能


## 适用于Vue 3
​	见  [vue.draggable.next](https://github.com/SortableJS/vue.draggable.next)

## 示例

![demo gif](https://raw.githubusercontent.com/SortableJS/Vue.Draggable/master/example.gif)

## 浏览Demo

https://sortablejs.github.io/Vue.Draggable/

https://david-desmaisons.github.io/draggable-example/

## 特点

* 完全支持 Sortable.js 的功能
    * 支持触摸设备
    * 支持拖动手柄和可选文本 [选择器???]
    * 智能自动滚动
    * 支持在不同列表之间拖放
    * 没有 JQuery 依赖关系
* 使HTML与视图模型列表保持同步 [ HTML结构与数据保持同步 ]
* 兼容 Vue.js 2.0 的 transition-group
* 支持撤销功能
* 当需要全面控制时, 报告任何变化的事件 [ 拖放从鼠标按下开始拖拽到鼠标松开拖动结束都有完整的事件监听,可以添加自己的处理 ]
* 重用现有的UI组件库,如:[vuetify](https://vuetifyjs.com), [element](http://element.eleme.io/), or [vue material](https://vuematerial.io) 等等, 使用 `tag` 或者 `componentData` 属性选项来使他们可以拖动

## 支持者

 <a href="https://flatlogic.com/admin-dashboards">
 <img style="margin-top: 10px;" src="https://flatlogic.com/assets/logo-b6ca6492a82bd9eddf58c40710235855b1c502097c23faae6306cd36973aaea8.svg">
 </a>

Admin Dashboard Templates made with Vue, React and Angular.


## 捐赠

觉得项目有用吗? 你可以请我:coffee: or a :beer:

[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=GYAEKQZJ4FQT2&currency_code=USD&source=url)


## 安装

### 使用 npm 或者 yarn

```bash
yarn add vuedraggable

npm i -S vuedraggable
```

**注意它是针对Vue 2.0的vuedraggable，而不是针对1.0版本的vue-draggable**

### 直链
```html

<script src="//cdnjs.cloudflare.com/ajax/libs/vue/2.5.2/vue.min.js"></script>
<!-- CDNJS :: Sortable (https://cdnjs.com/) -->
<script src="//cdn.jsdelivr.net/npm/sortablejs@1.8.4/Sortable.min.js"></script>
<!-- CDNJS :: Vue.Draggable (https://cdnjs.com/) -->
<script src="//cdnjs.cloudflare.com/ajax/libs/Vue.Draggable/2.20.0/vuedraggable.umd.min.js"></script>

```

[参照实例部分](https://github.com/SortableJS/Vue.Draggable/tree/master/example)

## 适用于 Vue.js 2.0

使用 draggable 组件: 

### 典型使用:
``` html
<draggable v-model="myArray" group="people" @start="drag=true" @end="drag=false">
   <div v-for="element in myArray" :key="element.id">{{element.name}}</div>
</draggable>
```
.vue 文件:
``` js
  import draggable from 'vuedraggable'
  ...
  export default {
        components: {
            draggable,
        },
  ...
```

### 使用 `transition-group`:

``` html
<draggable v-model="myArray">
    <transition-group>
        <div v-for="element in myArray" :key="element.id">
            {{element.name}}
        </div>
    </transition-group>
</draggable>
```

Draggable 组件应该直接包裹 draggable 元素, 或者包裹包含 draggable 元素的 `transition-group`


### 使用 footer slot:
``` html
<draggable v-model="myArray" draggable=".item">
    <div v-for="element in myArray" :key="element.id" class="item">
        {{element.name}}
    </div>
    <button slot="footer" @click="addPeople">Add</button>
</draggable>
```
### 使用 header slot:
``` html
<draggable v-model="myArray" draggable=".item">
    <div v-for="element in myArray" :key="element.id" class="item">
        {{element.name}}
    </div>
    <button slot="header" @click="addPeople">Add</button>
</draggable>
```

### 使用 Vuex:

```html
<draggable v-model='myList'>
```

```javascript
computed: {
    myList: {
        get() {
            return this.$store.state.myList
        },
        set(value) {
            this.$store.commit('updateList', value)
        }
    }
}
```


### 接收属性 Props
#### value
Type: `Array`<br>
Required: `false`<br>
Default: `null`

draggable component 的输入数组。通常与内部元素 v-for 指令引用的数组相同。<br>这是使用 Vue.draggable 的首选方式，因为它与 Vuex 兼容 。<br>它不应该直接使用， 但可以通过 `v-model` 指令使用：

```html
<draggable v-model="myArray">
```

#### list
Type: `Array`<br>
Required: `false`<br>
Default: `null`

Alternative to the `value` prop, list is an array to be synchronized with drag-and-drop.<br>

作为 `value` 属性的替代, list 是一个可以与拖放同步的数组

主要区别在于: `list` 属性是 draggable component 使用 splice 方法更新的，而 `value` 是不可变的。

**不用与 value prop 同时使用**

#### All sortable options(所有的 sortable 选项)

2.19版的新内容

从2.19版开始, Sortable 的选项可直接设置为 vue.draggable 的 属性

这意味着所有的  [sortable option](https://github.com/RubaXa/Sortable#options) 都是有效的 sortable props, 但是有明显的例外:所有以 "on" 开头的方法。因为 draggable component 通过事件暴露了相同的API

支持 kebab-case 属性: 例如 `ghost-class` 属性将会被转换名为 `ghostClass` 的 sortable option。

例如设置 handle,sortable 和 group的选项:

```HTML
<draggable
        v-model="list"
        handle=".handle"
        :group="{ name: 'people', pull: 'clone', put: false }"
        ghost-class="ghost"
        :sort="false"
        @change="log"
      >
      <!-- -->
</draggable>
```

#### tag
Type: `String`<br>
Default: `'div'`

draggable component 作为包含slot的外部元素创建的HTML节点类型<br>

也可以将Vue组件的name作为元素传递,在这种情况下, draggable的属性将被传递给创建组件<br>

如果你需要为创建的组件设置props或者event, 请参考 [componentData](#componentdata)

#### clone
Type: `Function`<br>
Required: `false`<br>
Default: `(original) => { return original;}`<br>

当 clone 选项为true时, 在源组件上调用函数来克隆元素。唯一的参数是要克隆的viewModel元素, 返回值是它的克隆版本。<br>

默认情况下, vue.draggable 复用了 viewModel元素(的数据), 所有如果你想要去克隆或者深度克隆它,你必须使用这个hook。

#### move
Type: `Function`<br>
Required: `false`<br>
Default: `null`<br>

If not null this function will be called in a similar way as [Sortable onMove callback](https://github.com/RubaXa/Sortable#move-event-object).

如果不为null的话, 那此函数的调用方式与  [Sortable onMove callback](https://github.com/RubaXa/Sortable#move-event-object) 类似。

返回false将取消拖动操作。

```javascript
function onMoveCallback(evt, originalEvent){
   ...
    // return false; — for cancel
}
```
evt 对象有三个与 [Sortable onMove event](https://github.com/RubaXa/Sortable#move-event-object) 相同的属性以及3个附加属性:

 - `draggedContext`:  与被拖动元素相关的上下文
   - `index`: 被拖动元素的索引
   - `element`: dragged element underlying view model element 被拖动元素的底层视图模型元素 [ 被拖动元素的数据 ]
   - `futureIndex`:  如果接受(鼠标)放下的操作, (则为)被拖动元素的潜在(未来)索引值
 - `relatedContext`: 与当前拖动操作相关的上下文
   - `index`: 目标元素的索引
   - `element`: 目标元素的视图模型元素 [ 目标元素的数据 ] 
   - `list`: 目标(所在的)列表
   - `component`: target VueComponent    [ Vue组件目标??? ]

HTML:
```HTML
<draggable :list="list" :move="checkMove">
```
javascript:
```javascript
checkMove: function(evt){
    return (evt.draggedContext.element.name!=='apple');
}
```
查看完整演示:  [Cancel.html](https://github.com/SortableJS/Vue.Draggable/blob/master/examples/Cancel.html), [cancel.js](https://github.com/SortableJS/Vue.Draggable/blob/master/examples/script/cancel.js)

#### componentData
Type: `Object`<br>
Required: `false`<br>
Default: `null`<br>

这个prop属性用来向被 [tag props](#tag) 所声明的子组件传递额外信息<br>
Value:

* `props`: 传递给子组件的 props 
* `attrs`: 传递给子组件的 attrs 
* `on`: 要在子组件中订阅的事件

Example(使用 [element UI library](http://element.eleme.io/#/en-US) ):

```HTML
<draggable tag="el-collapse" :list="list" :component-data="getComponentData()">
    <el-collapse-item v-for="e in list" :title="e.title" :name="e.name" :key="e.name">
        <div>{{e.description}}</div>
     </el-collapse-item>
</draggable>
```
```javascript
methods: {
    handleChange() {
      console.log('changed');
    },
    inputChanged(value) {
      this.activeNames = value;
    },
    getComponentData() {
      return {
        on: {
          change: this.handleChange,
          input: this.inputChanged
        },
        attrs:{
          wrap: true
        },
        props: {
          value: this.activeNames
        }
      };
    }
  }
```

### Events

* 支持 Sortable 事件: 

  `start`, `add`, `remove`, `update`, `end`, `choose`, `unchoose`, `sort`, `filter`, `clone`<br>
  
  由 Sortable.js 使用相同的参数触发 onStart, onAdd, onRemove, onUpdate, onEnd, onChoose, onUnchoose, onSort, onClone 时, 就会调用这些事件。

  [阅读此处以供参考](https://github.com/RubaXa/Sortable#event-object-demo)
  
  Note that SortableJS OnMove callback is mapped with the [move prop](https://github.com/SortableJS/Vue.Draggable/blob/master/README.md#move)
  
  注意： SortableJS 的 OnMove 回调是由 [move prop](#move) 映射的。

HTML:
```HTML
<draggable :list="list" @end="onEnd">
```

* change event

  `change` event is triggered when list prop is not null and the corresponding array is altered due to drag-and-drop operation.<br>
  
  当 list 属性不为 null 并且由于拖放操作而更改了对应的数组, 就会触发 `change` 事件。
  
  This event is called with one argument containing one of the following properties:
  
  可以使用包含以下属性之一的参数来调用事件： 
  
  - `added`:  包含添加到数组中的元素的信息
    - `newIndex`: 所添加的元素的索引
    - `element`: 增加的元素
  - `removed`:  包含从数组中移除的元素的信息
    - `oldIndex`: 移除前元素的索引
    - `element`: 移除的元素
  - `moved`:  包含在数组中移动的元素的信息
    - `newIndex`: 被移动元素的当前索引
    - `oldIndex`: 被移动元素的旧索引
    - `element`: 被移动的元素

### Slots

限制: header slot 和 footer slot 都不能与 transition-group 一起使用

#### Header
使用 `header` slot 来向 vuedraggable 组件内添加  none-draggable 元素

重要提示: 它应该与 draggable 选项一起使用来标记 draggable 元素

请注意: header slot 不论它在模板中什么位置, 它都会被加入到默认插槽之前。
Ex:

``` html
<draggable v-model="myArray" draggable=".item">
    <div v-for="element in myArray" :key="element.id" class="item">
        {{element.name}}
    </div>
    <button slot="header" @click="addPeople">Add</button>
</draggable>
```

#### Footer

使用 `footer` slot 来向vuedraggable 组件内添加 none-draggable 元素 

重要提示: 它应该和 draggable 选项一起使用来标记 draggable 元素
请注意: footer slot 不论它在模板中什么位置, 它都会被加入到默认插槽之后。
Ex:

``` html
<draggable v-model="myArray" draggable=".item">
    <div v-for="element in myArray" :key="element.id" class="item">
        {{element.name}}
    </div>
    <button slot="footer" @click="addPeople">Add</button>
</draggable>
```
 ### Gotchas

 - Vue.draggable children 应使用 v-for 指令来映射 list 或者 value 属性
   * 你可以使用 [header](https://github.com/SortableJS/Vue.Draggable#header) 或者 [footer](https://github.com/SortableJS/Vue.Draggable#footer) slot 来绕过这一限制
 - v-for中的子元素应该像Vue.js中的任何元素一样被标记. 特别需要注意的是要提供有意义的key值
    * 通常情况下提供数组索引值来作为 key 值是不通的, 因为key应该与 items content 相关联
    * cloned elements should provide updated keys, it is doable using the [clone props](#clone) for example
    * 克隆的元素应该提供更新后的key, 例如使用 [clone props](#clone) 是能做到的。


 ### Example 
  * [Clone](https://sortablejs.github.io/Vue.Draggable/#/custom-clone)
  * [Handle](https://sortablejs.github.io/Vue.Draggable/#/handle)
  * [Transition](https://sortablejs.github.io/Vue.Draggable/#/transition-example-2)
  * [Nested](https://sortablejs.github.io/Vue.Draggable/#/nested-example)
  * [Table](https://sortablejs.github.io/Vue.Draggable/#/table-example)

 ### Full demo example

[draggable-example](https://github.com/David-Desmaisons/draggable-example)

## For Vue.js 1.0

[See here](documentation/Vue.draggable.for.ReadME.md)

```
