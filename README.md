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
        {{msg}}                v-text="msg" 防止网速慢出现花括号
        {{*msg}} 数据只绑定一次
        {{{msg}}} html转译输出   v-html="msg" 防止网速慢出现花括号
============
    防止闪烁
        v-cloak   大段落
        v-text
        v-html
============
    过滤器:
        {{msg|filterA|filterB}} 
        {{'abc'|uppercase}} 转为大写
        {{'abc'|lowercase}} 转为大写
        {{'abc'|capitalize}} 首字母大写
        {{12|currency '¥'}} 钱符号
        {{{}|json}}  过滤json
============
    交互:
        如果vue想做交互,需要引入 vue-resource     this.$http   
        vue2.0之后，就不再对vue-resource更新，而是推荐使用axios。基于 Promise 的 HTTP 请求客户端，可同时在浏览器和 Node.js 中使用。 
==============
    生命周期:
        钩子函数:
            created -> 实例已经创建
==============
    计算属性:
        computed里面可以防止一些业务代码,一定要return
        computed: {
            b: {
                get: function(){
                    return 1;
                },
                set: funcion(val){

                }
            }
        }
        //简写
        computed: {
            b: function(){
                return 1;
            }
        }
        值为函数返回值
=============
    实例
    vm.$el       元素 el
    vm.$data     数据 data
    vm.$mount()  手动挂载
    vm.$options  获取自定义属性
    vm.$destroy  销毁对象
    vm.$log      查看现在的数据状态
    vm.$watch
==============
    循环
     v-for 处理重复数据 加上索引 track-by="$index"  提高性能
==============
    过滤器
        uppercase
        capitalize
        currency
        debounce 配合事件,延迟执行
    数据配合使用过滤器
        limitBy 参数(取几个,从哪开始)
        filterBy 过滤数据  参数(值)
        orderBy 排序 1:正序 -1:倒序
    自定义过滤器
        //model -> view
        Vue.filter(name, function(input, arg1, arg2 ...){
            return input + 1;
        })
    双向过滤器
        //model -> view -> model
        //处理v-model
        Vue.filter(name, {
            read: function(input){
                //model -> view
                return input+1
            },
            write: function(val){
                //view -> model
            }
        })
=============
    自定义属性指令
        扩展了html语法
        //调用时必须v-开头
        Vue.directive('指令名称',function(val){
            //val 为 v-color="val";传入
            this.el => dom
        })
    自定义元素指令(用处不大)
        <v-drag>22</v-drag>
==============
    自定义键盘信息 
        //自定义‘ctrl’
        Vue.directive('on').keyCodes.ctrl=17; 
==============
    监听数据变化
        vm.$watch("数据名字", cb) //浅度
        vm.$watch("数据名字", cb, {deep: true}) //深度
===============
    动画
    vue-> 过度(动画)
    transiton="fade"; 规定名称

    install animate
===============
    vue组件
    定义一个组件法1:
    (全局组件)
        var Aaa = Vue.extend({
            template: '<h3>333</h3>'
        })
        Vue.component('aaa',Aaa); 
        *** 组件内放数据, data必须是函数的形式,函数必须返回一个对象(json); ***
        var Aaa = Vue.extend({
            data(){
                return {
                    msg: 'tt'
                };
            },
            template: '<h3>{{msg}}</h3>'
        })
    (局部组件)
         var Aaa = Vue.extend({
            template: '<h3>{{msg}}</h3>'
        })
        new Vue({
            data: {
                a: 12
            },
            components: {
                aaa: Aaa //局部组件
            }
        }).$mount('#box')

    定义一个组件法2:
    (全局)
        Vue.component('aaa', {
            data(){
                return {
                    msg: 'uuu8'
                }
            },
            template: '<h3>{{msg}}</h3>'
        }); //全局
        new Vue({
            data: {
                a: 12
            }
        }).$mount('#box')
    (局部)
        new Vue({
            data: {
                a: 12
            },
            components: {
                aaa: {
                    data(){
                        return {
                            msg: 'uuu9'
                        }
                    },
                    template: '<h3>{{msg}}</h3>'
                }
            }
        }).$mount('#box')
=================
    template
    法1:
        <script type="x-template" id="tmp">
            <h3>{{msg}}</h3>
        </script>
        new Vue({
            components: {
                aaa: {
                    data(){
                        return {
                            msg: 'llllll'
                        }
                    },
                    template: '#tmp'
                }
            }
        }).$mount('#box')
    法2:
        <template id="tmp2">
            <h3>{{msg}}</h3>
        </template>
===================
    动态组件
    <component :is="a"></component>
===================
vue-devtools 调试工具








