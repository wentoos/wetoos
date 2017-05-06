 ##ES6

先要知道 ECMAScript就是JavaScript中的语法规范！ 它定义了很多重要的东西，包括：

* 语法 – 解析规则，关键字，语句，声明，操作等

* 类型 – 布尔型，数字，字符串，对象等

原型和继承

* 内置对象和函数的标准库 – JSON，数字（Math），数组方法，对象内省的方法等等。

- JavaScript由三部分组成：

  1. ECMAScript（核心）
  2. DOM（文档对象模型）
  3. BOM （浏览器对象模型）
  4. ECMAScript标准的版本分别是1、2、3、5、6、7。

 ## Es6新增了许多特性。
   
    
##1. Let + Const 块级作用域和常量
 *** 
 ###let
    let 有严格的作用域，并没有所谓的声明提升，严格遵守作用域规则，只会存在于{ }之中，但定义全局变量时，this指向window。
    
    ```js   
       console.log(a)//输出为is not defined
       let  a=5;  
    ```   
### const 只读变量   
    ```js
        const a=5;
        a=6;//用const 进行在赋值是错误的
    //但当a为对象是可以改变对象的属性    
        const a={
            name:'a'
        }
        a.name='b'  
    ```
***    
##2.解构

-  解构意思就是分解一个东西的结构,可以用一种类似数组的方式定义N个变量，可以将一个数组中的值按照规则赋值 。    
   
   1. 数组的解构赋值    
   ```js
   let [a,b, , ,c]=[1,2,3]     
   
   //数组进行匹配时，按照数组的下标进行匹配，空格会占位
   ``` 
   ***
   2. 对象的解构赋值    
   ```js
      let obj={bar:'bbb',foo:'aaa'}
      let {foo,bar,sdf}=obj;
      console.log(foo,bar,sdf);    
      //结果为aaa,bbb,undefined
    ```
    ***
    3. 同数组，按下标匹配   
    
```js
    const [a, b, c, d, e] = 'hello';
    console.log(a + b + f)//heundefined
```
***


##es6对象声明方法     
    - 当属性名与属性值相等时，可以只写一个。 对象里面有function时，声明方法也有所改变。   
```js
            let obj={
                 name,//注意和之前的不同
                 age,
                 say,
                 run(){
                   console.log('run')
                 }
            }
            console.log(obj);
        ```    
        ##es6箭头函数    
        -  箭头函数简化了函数的的定义方式，( ):代表参数  =>:代表返回值；  
        ```js
        //es5
        var a=function(){} 
        //es6
        let a=()=>return;    
        //有一个参数时可以省略，多个参数不可以省略
        //函数里面有多条语句时。
        //es5
        var b=function(num,num1){   
          num=num++;
          num1=num1++;
          return num+num1
        }
        //es6
        let b=(num,num1)=>{
          num=num++;
          num1=num1++;
          return num+num1
        }
        //返回一个对象时
        let c=(num,num1)=>({name:'aaa'})
        //将对象用()包起来，{}表示执行多条语句
```   

    -  箭头函数this指向   在箭头函数声明时对应的将this绑定在函数本身，无论是谁调用都不变    
   ##es6字符串模板

    ES6中允许使用反引号 `` 来创建字符串，字符串用`包起来，里面有变量用${}表示。
```js
        var name='jaya';
        var age='20';
        var str=`<p class='active'>姓名是 ${name} 年龄是 ${age}</p>`
```   
##Rest 剩余参数

- 不定参数是在函数中使用命名参数同时接收不定数量的未命名参数。类似之前js中学的arguments。
- 不定参数的格式是三个点号后跟代表所有不定参数的变量名。

```js

    function fun(a, ...rest) {
      console.log(a)
      console.log(rest)
    }
    fun(1);//a:1 rest:[]
    fun(1, 2, 3, 4); //a:1 rest[2,3,4]


    //利用这个属性可以将所有参数相加
    function add(...x){
        return x.reduce((m,n)=>m+n);
    }
    //传递任意个数的参数
    console.log(add(1,2,3));//输出：6
    console.log(add(1,2,3,4,5));//输出：15   
```
6.Spread 扩展操作符

demo1

```js
    var arr=[1,2,3];     
    var arr1=[...arr,4,5];
    console.log(arr1);//[1,2,3,4,5]
```


demo2

```js
let obj={a:{b:1}};
let {...x}=obj;
console.log(x);//a:{b:1} 
```

##Default 默认参数值
***
还有一种是参数里可以对象解构 

```js

    //传统的指定默认参数的方式
    //必须要传参数
    function sayHello1(name){
        var name=name||'dude';
        console.log('Hello '+name);
    }
    //运用ES6的默认参数
    //当没有传参时，就使用默认参数，传了参时，就用实际参数。
    function sayHello2(name='dude'){
        console.log(`Hello ${name}`);
    }
    sayHello1();//输出：Hello dude
    sayHello1('zf');//输出：Hello zf
    sayHello2();//输出：Hello dude
    sayHello2('zf');//输出：Hello zf
```
##es6Modules 模块
****

将不同功能的代码分别写在不同文件中，各模块只需导出公共接口部分，然后通过模块的导入的方式可以在其他地方使用。

```js

    //test.js中
    let name='yu'
    let obj={
      sex:'nan',
      age:'20'
    }
    export{name,obj}//命名导出
    export default obj;//默认导出，只允许有一项
    //index.js中
    import { name} from './test.js';
    console.log(name) //jaya
    import newobj from './test.js'
    console.log(newobj);//随意命名
    //as
    import { name as newname} from './test.js';
    console.log(newname)//jaya
    //而且使用了as后在index.js中就没有name了
```   
***
#es6   函数


###箭头函数   


()为参数一个的时候可以省略、多个不能省略用,隔开、没有的时候不能省略。
 =>为返回值，返回一个对象的时候用小括号包起来。
执行多条js语句用{}包起来,需要自己写返回值。
箭头函数指向的this在声明时就会绑定，以后所有的this都指向声明时的this。
```js
let a = () => 8;等于
function a() {
	  return 8;
	}
	
```js
	let a = (num,num1) => num*num1;
	console.log(a(5,8));
```


```js
let a = (num,num1) =>{
	num++;
	num1++;
	return num+num1;
}
console.log(a(5,8));
```
```js
let a = (num,num1) =>({name:'sayname'});
console.log(a)
```
```js
function foo(){
	console.log(this);
	setTimeout(() =>{
		console.log(this);
		console.log(this.id);
	},1000)
};
var id = 21;
foo.call({id:42},12);
```
