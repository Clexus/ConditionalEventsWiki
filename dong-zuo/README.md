# 动作

当玩家完成条件时，你可以执行各种各样的动作。你也可以使用动作列表中的变量。

| 动作                                                                   | 描述                                                                                                                                                                                                                                                                                                                                                                                                             | 例子                                                                                                                                                                              |
| -------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **message**                                                          | 向玩家发送一条消息                                                                                                                                                                                                                                                                                                                                                                                                      | message: \&aGreat %player%! You''ve just received $5000!                                                                                                                        |
| **centered\_message**                                                | 向玩家发送一条居中的消息                                                                                                                                                                                                                                                                                                                                                                                                   | centered\_message: \&c\&lWELCOME TO THE SERVER                                                                                                                                  |
| **console\_message**                                                 | 向控制台发送一条消息                                                                                                                                                                                                                                                                                                                                                                                                     | console\_message: %player\_name% left the server with IP %player\_ip%                                                                                                           |
| **console\_command**                                                 | 以控制台身份执行命令                                                                                                                                                                                                                                                                                                                                                                                                     | console\_command: eco give %player% 5000                                                                                                                                        |
| **player\_command**                                                  | 以玩家身份执行命令                                                                                                                                                                                                                                                                                                                                                                                                      | player\_command: warp survival                                                                                                                                                  |
| **player\_command\_as\_op**                                          | 以OP身份执行命令                                                                                                                                                                                                                                                                                                                                                                                                      | player\_command\_as\_op: help                                                                                                                                                   |
| **player\_send\_chat**                                               | 从玩家身上发出信息，你可以用它来执行未注册的命令                                                                                                                                                                                                                                                                                                                                                                                       | <p>player_send_chat: &#x26;2Hello</p><p>player_send_chat: /rewards</p>                                                                                                          |
| **teleport**                                                         | 传送玩家，请使用以下格式："teleport: 传送到的世界;x;y;z;偏航角;倾斜角"                                                                                                                                                                                                                                                                                                                                                                  | teleport: lobby;0;60;0;90;0                                                                                                                                                     |
| **give\_potion\_effect**                                             | <p>给玩家一个药水效果. 请使用以下格式: <br>"give_potion_effect: 效果名;持续多少刻;等级"<br>可以在下方找到药水效果列表: <a href="https://hub.spigotmc.org/javadocs/spigot/org/bukkit/potion/PotionEffectType.html">https://hub.spigotmc.org/javadocs/spigot/org/bukkit/potion/PotionEffectType.html</a></p>                                                                                                                                            | give\_potion\_effect: POISON;120;1                                                                                                                                              |
| **remove\_potion\_effect**                                           | 移除玩家药水效果。                                                                                                                                                                                                                                                                                                                                                                                                      | remove\_potion\_effect: POISON                                                                                                                                                  |
| **cancel\_event**                                                    | 是否取消事件,格式："cancel\_event: true/false"                                                                                                                                                                                                                                                                                                                                                                          | cancel\_event: true                                                                                                                                                             |
| **kick**                                                             | 踢出玩家                                                                                                                                                                                                                                                                                                                                                                                                           | kick: \&cWhat are you trying to do?                                                                                                                                             |
| **playsound**                                                        | <p>向玩家播放声音. 请使用以下格式:<br>"playsound: 声音;音量;音高(可选,位置);&#x3C;x>,&#x3C;y>,&#x3C;z>,&#x3C;世界名>"<br>所有的声音: <a href="https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html">https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html</a><br>用1.8时请用下面这个: <a href="https://helpch.at/docs/1.8.8/index.html?org/bukkit/Sound.html">https://helpch.at/docs/1.8.8/index.html?org/bukkit/Sound.html</a></p> | <p>playsound: BLOCK_NOTE_BLOCK_PLING;10;0.1<br>playsound: BLOCK_NOTE_BLOCK_PLING;10;2;100,60,-127,world</p>                                                                     |
| <p><strong>playsound_resource_</strong><br><strong>pack</strong></p> | 播放材质包音效,格式同上                                                                                                                                                                                                                                                                                                                                                                                                   | <p>playsound_resource_<br>pack:</p><p>my_custom_sound;10;1</p>                                                                                                                  |
| **gamemode**                                                         | 更改玩家的游戏模式，可用的模式：CREATIVE, SURVIVAL, ADVENTURE, SPECTATOR                                                                                                                                                                                                                                                                                                                                                       | gamemode: CREATIVE                                                                                                                                                              |
| **send\_to\_server**                                                 | 把玩家送到一个bungee服务器去                                                                                                                                                                                                                                                                                                                                                                                              | send\_to\_server: lobby                                                                                                                                                         |
| **actionbar**                                                        | <p>发送actionbar消息，请使用以下格式：<br>"actionbar: 消息;持续时间 (以刻为单位, 20刻 = 1秒)"<br>如果是repetitive事件，请将时间改为0以避免闪烁</p>                                                                                                                                                                                                                                                                                                        | actionbar: &6Welcome to the server;120                                                                                                                                          |
| **title**                                                            | <p>向玩家发送标题信息。请使用以下格式：<br>"title: 渐入时间;停留时间;渐出时间;标题信息;副标题信息"<br>渐入时间、停留时间和渐出时间都必须以刻为单位。如果你只想要主标题，那么就把副标题信息填写为"none"</p>                                                                                                                                                                                                                                                                                         | title: 20;40;20;&6This is a title;none                                                                                                                                          |
| **json\_message**                                                    | 向玩家发送json信息。这些信息可以有添加点击触发事件和鼠标覆盖提示信息的功能。你可以通过以下链接创建json消息：[https://minecraft.tools/en/json\_text.php](https://minecraft.tools/en/json\_text.php)                                                                                                                                                                                                                                                               | json\_message: {"text":"Welcome to the server","underlined":true,"color":"red"}                                                                                                 |
| **remove\_item**                                                     | 移除玩家X个物品，格式见下方                                                                                                                                                                                                                                                                                                                                                                                                 | remove\_item: DIAMOND;10                                                                                                                                                        |
| **firework**                                                         | 在玩家坐标放烟花，格式见下方                                                                                                                                                                                                                                                                                                                                                                                                 | firework: colors:YELLOW,RED type:BALL fade:AQUA power:0                                                                                                                         |
| **wait**                                                             | 执行下一个动作前等待X秒                                                                                                                                                                                                                                                                                                                                                                                                   | <p> - 'message: &#x26;a3'</p><p> - 'wait: 1'</p><p> - 'message: &#x26;a2'</p><p> - 'wait: 1'</p><p> - 'message: &#x26;a1'</p><p> - 'wait: 1'</p><p> - 'message: &#x26;aGo!'</p> |
| **wait\_ticks**                                                      | 执行下一个动作前等待X刻                                                                                                                                                                                                                                                                                                                                                                                                   | <p> - 'message: &#x26;a3'</p><p> - 'wait_ticks: 20'</p><p> - 'message: &#x26;a2'</p>                                                                                            |
| **damage**                                                           | 对目标造成一定伤害                                                                                                                                                                                                                                                                                                                                                                                                      | damage: 5                                                                                                                                                                       |
| **close\_inventory**                                                 | 关闭玩家打开的容器界面                                                                                                                                                                                                                                                                                                                                                                                                    | <p>close_inventory<br>(对，就这么填)</p>                                                                                                                                              |
| **set\_on\_fire**                                                    | 点燃玩家，时间按刻计算\[20刻=1秒]                                                                                                                                                                                                                                                                                                                                                                                           | set\_on\_fire: 60                                                                                                                                                               |
| **freeze**                                                           | 冰冻玩家，时间按刻计算，只在1.17+生效                                                                                                                                                                                                                                                                                                                                                                                          | freeze: 200                                                                                                                                                                     |
| **heal**                                                             | 为玩家恢复一定血量                                                                                                                                                                                                                                                                                                                                                                                                      | heal: 10                                                                                                                                                                        |

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

### Remove Item Slot(移除特定槽位物品)

从玩家的特定背包槽位移除任意数量的物品，格式:\
`remove_item_slot: <槽位>;<数量>`

{% hint style="info" %}
**可用槽位:** HAND, OFF\_HAND, HELMET, CHESTPLATE, LEGGINGS, BOOTS\
对应主手 副手 头盔 胸甲 护腿 靴子的槽位\
其他可用槽位见此[https://proxy.spigotmc.org/d3e11b631e22f45fc07c3fcd1c7000b2245fed78?url=http%3A%2F%2Fi.imgur.com%2F3YCrfC8.png](https://proxy.spigotmc.org/d3e11b631e22f45fc07c3fcd1c7000b2245fed78?url=http%3A%2F%2Fi.imgur.com%2F3YCrfC8.png)
{% endhint %}

```
remove_item_slot: HAND;1
remove_item_slot: 0;1
```

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

### Give Item(给予物品)

给玩家一个物品. 格式如下: `give_item: id:<物品ID>;<属性>:<对应值>;<属性N>:<对应值N>`

{% hint style="info" %}
**全局属性:**

id:<物品ID> (必须, 可用ID见此: [https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html))\
amount:<数量>\
durability:<耐久值>\
custom\_model\_data:<自定义模型数据>\
name:<名字>\
lore:<第一行迷哦书>|<第N行描述>\
enchants:<附魔1>-<等级1>|<附魔N>-<等级N> (所有附魔名称: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html))\
flags:<标志1>|<标志N> (所有可用标志: [https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/ItemFlag.html](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/ItemFlag.html))\


**仅限玩家头颅的属性:**

skull\_texture:<头颅材质值> (头颅的材质值(Texture value). 见此: [https://minecraft-heads.com/custom-heads](https://minecraft-heads.com/custom-heads))\
skull\_owner:<头颅主人> (玩家名)\
skull\_id:<头颅ID> (头颅的ID，可在这里找到 [https://minecraft-heads.com/custom-heads](https://minecraft-heads.com/custom-heads))
{% endhint %}

{% tabs %}
{% tab title="例子 1" %}
```yaml
give_item: id:IRON_HELMET;amount:1;name:&6Basic Helmet
```
{% endtab %}

{% tab title="例子 2" %}
```yaml
give_item: id:NETHERITE_SWORD;amount
```
{% endtab %}

{% tab title="例子3" %}
```
give_item: id:PLAYER_HEAD;amount:16;skull_owner:%player_name%
```
{% endtab %}
{% endtabs %}

### Drop Item(掉落物品)

在某个位置掉落物品

格式: `drop_item: location:<x>,<y>,<z>,<world>;id:<id>;<property>:<value>;<propertyN>:<valueN>`

{% hint style="info" %}
全局属性：

location:\<x>,\<y>,\<z>,<世界名>(必填)

其他的和上方一样&#x20;
{% endhint %}

```
drop_item: location:%block_x%,%block_y%,%block_z%,%block_world%;id:DIAMOND;name:&bUnique Diamond
```

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

### Execute Action Group(执行动作组)

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

### Set Block(设置方块)

在世界的特定位置放置方块，请使用此格式：`setblock: location:<x>,<y>,<z>,<世界名>;id:<方块id>;block_data:<方块数据>` 只在1.13+可以使用

{% hint style="info" %}
**一般属性:**

location:\<x>,\<y>,\<z>,<世界名> (必须)

\
**可选属性：**

**Block data(方块数据)**

block data 属性是可选的，代表了方块可以有的某些状态。比如台阶方块可以有东南西北四个朝向。农作物方块有生长年龄。

请使用此格式添加: `<属性1>=<值1>,<属性N>=<值N>`

所有可用的方块数据: [https://minecraft.fandom.com/wiki/Java\_Edition\_data\_values#Block\_states](https://minecraft.fandom.com/wiki/Java\_Edition\_data\_values#Block\_states)

\
**Skull data(头颅数据)**

skull\_texture:<头颅纹理值> (头颅纹理值可在此找到: [https://minecraft-heads.com/custom-heads](https://minecraft-heads.com/custom-heads))\
skull\_owner:<头颅主人> (玩家名)
{% endhint %}

{% tabs %}
{% tab title="例子 1" %}
```yaml
set_block: location:50,50,-256,world;id:DIAMOND_BLOCK
```
{% endtab %}

{% tab title="例子 2" %}
```yaml
# 用于再生方块
set_block: location:%block_x%,%block_y%,%block_z%,%block_world%;%id:%block%;block_data:%block_data%
```
{% endtab %}

{% tab title="例子 3" %}
```yaml
set_block: location:50,50,-256,world;id:CHEST;block_data:facing=north
```
{% endtab %}
{% endtabs %}
