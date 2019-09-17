# 正则表达式
## 正则表达式的作用

1. 给定的字符串是否符合正则表达式的过滤逻辑(匹配)
2. 可以通过正则表达式，从字符串中获取我们想要的特定部分(提取)
3. 强大的字符串替换能力(替换)

```
var exp = /pattern/flags  
var exp1 = new RegExp("[bc]at",'i')
//pattern正则表达式
//flags 标志
```
* flags:
  * g 表示全局模式--应该于所有字符串，而非发现第一个匹配项时立即停止
  * i 表示不区分大小写模式
  * m 表示多行模式--到达一行文本末尾时还会继续查找下一行

* 正则表达式中遇到的   `元字符`都必须转义  
\( { \ ^ $ | ? * + . ] } )

* 注意：传给RegExp构造函数的两个参数都是字符串，所以在某些情况下要进行双重转义 即\\\
```
    var re3 =  /cat/g;
    let boo3 =  re3.test("cat11111ctui");
    console.log(boo3);//true
    let boo4 =  re3.test("cat11111ctui");
    console.log(boo4);//false
    原因：只为cat创建了一个RegExp实例，由于实例属性不会重置，所以再次调用test方法是从索引为3的字符开始
```
* 实例属性
  * global：布尔值，是否设了g标志
  * ignoreCase：布尔值 是否设置了i标志
  * lastIndex：整数 表示开始搜索下一个匹配项的字符位置
  * multiline：布尔值，表示是否设置了m标志
  * source：正则表达式的字符串表示
  ```
    let par = /\[bc\]at/i;
    console.log(par.global);//false
    console.log(par.ignoreCase);//true
    console.log(par.multiline);//false
    console.log(par.lastIndex);//0
    console.log(par.source);//\[bc\]at
    par.test("[bc]atuionno")
    console.log(par.lastIndex)//0???????????
  ```
* 实例方法
 * exec()专门为捕获组设计。接收应用模式的字符串，返回第一个包含匹配项信息的数组（包含两个额外属性：index和input），index表示匹配项在字符串中的位置，而input表示应用正则表达式的字符串。在数组中，第一项时与整个模式匹配的字符串，其他项则是与模式中的捕获组匹配的字符串
 ```
  var text = "mom and dad and baby111";
  var pattern = /mom and dad and baby/gi;
  var matches = pattern.exec(text)
  console.log(matches);
//["mom and dad and baby", index: 0, input: "mom and dad and baby111", groups: undefined]
```
```
    var text = "mom and dad and baby111";
    var pattern = /mom( and dad( and baby)?)?/gi;
    var matches = pattern.exec(text)
    console.log(matches);
    //["mom and dad and baby", " and dad and baby", " and baby", index: 0, input: "mom and dad and baby111", groups: undefined]
```

 <font color="red">对于exec方法而言，即使在模式中设置了全局模式g，每次也只会返回一个匹配项，在不设置全局标志的情况下，在同一个字符串上多次调用exec()将始终返回第一个匹配项的信息，在设置全局标志的情况下，每次调用exec则都会在字符串中继续查找新匹配项</font>

 * test()//匹配返回true
 * toLocaleString()、toString()返回正则表达式的字面变量

 * 构造函数属性
   * input：最近一次匹配的字符串
   * lastMatch：最近一次的匹配项
   * lastParen：最近一次匹配的捕获组
   * leftContext：input字符串中lastMatch之前的文本
   * multiline：是否所有表达式都使用多行模式
   * rightContext：input字符串中lastMatch之后的文本

   * 还有多达9个用于存储捕获组的构造函数属性 RegExp.$1... RegExp.$9
