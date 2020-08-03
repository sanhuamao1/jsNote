# [window对象](https://www.runoob.com/jsref/obj-window.html)
浏览器的顶级对象：window
页面中的顶级对象：document
页面中的所有内容都是属于浏览器的，即页面的内容也都是window的
由于页面中所有内容都是window的，所以window可以省略

```js
var num=10
console.log(num)==>实则：console.log(window.num)
document.write()==>实则：window.document.write()
```

### 属性
- `innerHeight`——返回窗口的文档显示区的高
- `innerWidth`——返回窗口的文档显示区的宽度
- `localStorage`

### 方法

1. **系统对话框**

- `alert(message)`
  
  ```js
  //带有一条指定消息和一个确认按钮的警告框。
  alert("hello你好")
  ```

- `prompt(text,defaultText)`
  
  ```js
  //可让用户输入值的对话框
  //第一个参数是显示的文本（可选）；第二个参数是默认的输入文本（可选）
  //如果用户单击提示框的取消按钮，则返回 null。如果用户单击确认按钮，则返回输入字段当前显示的文本。
  var age=prompt("你的年龄是？")
  ```
  
- `confirm(message)`
  
  ```js
  //一个带有指定消息、 OK 和取消按钮的对话框
  //如果用户点击确定按钮，则 confirm() 返回 true。如果点击取消按钮，则 confirm() 返回 false 
  var Isok=confirm("你觉得ok吗？")
  ```

2. **页面加载事件**

- `onload`——页面加载完毕，即页面所有内容，标签、属性、文本、包括外部引入的js文件加载完毕后触发

    ```html
    <script>
    //一般情况下，页面是从上到下加载的，此时并没有加载到按钮所以该事件会报错。
    document.getElementById("btn").onclick=function{
       alert("hello")
    }
    //改正写法,即等页面加载到这个按钮后加载完毕页面后触发事件。这里的window可以省略
    window.onload=function(){
        document.getElementById("btn").onclick=function{
           alert("hello")
        }
    } 
    </script>

    <body>
        <input id="btn" value="按钮" type="button">
    </body>
    ```

3. **反复执行定时器**

- `setInterval(fn,time)`

  **每隔一段时间执行一次函数**。time的单位是毫秒，即1s=1000。它会返回定时器的id值
  
- `clearInterval(id)`

  清理定时器，参数是要清理的定时器的id。

  ```js
  //需要注意的是，最好把timeId设置为全局变量，以便取消定时器时拿来用
  var timeId=setInterval(function(){alert("hello")},1000)
  window.clearInterval(timeId)
  ```
  >[协议倒计时内禁用案例](https://github.com/sanhuamao1/BOM/blob/master/%E5%AE%9A%E6%97%B6%E5%99%A8-%E5%8D%8F%E8%AE%AE%E6%8C%89%E9%92%AE%E7%A6%81%E7%94%A8.html)
4. **一次性定时器**
- `setTimeout(fn,time)`

  code是调用函数后要执行的js代码串；millisec是在执行代码前需要等待的毫秒数，**它只执行一次**。它也会返回一个id值

- `clearTimeout(id)`

  清理定时器。**注意：如果不清理，这个定时器将会一直在内存占空间**
  
    ```js
  //计时器
  var t=setTimeout("alert('5 seconds!')",5000)
  window.clearInterval(t)
    ```

# [location对象](https://www.w3school.com.cn/jsref/dom_obj_location.asp)

Location 对象包含有关当前 URL 的信息。Location 对象是 Window 对象的一个部分，可通过 window.location 属性来访问。

### 属性

- `hash`——设置或返回从井号 (#) 开始的 URL（锚）
- `host`——设置或返回主机名和当前 URL 的端口号   
- `hostname`——设置或返回当前 URL 的主机名
- `href`——设置或返回完整的 URL
- `pathname`——设置或返回当前 URL 的路径部分
- `port`——设置或返回当前 URL 的端口号
- `protocol`——设置或返回当前 URL 的协议
- `search`——设置或返回从问号 (?) 开始的 URL（查询部分）

    ```js
    //举个例子：原地址——https://www.w3school.com.cn/jsref/dom_obj_location.asp
    hash: ""
    host: "www.w3school.com.cn"
    hostname: "www.w3school.com.cn"
    href: "https://www.w3school.com.cn/jsref/dom_obj_location.asp"
    origin: "https://www.w3school.com.cn"
    pathname: "/jsref/dom_obj_location.asp"
    port: ""
    protocol: "https:"
    ```

### 方法

1. **实现页面跳转**

    ```js
    //通过更改属性的方式
    location.href="url"
    //通过assign
    location.assign("url")
    //通过replace,直接替换，没有历史记录，没有后退
    location.replace("url")
    ```
2. **其他**
- `reload()`——重新加载



# [history对象](https://www.w3school.com.cn/jsref/dom_obj_history.asp)

History 对象包含用户（在浏览器窗口中）访问过的 URL。History 对象是 window 对象的一部分，可通过 window.history 属性对其进行访问。

### 属性

- `length`——返回浏览器历史列表中的 URL 数量

### 方法

- `back()`——加载 history 列表中的前一个 URL
- `forward`——加载 history 列表中的下一个 URL
- `go(number|url)`——加载 history 列表中的某个具体页面。num是指你要访问的页面的相对位置，正数为前进，负数为后退


# [navigator对象](https://www.w3school.com.cn/jsref/dom_obj_navigator.asp)

Navigator 对象包含有关浏览器的信息。

### 属性

- `platform`——返回运行浏览器的操作系统平台
- `userAgent`——返回由客户机发送服务器的 user-agent 头部的值
- `appCodeName`——返回浏览器的代码名
- `appName`——返回浏览器的名称
- `cookieEnabled`——判断浏览器中是否启用 cookie 


```js
//举个例子：原地址——https://www.w3school.com.cn/jsref/dom_obj_navigator.asp
platform: Win32
userAgent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/76.0.3809.100 Safari/537.36
appCodeName: Mozilla
appName: Netscape
cookieEnabled: true
```

# [screen 对象](https://www.w3school.com.cn/jsref/dom_obj_screen.asp)

Screen 对象包含有关客户端显示屏幕的信息

### 属性

- `availHeight`——返回显示屏幕的高度 (除 Windows 任务栏之外)

- `availWidth`——返回显示屏幕的宽度 (除 Windows 任务栏之外)

- `height`——返回显示屏幕的高度

- `width`——返回显示器屏幕的宽度

  
