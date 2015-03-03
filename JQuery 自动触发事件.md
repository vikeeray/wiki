常用模拟
有时候，需要通过模拟用户操作，来达到单击的效果。例如在用户进入页面后，就触发click事件，而不需要用户去主动单击。

在JQuery中，可以使用trigger()方法完成模拟操作。例如可以使用下面的代码来触发id为btn的按钮的click事件。
```javascript
$('#btn').trigger("click");
```
这样，当页面加载完毕后，就会立刻输出想要的效果。也可以直接简写click()，来达到同样的效果：
```javascript
$('#btn').click();
```
触发自定义事件
trigger()方法不仅能触发浏览器支持的具有相同名称的事件，也可以触发自定义名称的事件。例如为元素绑定一个“myClick”的事件，JQuery代码如下：
```javascript
$('#btn').bind("myClick", function(){  
  $('#test').append("<p>我的自定义事件.</p>");  
});
```
想要触发这个事件，可以使用以下代码来实现：
```javascript
$('#btn').trigger("myClick");
```
传递数据
trigger(type[，data])方法有两个参数，第1个参数是要触发的事件类型，第2个参数是要传递给事件处理函数的附加数据，以数组形式传递。通常可以通过传递一个参数给回调函数来区别这次事件是代码触发的还是用户触发的。

下面是一个传递数据的例子。
```javascript
$(function(){  
   $('#btn').bind("myClick", function(event, message1, message2){  
                 $('#test').append( "<p>"+message1 + message2 +"</p>");  
    });  
   $('#btn').click(function(){  
        $(this).trigger("myClick",["我的自定义","事件"]);  
   }).trigger("myClick",["我的自定义","事件"]);  
})
```
执行默认操作
trigger()方法触发事件后，会执行浏览器默认操作。例如：
```javascript
$("input").trigger("focus");
```
以上代码不仅会触发为<input>元素绑定的focus事件，也会使<input>元素本身得到焦点（这是浏览器的默认操作）。

如果只想触发绑定的focus事件，而不想执行浏览器默认操作，可以使用jQuery中另一个类似的方法——triggerHandler()方法。
```javascript
$("input").triggerHandler("focus");
```
该方法会触发<input>元素上绑定的特定事件，同时取消浏览器对此事件的默认操作，即文本框只触发绑定的focus事件，不会得到焦点。
