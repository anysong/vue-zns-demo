# vue-zns-demo
老潇demo ing!

#### 一片html代码配合上json,再new出来vue实例
#### 更适合移动端项目
#### 不兼容低版本IE
#### 不依赖服务器环境

#### 指令:扩展html标签功能
    v-model 双向数据绑定
    v-for 循环 
        索引{{$index}} 
        key{{$key}} 
        (k,v) in json
    v-show
#### 事件
    v-on:click
    v-on:keydown
    v-on:mousedown
===========
    事件简写 @click
    事件对象 $event
    事件冒泡 ev.cancelBubble=true || @click.stop
    默认事件 ev.preventDefault() || @click.prevent
===========
    键盘事件 @keydown,@keyup
            回车  @keyup.13 || @keyup.enter
            上    @keyup.[键码] || @keyup.up
            下    @keyup.[键码] || @keyup.down
            左    @keyup.[键码] || @keyup.left
            右    @keyup.[键码] || @keyup.right
===========
    属性 v-bind:src=""
    简写 :src
    特殊class style
    class="" [] || {} || data内·书写
    style="" [] || {} || data内·书写  复合样式 驼峰命名法
============
    模板: 
        {{msg}}
        {{*msg}} 数据只绑定一次
        {{{msg}}} html转译输出
============
    过滤器:
        {{msg|filterA|filterB}} 
        {{'abc'|uppercase}} 转为大写
        {{'abc'|lowercase}} 转为大写
        {{'abc'|capitalize}} 首字母大写
        {{12|currency '¥'}} 钱符号
============
    交互:
        如果vue想做交互,需要引入 vue-resource     this.$http   
        vue2.0之后，就不再对vue-resource更新，而是推荐使用axios。基于 Promise 的 HTTP 请求客户端，可同时在浏览器和 Node.js 中使用。 
