
* datalist 跟input搭配使用
```
    <input type="text" value="输入名称" list="star">
    <datalist id="star">
        <option>刘德华</option>
        <option>马德华</option>
        <option>刘若英</option>
        <option>顾小怼</option>
    </datalist>
```
* keygen 密钥对生成器???
* fieldset 将表单内的相关元素分组，打包 legend
* output 输出结果
```
    <fieldset>
        <legend>用户登录</legend>
        <p>用户名：
        <input type="text"></p>
        <p>密码：
        <input type="password"></p>
    </fieldset>
```
* input
![avatar](img/input新增.png)  
* 表单新增属性
![avatar](img/input属性.png)  
 autocomplete:1.提交 2.name属性
 ```
 //点击用户名光标定位
    <label>用户名：
        <input type="text">
    </label>
 ```