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
