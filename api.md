# API

此插件有一个你可以拿来制作插件的事件：

```java
//此事件会在事件成功执行或一系列动作被成功执行的时候被唤起
@EventHandler
public void actionsExecuted(ConditionalEventsEvent event){
   Player player = event.getPlayer(); //Returns null if not a player event
   String eventName = event.getEvent();
   String actionName = event.getAction();
}
```
