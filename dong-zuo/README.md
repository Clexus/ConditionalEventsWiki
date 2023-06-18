# 动作

当玩家完成条件时，你可以执行各种各样的动作。你也可以使用动作列表中的变量。

| 动作                                                                   | 描述                                                                                                                                                                                                                                                                                                                                                                | 例子                                                                                                                                                                              |
| -------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **message**                                                          | 向玩家发送一条消息                                                                                                                                                                                                                                                                                                                                                         | message: \&aGreat %player%! You''ve just received $5000!                                                                                                                        |
| **centered\_message**                                                | 向玩家发送一条居中的消息                                                                                                                                                                                                                                                                                                                                                      | centered\_message: \&c\&lWELCOME TO THE SERVER                                                                                                                                  |
| **console\_message**                                                 | 向控制台发送一条消息                                                                                                                                                                                                                                                                                                                                                        | console\_message: %player\_name% left the server with IP %player\_ip%                                                                                                           |
| **console\_command**                                                 | 以控制台身份执行命令                                                                                                                                                                                                                                                                                                                                                        | console\_command: eco give %player% 5000                                                                                                                                        |
| **player\_command**                                                  | 以玩家身份执行命令                                                                                                                                                                                                                                                                                                                                                         | player\_command: warp survival                                                                                                                                                  |
| **player\_command\_as\_op**                                          | 以OP身份执行命令                                                                                                                                                                                                                                                                                                                                                         | player\_command\_as\_op: help                                                                                                                                                   |
| **player\_send\_chat**                                               | 从玩家身上发出信息，你可以用它来执行未注册的命令                                                                                                                                                                                                                                                                                                                                          | <p>player_send_chat: &#x26;2Hello</p><p>player_send_chat: /rewards</p>                                                                                                          |
| **teleport**                                                         | 传送玩家，请使用以下格式："teleport: 传送到的世界;x;y;z;偏航角;倾斜角"                                                                                                                                                                                                                                                                                                                     | teleport: lobby;0;60;0;90;0                                                                                                                                                     |
| **give\_potion\_effect**                                             | <p>给玩家一个药水效果. 请使用以下格式: <br>"give_potion_effect: 效果名;持续多少刻;等级"<br>可以在下方找到药水效果列表: <a href="https://hub.spigotmc.org/javadocs/spigot/org/bukkit/potion/PotionEffectType.html">https://hub.spigotmc.org/javadocs/spigot/org/bukkit/potion/PotionEffectType.html</a></p>                                                                                               | give\_potion\_effect: POISON;120;1                                                                                                                                              |
| **remove\_potion\_effect**                                           | 移除玩家药水效果。                                                                                                                                                                                                                                                                                                                                                         | remove\_potion\_effect: POISON                                                                                                                                                  |
| **cancel\_event**                                                    | 是否取消事件,格式："cancel\_event: true/false"                                                                                                                                                                                                                                                                                                                             | cancel\_event: true                                                                                                                                                             |
| **kick**                                                             | 踢出玩家                                                                                                                                                                                                                                                                                                                                                              | kick: \&cWhat are you trying to do?                                                                                                                                             |
| **playsound**                                                        | <p>向玩家播放声音. 请使用以下格式:<br>"playsound: 声音;音量;音高"<br>所有的声音: <a href="https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html">https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html</a><br>用1.8时请用下面这个: <a href="https://helpch.at/docs/1.8.8/index.html?org/bukkit/Sound.html">https://helpch.at/docs/1.8.8/index.html?org/bukkit/Sound.html</a></p> | playsound: BLOCK\_NOTE\_BLOCK\_PLING;10;0.1                                                                                                                                     |
| <p><strong>playsound_resource_</strong><br><strong>pack</strong></p> | 播放材质包音效,格式同上                                                                                                                                                                                                                                                                                                                                                      | <p>playsound_resource_<br>pack:</p><p>my_custom_sound;10;1</p>                                                                                                                  |
| **gamemode**                                                         | 更改玩家的游戏模式，可用的模式：CREATIVE, SURVIVAL, ADVENTURE, SPECTATOR                                                                                                                                                                                                                                                                                                          | gamemode: CREATIVE                                                                                                                                                              |
| **send\_to\_server**                                                 | 把玩家送到一个bungee服务器去                                                                                                                                                                                                                                                                                                                                                 | send\_to\_server: lobby                                                                                                                                                         |
| **actionbar**                                                        | <p>发送actionbar消息，请使用以下格式：<br>"actionbar: 消息;持续时间 (以刻为单位, 20刻 = 1秒)"<br>如果是repetitive事件，请将时间改为0以避免闪烁</p>                                                                                                                                                                                                                                                           | actionbar: &6Welcome to the server;120                                                                                                                                          |
| **title**                                                            | <p>向玩家发送标题信息。请使用以下格式：<br>"title: 渐入时间;停留时间;渐出时间;标题信息;副标题信息"<br>渐入时间、停留时间和渐出时间都必须以刻为单位。如果你只想要主标题，那么就把副标题信息填写为"none"</p>                                                                                                                                                                                                                                            | title: 20;40;20;&6This is a title;none                                                                                                                                          |
| **json\_message**                                                    | 向玩家发送json信息。这些信息可以有添加点击触发事件和鼠标覆盖提示信息的功能。你可以通过以下链接创建json消息：[https://minecraft.tools/en/json\_text.php](https://minecraft.tools/en/json\_text.php)                                                                                                                                                                                                                  | json\_message: {"text":"Welcome to the server","underlined":true,"color":"red"}                                                                                                 |
| **remove\_item**                                                     | 移除玩家X个物品，格式见下方                                                                                                                                                                                                                                                                                                                                                    | remove\_item: DIAMOND;10                                                                                                                                                        |
| **firework**                                                         | 在玩家坐标放烟花，格式见下方                                                                                                                                                                                                                                                                                                                                                    | firework: colors:YELLOW,RED type:BALL fade:AQUA power:0                                                                                                                         |
| **wait**                                                             | 执行下一个动作前等待X秒                                                                                                                                                                                                                                                                                                                                                      | <p> - 'message: &#x26;a3'</p><p> - 'wait: 1'</p><p> - 'message: &#x26;a2'</p><p> - 'wait: 1'</p><p> - 'message: &#x26;a1'</p><p> - 'wait: 1'</p><p> - 'message: &#x26;aGo!'</p> |
| **wait\_ticks**                                                      | 执行下一个动作前等待X刻                                                                                                                                                                                                                                                                                                                                                      | <p> - 'message: &#x26;a3'</p><p> - 'wait_ticks: 20'</p><p> - 'message: &#x26;a2'</p>                                                                                            |

### Remove Item(移除物品) <a href="#remove-item" id="remove-item"></a>

这是 **remove\_item** 动作的格式: `remove_item: <物品种类>;<数量>;datavalue: <数据值>;name: <名字>;lorecontains: <包含的描述>`

{% hint style="warning" %}
数据值，名字和包含的描述都是**可选的**\
**不要使用颜色格式(比如**`&4我的刀`**)**
{% endhint %}

{% hint style="info" %}
你可以在这看到最新的物品种类列表: [https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html ](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html)\
1.8: [https://helpch.at/docs/1.8/org/bukkit/Material.html](https://helpch.at/docs/1.8/org/bukkit/Material.html)
{% endhint %}

你也可以用PlaceholderAPI的Checkitem扩展（https://www.mcbbs.net/thread-1226244-1-1.html）来删除物品：请使用贴内提到的格式。

{% tabs %}
{% tab title="例子1" %}
```
# 这会从玩家背包中移除五个钻石
remove_item: DIAMOND;5
```
{% endtab %}

{% tab title="例子2" %}
```
# 这会从玩家背包中移除五个叫"Unique Diamond"的钻石
remove_item: "DIAMOND;5;name: Unique Diamond"
```
{% endtab %}

{% tab title="例子3" %}
这会从玩家背包中移除一个叫做"<mark style="color:green;">Burst</mark> <mark style="color:orange;">Turret</mark>"的煤炭块(带颜色)

```
remove_item: "%checkitem_remove_mat:COAL_BLOCK,nameequals:&aBurst &6Turret,amt:1%"
```
{% endtab %}
{% endtabs %}

### Firework(放烟花)

这是 **firework** 动作的格式:\
`firework: colors:<颜色1>,<颜色2> type:<种类> fade:<颜色1>,<颜色2> power:<飞行时间>`

{% hint style="warning" %}
fade属性可选，其他的是必需的，你可以添加多个颜色
{% endhint %}

{% hint style="info" %}
烟花颜色: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Color.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Color.html)\
烟花种类: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/FireworkEffect.Type.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/FireworkEffect.Type.html)
{% endhint %}

{% tabs %}
{% tab title="例子1" %}
```
firework: colors:YELLOW,RED type:BALL fade:AQUA power:0
```
{% endtab %}

{% tab title="例子2" %}
```
firework: colors:BLACK,WHITE type:BURST power:1
```
{% endtab %}
{% endtabs %}

### Call Event(唤起其他事件)
