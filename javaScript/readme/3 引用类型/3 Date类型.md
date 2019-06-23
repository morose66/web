# Date类型
* 创建日期对象 new Date(),不传参数的情况下，自动获得当前日期和时间，如果想根据特定的日期和时间创建对象，必须传入该日期的毫秒数
* Date.parse()接收一个字符串参数，根据这个字符串参数返回相应的毫秒数 P99可以转换的格式
```
返回2004年5月25日的日期对象
console.log(new Date(Date.parse("May 25,2004")))//Tue May 25 2004 00:00:00 GMT+0800 (中国标准时间)

```
`如果直接把参数传给Date构造函数，也会在后台调用Date.parse（）`,上面代码可简化为new Date("May 25,2004")
* Date.UTC()方法同样也返回表示日期的毫秒数，构建时使用不同的信息。（年份，月[从0开始]，日，时[0-23]，分，秒）
```
console.log(new Date(2004,4,25))
//Tue May 25 2004 00:00:00 GMT+0800 (中国标准时间)

```
* Date.now()方法返回当前时间的毫秒数
* 可以使用+操作符获取Date对象时间戳
* 继承的方法
   * toLocaleString:按浏览器设置的地区相适应的格式返回时间
   * toString:返回带有时区信息的日期时间
   * valueOf:返回日期的毫秒表示
* 日期格式化方法
```
    console.log(new Date().toDateString())//Sun Jun 23 2019 星期几、月、日、年
    console.log(new Date().toTimeString())
    //16:49:30 GMT+0800 (中国标准时间) 时、分、秒和时区
    console.log(new Date().toLocaleDateString())
    //2019/6/23
    console.log(new Date().toLocaleTimeString())
    //下午4:49:30
    console.log(new Date().toUTCString())
    //Sun, 23 Jun 2019 08:49:30 GMT
```
* 其余的Date类型方法 p102