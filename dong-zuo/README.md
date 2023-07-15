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
| **damage**                                                           | 对目标造成一定伤害                                                                                                                                                                                                                                                                                                                                                         | damage: 5                                                                                                                                                                       |
| **close\_inventory**                                                 | 关闭玩家打开的容器界面                                                                                                                                                                                                                                                                                                                                                       | <p>close_inventory<br>(对，就这么填)</p>                                                                                                                                              |
| **set\_on\_fire**                                                    | 点燃玩家，时间按刻计算\[20刻=1秒]                                                                                                                                                                                                                                                                                                                                              | set\_on\_fire: 60                                                                                                                                                               |

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
`firework: colors:<颜色1>,<颜色2> type:<种类> fade:<颜色1>,<颜色2> power:<飞行时间>(可选，定义位置)location:<x>;<y>;<z>;<世界>`

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
firework: colors:BLACK,WHITE type:BURST power:1 location:%block_x%;%block_y%;%block_z%;%block_world%
```
{% endtab %}
{% endtabs %}

### Particle(生成粒子)

在玩家所在位置生成一个粒子，请使用此格式:`particle: effect:<粒子种类> offset:<x方向偏移量，以此类推>;<y>;<z> speed:<粒子速度> amount:<数量> (可选)location:<x>;<y>;<z>;<世界名>`

{% hint style="info" %}
粒子种类: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html)\
offset: 要生成的粒子的分散分布状态
{% endhint %}

{% hint style="info" %}
你可以生成一个有颜色的红石粒子，只需要使用以下格式: \
`REDSTONE;<red>;<green>;<blue>`\
: [https://htmlcolorcodes.com/](https://htmlcolorcodes.com/)
{% endhint %}

{% hint style="warning" %}
只在 1.9+ 工作
{% endhint %}

{% tabs %}
{% tab title="例子 1" %}
```yaml
particle: effect:EXPLOSION_LARGE offset:0.1;0.1;0.1 speed:1 amount:5
```
{% endtab %}

{% tab title="例子 2" %}
```yaml
particle: effect:REDSTONE;25;229;198 offset:0.1;0
```
{% endtab %}
{% endtabs %}

### Call Event(唤起其他事件)

执行一个“call”类事件，请使用此格式:`call_event: <事件名>;%变量名1%=<值1>;%变量名N%=<值N>`

{% hint style="info" %}
你可以传递多个变量，但是它们是可选的，你也可以不传递任何变量
{% endhint %}

```
example:
    type: player_command
    conditions:
    - "%main_command% == /test"
    actions:
      default:
      - "cancel_event: true"
      - "message: This is a test message from event 'example'"
      - "call_event: example2;%example_variable%=Something"

example2:
    type: call
    conditions:
    - "%example_variable% == Something"
    actions:
      default:
      - "message: This message will be sent only when event 'example2' is called"
```

## Execute Action Group(执行动作组)

从事件随机执行动作组。请使用以下格式`execute_action_group: <组1>:<概率1>;<组N>:<概率N>` <组N>指的是事件创造的动作组，<概率N>指的是这个组被执行的概率(加起来可以不等于100%，它们是分别计算的)

{% hint style="info" %}
如果你只想执行一个单独的动作组, 而不要随机概率, 可以直接这么写: `execute_action_group: <组1>:100`
{% endhint %}

```yaml
example:
    type: player_command
    conditions:
    - "%main_command% == /randomfirework"
    actions:
      default:
      - "cancel_event: true"
      - "execute_action_group: firework1:70;firework2:30;firework3:30"
      firework1:
      - "firework: colors:YELLOW,RED type:BALL fade:AQUA power:0"
      firework2:
      - "firework: colors:BLACK,WHITE type:BURST power:1"
      firework3:
      - "firework: colors:GREEN,BLUE type:BURST power:1"
```
