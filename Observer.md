# 观察者模式
## 要素
- 主题
	报纸《参考消息》
- 观察者
	普通民众（可以成为订阅者的主体）
- 订阅
	一种注册行为，如王欢订阅报纸《参考消息》
- 通知
	主题通知订阅者的行为，如每周三收到《参考消息》
- 更新
	观察者接收消息后，更新自我的行为，如王欢看了参考消息后，了解到卖豆腐很挣钱，去卖豆腐。

## 结构

![](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1513848528635&di=8982df1c5ba17f7455781fef17b5d685&imgtype=0&src=http%3A%2F%2Fimg.mukewang.com%2F57a0d4db0001998708520542.png)

## 接口

1. Subject主题接口（Observable）
	主题接口定义了，一个主题对象必须要实现的四种方法
	- registerObserver()：订阅
	- removeObserver()：取消订阅
	- notifyObserver()：通知
	- setChanged()：主题对象更新
2. Observer观察者接口（Observer）
	观察者接口定义了，一个观察者必须要实现的方法
	- update()：观察者更新
3. 其他接口
	观察者可自我实现一些特定功能，比如观察者需要对外显示，可以自定义Display接口来实现。

## 实例

### Nodejs事件循环

![](http://www.runoob.com/wp-content/uploads/2015/09/event_loop.jpg)

### 要素

- Events：事件，类似于主题
- EventEmitters：主题静态方法，可生产出一个主题
- eventEmitter.on('eventName',eventHandler)
	绑定主题对象与观察者，类似于registerObserver订阅行为，eventHandler为观察者，eventName为实际的主题对象
- eventEmitter.emit('eventName')
	触发事件，类似于notifyObserver通知行为，此时会触发订阅该主题对象的观察者行为，即eventHandler定义的function

### 代码

```js
//引入events模块
var events=require('events')
//生产一个主题
var eventEmitter=new events.EventEmitter()
//定义观察者的更新行为
var eventHandler=function func(){
	--Method--
}
//绑定主题对象与观察者，订阅
eventEmitter.on('eventName',eventHandler)
//主题对象的通知行为,此时会触发观察者的更新行为
eventEmitter.emit('eventName')

```

