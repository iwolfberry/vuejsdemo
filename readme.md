vue教程：https://cn.vuejs.org/v2/guide/installation.htm

imooc vue2.5:https://www.imooc.com/learn/980

二、vue.js第二天整理：

1、组件template:
    //全局组件

    /**
     *Prop 是你可以在组件上注册的一些自定义特性。当一个值传递给一个 prop 特性的时候，它就变成了那个组件实例的一个属性。
    一个组件默认可以拥有任意数量的 prop，任何值都可以传递给任何 prop。
     */
    Vue.component('todo-item', {
        data: function () { //data 必须是一个函数,因此每个实例可以维护一份被返回对象的独立的拷贝
            return {
                count: 0
            }
        },
        props: ['post'], //组件传值
        template: '<div><button v-on:click="$emit(\'enlarge-text\', 0.1)">放大字体</button>' +
            '<p>{{post.title}}</p><div v-html="post.content" ></div></div>'
    })

    new Vue({
            el: '#root',
            data: {
                postFontSize: 1,
                posts: [ //数据列表
                    {
                        id: 1,
                        title: 'todo first',
                        content: '111'
                    },
                    {
                        id: 2,
                        title: 'todo second',
                        content: '222'
                    },
                    {
                        id: 3,
                        title: 'todo third',
                        content: '333'
                    }
                ]
            },
            methods: {
                onEnlargeText: function (enlargeAmount) {
                    this.postFontSize += enlargeAmount
                }
            
            }
        });

    //使用：
     <div :style="{ fontSize: postFontSize + 'em' }">
            <todo-item v-on:enlarge-text="postFontSize += $event" v-for="post in posts" v-bind:key="post.id"
                v-bind:post="post"></todo-item>
        </div>

一、vue.js第一天整理：

1、数据绑定：{{data}}，写在data{}里

2、事件绑定：v-bind:click   /     @click

3、属性绑定：v-bind:title   /     :title

4、双向绑定：v-model

5、数据计算：computed{}

7、数据监听：watch{}

8、方法区域：methods{}

