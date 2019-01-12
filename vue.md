# 基于VUE脚手架开发的部分规范
## 一、通用规范
### 1.禁止使用汉语拼音
##### 反例
```javascript
    let bianliang = 1;
```
##### 正例
```javascript
    let good = 1;
```
### 2.使用驼峰式命名
##### 反例
```javascript
    let formitem = 1;
```
##### 正例
```javascript
    let formItem = 1;
```
### 3.首字母小写
##### 反例
```javascript
    let Good = 10;
```
##### 正例
```javascript
    let good =10;
```
### 4.代码格式化
##### 反例
```javascript
{let name =1;
    let fn = function(){}}
```
##### 正例
```javascript
    let fn = function(){
        alert('代码格式化')
    }

    fn();
```
## 二、data规范
### 1.变量声明添加注释
##### 反例
```javascript
export default {
    data() {
        return {
            name:'zhangsan'
        }
    }
}
```
##### 正例
```javascript
export default {
    data() {
        return {
            name:'zhangsan'//昵称
        }
    }
}
```
### 2.布尔类型变量使用is或has开头
##### 反例
```javascript
export default {
    data() {
        return {
            show:true//是否显示
        }
    }
}
```
##### 正例
```javascript
export default {
    data() {
        return {
            isShow:true//是否显示
        }
    }
}
```
## 三、prop规范
### 1.属性定义需要规定type类型
##### 反例
```javascript
export default {
    props: ['status']
}
```
##### 正例
```javascript
export default {
    props: {
        name:String//昵称
    }
}
```
```javascript
export default {
    props: {
        name:{//昵称
            type:String,
            default:'name'
        }
    }
}
```
### 2.父组件传值给子组件时如果是多单词变量，以烤串格式传递参数，子组件以驼峰式命名定义变量
##### 例
```HTML
//父组件
<template>
    <div>
        <child-item :child-data="testData"></child-item>
    </div>
</template>
<script>
import ChildItem from './ChildItem'
export default {
    data(){
        return {
            testData:''//传递给子组件的数据
        }
    }
}
</script>
```
```HTML
//子组件
<template>
    <div>
    </div>
</template>
<script>
export default {
    props: {
        childData:{//子组件data
            type:String,
            default:'name'
        }
    }
}
</script>
```

## 三、methods的规范
### 1.子组件自定义暴露给父组件事件以on开头
##### 例
```html
<!--子组件 -->
<template>
    <div @click="handleClickTest">
    </div>
</template>
<script>
export default {
    methods:{
        handleClickTest(){
            this.$emit('on-test')//自定义暴露方法以on-开头，后面接方法描述
        }
    }
}
</script>
<!--父组件 -->
<template>
    <div>
        <child-item @on-test="onTest"></child-item>
    </div>
</template>
<script>
export default {
    methods:{
        onTest(){
            
        }
    }
}
</script>
```
### 2.默认事件命名以handle+事件类型+描述
##### 例
```HTML

    <div id="app">
        <button @click="handleClickTest">按钮</button>
        <select @change="handleChangeTest">
            <option>1</option>
        </select>
    </div>

```
### 3.初始化调用接口渲染的事件默认定义getInit()（或根据实际情况定义）
##### 例
```html
<template>
    <div>
        
    </div>
</template>
<script>
export default {
    methods:{
        //初始化方法
       async getInit(){
           let res = await get();//get()为用户封装好的接口方法
       }
    },
    created(){
        this.getInit()
    }
}
</script>
```

## 四、组件规范
### 1.组件头需有注释声明，声明组件描述
##### 例
```html
<!--
 * @Description: 组件描述
 * @Author: you name
 * @Date: 2019-01-08 20:49:08
 * @LastEditors:  you name
 * @LastEditTime: 2019-01-12 12:23:53
 -->
<template>
    <div>

    </div>
</template>
<script>
export default {
    data () {
        return {
            
        }
    }
}
</script>
<style lang="less" scoped>

</style>
```
### 2.组件命名使用驼峰式(首字母大写，除根组件APP外)，如单词过长可使用简写
##### 例
```
<template>
    <div>
        <child-item></child-item>
    </div>
</template>
<script>
import ChildItem from './components/ChildItem.vue'//文件夹为小写，组件名为驼峰式，首字母也大写
export default {
    data () {
        return {
            
        }
    },
     components: {
        ChildItem
    }
}
</script>
<style lang="less" scoped>

</style>
```
### 3.引用组件时 再html中 不能使用驼峰式，需要使用全小写烤串式 不得出现大写字母。
##### 例
```
<template>
    <div>
        <child-item></child-item><!-- 全小写，烤串格式 -->
    </div>
</template>
<script>
import ChildItem from './components/ChildItem.vue'
export default {
    data () {
        return {
            
        }
    },
     components: {
        ChildItem
    }
}
</script>
<style lang="less" scoped>

</style>
```