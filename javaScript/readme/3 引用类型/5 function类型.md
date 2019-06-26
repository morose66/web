# Function类型
### 没有重载
### 函数声明与函数表达式
   解析器会率先读取函数声明，并使其在执行任何代码前可用。函数表达式，必须等到解析器执行到它所在的代码行，才会真正的被解析执行
### 作为值的函数
### 函数内部属性
 在函数的内部，有两个特殊对象，arguments和this；  
 arguments是一个类数组对象，主要用途是保存函数参数，该对象有一个属性callee，该属性是一个指针，指向拥有这个arguments对象的函数。  
 this:this引用的是函数执行的环境对象--也可以说是this值在全局作用域中调用函数时，this对象引用的就是window  
 caller:这个属性保存着调用当前函数的函数的引用，如果在全局作用域中调用当前函数，它的值为null  

 ### 函数的属性和方法
 每个函数包含两个属性：length和prototype
* length：表示函数希望接收的命名参数的个数
```
    function sayName(name){
        alert(name);
    }
    function sum(num1,num2){
        return num1+num2;
    }
    console.log('sayName(name)',sayName.length);//1
    console.log('sum(num1,num2)',sum.length);//2
```
* prototype:prototype是保存所有实例方法的真正所在。
每个函数都包含两个非继承而来的方法 apply()和call(),用途：在特定的作用域中调用函数，实际等于设置函数体内this对象的值。  
apply()接收两个参数，一个是在其中运行函数的作用域，另一个是参数数组（可以是Array的实例，也可以是arguments对象）
call()接收两个参数，第一个this，其余参数直接传递给函数call(this,num1,num2)  
传递参数并非call()和apply()真正的用武之地，真正强大的地方是能够扩充函数赖以运行的作用域。--好处：对象不需要与方法有任何耦合关系  
bind():这个方法会创建一个函数的实例，其this值会被绑定到传给bind()函数的值  



