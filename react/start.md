
## create-react-app 初始化项目：

react 使用babel 将jsx 转成正常的js 代码<br>
测试Babel转js
[babel]: https://babeljs.io

## jsx 识别表达式：

```
{'string'}  
{count}  
{getName()}  
{{color:'red'}}
```


## react 使用map 渲染列表

```
{list.map(item => <li key={item.id}> {item.name}</li>)}
```

## jsx 中实现条件渲染：

1. 使用逻辑与运算符  
2. 三元表达式
3. 复杂的条件渲染（使用函数return不同的情况）
```
// flag 为true 显示，false 不显示
{flag && <span>this is span</span>}
{flag ? <span>1</span> : <span>2</span>}
```
## react 基础事件绑定：

``` <button onClick={handleClick}> </button> ```
``` <button onClick={() => handleClick('name')}> </button> ```
``` <button onClick={() => handleClick('name', e)}> </button> ```

## 组件：

1.函数 首字母必须大写，内部存放了组件的逻辑和视图UI  

## useState基础使用：

useState 是一个React Hook 函数， 它允许我们向逐渐添加一个状态变量， 从而控制影响组件的渲染结果：（数据驱动试图） 
规则： 状态不可变， 只读的我们始终替换它而不是修改它：直接修不能触发试图刚更新； 对于对象的修改应该始终传给set 方法一个全新的对象来进行修改。  

update object 
``` 
setform({
    ...form,
    name: 'hohn'
}) 
```
## 组件的基础样式的控制方案：

行内：
```
 <div style={{ color: 'red'}}> </div>
```
```
const style = {
    color: 'red',
}

 <div style={style}> </div>
```
分离写法： 常用
``` 
<div className="foo"> </div>
 ```
## 当渲染的html结构比较复杂的时候我们可以使用（） 让结构变的更加清晰：

## lodash 给数据排序生成新的数据：

## classnames 优化类名控制
 
 为啥使用呢？ 字符串拼接比较容易出错， 而且不直观
 ```
 //before
 className={`nav-item ${type == itme.type && active}`}
 ```

 ```
//after
className={'nav-item', {active: type === item.type}}
 ```


 ## 受控表单绑定

 ``` 
 <input value = {value}
    onChange={(e) => setValue(e.target.value)}
  />
 ```

 ## react 中获取dom 不常用，我们都是数据驱动试图的

 在react组件中获取/操作dom， 需要使用useRef钩子函数，分为两步：

 //渲染完毕之后dom生成之后 才可用 一般在点击事件中使用。`console.log(inputRef.current)`
 ```
const inputRef = useRef(null);
<input type="text"  ref={inputRef}>
 ```

 ## uuid 可以使用 npm install uuid  时间格式处理我们可以使用 dayjs
 ## ingput 获取焦点 useRef 获取dom dom.current.forcus
 ## 组件通信
 通过props 传递参数：
 ```
 child:
 function(props) {
    props.name;
    props.age;
 }

 father:
 <div name = {test} 
    age = {18}
    isTrue={false}
    list={['vue','react']}
    abj={{name:'test'}}
    cd={()=>console.log(111)}
    child={<span> this is span</span>}
 > </div>
 ```
 
 props 是只读对象  
 子组件只能读取props中的数据，不能直接进行修改，父组件的数据只能由父组件修改。
 