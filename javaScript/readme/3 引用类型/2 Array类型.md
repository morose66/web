# Array类型
## 创建方式
```
var arr = new Array();
var arr = new Array(20);//创建了一个长度为20的数组
var arr = new Array('gww')//创建一个包含一项，即字符串为gww的数组
var arr = [1,2,3,4];
var arr = []//创建一个空数组
```
数组的length不是只读的，通过这个属性，可以从数组的末尾移除项或向数组添加两项
```
    let arr = [1,2,3];
    console.log("arr的长度为",arr.length);//3
    arr.length = 2;//2
    alert(arr[2]);
    arr[2] =4;
    console.log("arr长度为",arr.length)//3
    alert(arr[2]);
    //把一个值放在超出当前数组大小的位置上，数组会重新计算其长度。
    arr[99] = 99;
    alert(arr.length)//100
```
## 检测数组
Array.isArray(value);

## 转换方法
### toString()、tolocalString()、valueOf()
`toString（）和tolocalString（）都调用数组每一项的toString（）和tolocalString（）方法`
```
var colors = ['red','blue','green'];
console.log(colors.toString());//'red','blue','green'
console.log(colors);//['red','blue','green']
console.log(colors.valueOf());//返回数组本身['red','blue','green']
```
### join()方法
```
arr.join('||')
```
### 栈方法（后进先出）
push：可以接收任意数量的参数，把他们逐个添加到数组末尾，并返回修改后数组的长度。  
pop：从数组末尾移除最后一项，减少数组的length值，然后返回移除的项
### 队列方法（先进先出）
push: 
shift:移除数组中的第一个项并返回该项
unshift:在数组前端加任意项并返回数组长度

### 重排序方法
reverse()和sort()  
* reverse():反转数组项的顺序
* sort():可以接收一个比较参数
```
   //升序
   let sortFun = function(value1,value2){
    if(value1<value2){
        return -1
    }else if(value1>value2){
        return 1
    }else{
        return 0
    }
   }
```
```
//对于数值类型或者其valueOf()方法会返回数值类型的的对象类型，可以使用
function compare(val1,val2){
    return val2- val1
}
```

### 操作方法
* concat():没有传参数，复制数组。可以传一个或多个数组。如果传的不是数组，把该项添加到数组末尾。<font style="color:red">不改变原数组</font>
* slice():接收一个或两个参数，即要返回项的起始和结束位置<font style="color:red">不改变原数组</font>
* splice():
  * 删除：splice(0,2)//删除的第一项位置，删除项数
  * 插入：splice(2,0,'red','green')//起始位置 删除项数  插入项
  * 替换:splice(2,1,'red','green')//起始位置 删除位置 要插入的项

### 位置方法
* indexOf()//从头开始查找要查找的项在数组中的位置，在没找到的情况返回-1（查找严格相等 ===）//接收两个参数：要查找的项 查找起点位置的索引
* lastIndexOf()
```
   var nums = [1,1,2,3,1,88];
   console.log(nums.indexOf(1));//0
   console.log(nums.indexOf(1,1));//1
   console.log(nums.lastIndexOf(1));//4
   let o1 = {
       name:'gww'
   }
   let o2 = {
       name:'gww'
   }
   let os = [o1];
   console.log(os.indexOf(o2));//-1
   console.log(os.indexOf(o1));//0
   console.log(os.indexOf({
    name:'gww'
   }))//-1
```

### 迭代方法
每个方法都接收两个参数，要在每一项上运行的函数和运行该函数的作用域对象，影响this的值 可选
* every()//对数组的每一项运行给定函数，如果该函数对每一项都返回true，则返回true
* filter()//对数组中的每一项运行给定函数，返回该函数会返回true的项组成的数组
* forEach()//对数组中的每一项运行给定函数，没有返回值
* map()//对数组中的每一项运行给定函数，返回每次函数调用的结果组成的数组
* some()//对数组中的每一项运行给定函数，如果该函数对任一项返回true，则返回true

### 归并方法
* reduce()
* reduceRight()
```
   var v = [1,2,3,4,5];
   //函数参数 前一个值 当前值 项的索引 数组对象 这个函数返回的任何值都会作为第一个参数的索引自动传入下一项
   //第一次迭代发生在第二项上  
   var sum = v.reduce(function(pre,cur,index,arr){
    console.log(pre)
    console.log(cur);
    console.log(index)
    console.log(arr);
    return pre+cur
   })
   console.log(sum)//15
```