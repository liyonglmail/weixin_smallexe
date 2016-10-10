## 微信小程序之事件绑定

### 》》》什么是事件
- 事件是视图层到逻辑层的通讯方式。
- 事件可以将用户的行为反馈到逻辑层进行处理。
- 事件可以绑定在组件上，当达到触发事件，就会执行逻辑层中对应的事件处理函数。
- 事件对象可以携带额外信息，如id, dataset, touches。

### 》》》事件分类
- touchstart    手指触摸
- touchmove     手指触摸后移动
- touchcancel   手指触摸动作被打断，如弹窗和来电提醒
- touchend      手指触摸动作结束
- tap           手指触摸后离开
- longtap       手指触摸后后，超过350ms离开

### 》》》事件绑定

事件绑定的写法同组件的属性，以 key、value 的形式。

- key 以bind或catch开头，然后跟上事件的类型，如bindtap, catchtouchstart
- value 是一个字符串，需要在对应的 Page 中定义同名的函数。不然当触发事件的时候会报错。
bind事件绑定不会阻止冒泡事件向上冒泡，catch事件绑定可以阻止冒泡事件向上冒泡。

上面简单介绍了小程序事件基础，是时候彰显"事件"的威力：
- 单击(tap)
- 双击(dbtap)
- 长按(longtap)
- 滑动手势
- 多点触控

#### 单击
单击事件由touchstart、touchend组成,touchend后出发tap事件。
![](./images/click.gif)

```
<view>
  <button type="primary" bindtap="mytap" bindtouchstart="mytouchstart" bindtouchend="mytouchend">点我吧</button>
</view>
```

```javascript
mytouchstart: function(e){
    console.log(e.timeStamp + '- touch start')
    this.setData({startPoint: [e.touches[0].pageX, e.touches[0].pageY]});
},
mytouchend: function(e){
    console.log(e.timeStamp + '- touch end')
},
mytap: function(e){
    console.log(e.timeStamp + '- tap')
}
```