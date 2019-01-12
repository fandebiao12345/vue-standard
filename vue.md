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
```
