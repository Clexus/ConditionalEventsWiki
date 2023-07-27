# 变量

## 全局变量

这些变量可在任何事件中使用

* **%player%** _(玩家名)_&#x20;
* **%player\_**_**x%** (玩家坐标)_&#x20;
* **%player\_y%** _(玩家坐标)_&#x20;
* **%player\_z%** _(玩家坐标)_&#x20;
* **%player\_world%** _玩家世界_
* **%player\_gamemode%** _玩家游戏模式_
* **%playerhas\_potioneffect\_\<type>%** _(会检查玩家是否有_ [_https://hub.spigotmc.org/javadocs/spigot/org/bukkit/potion/PotionEffectType.html_](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/potion/PotionEffectType.html) _列表中的药水效果. 会返回 'true' 或 'false')_
* **%player\_is\_sneaking%** _(玩家是否蹲下，会返回 'true' 或 'false')_
* **%random\_min\_max%** _(会从 "min" 到 "max" 之间随机选取一个整数. 比如: %random\_-1\_10% 会生成- 1 到 10之间的整数)_&#x20;
* **%playerarmor\_\<type>%** _(某位置护甲材质. 用以下值替换 \<type> : helmet, chestplate, leggings 或 boots)_&#x20;
* **%playerarmor\_name\_\<type>%** _(盔甲名)_
* **%block\_at\_\<x>\_\<y>\_\<z>\_\<world>%** _(某位置特定方块的材质)_
* **%playerblock\_below\_\<distance>%** (玩家脚下一定距离的方块的材质)
* **%playerblock\_above\_\<distance>%** (玩家头上一定距离的方块的材质)
* **%playerblock\_inside%** (玩家所在的方块之中，用于一些特殊的方块比如水、岩浆，又比如你站在头颅/台阶上时的头颅和台阶)
* **%random\_player%** _(随机选择一名服务器内玩家，如果没有会返回"none")_
* **%random\_player\_\<world>%** _(随机选择某世界内玩家，如果没有会返回"none")_
* **%randomword\_\<word1>-\<word2>-\<wordN>%** (随即返回指定的文字，文字之间应该用 '-' 隔开)
* **%is\_nearby\_\<x>\_\<y>\_\<z>\_\<world>\_\<radius>%** _(检查玩家是否在某个世界的某个坐标范围内，会返回 'true' 或 'false')_
* **%world\_time\_\<world>%** _(世界时间，按刻计)_
* **%empty%** _(一个会返回空的特殊变量. 你可以把它用来比较其他也可能返回空值的变量。)_
* **%random\_min\_max%** (会随机生成min到max之间\[包含]的数字，例如%random\_1\_10%会生成1-10之间的数字)

当然，你也可以用PlaceholderAPI的变量：[https://www.mcbbs.net/thread-1226244-1-1.html](https://www.mcbbs.net/thread-1226244-1-1.html)

## 物品变量

这些变量可用于物品事件

* **%item%** (物品的种类，种类参见[https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html))
* **%item\_durability%** _(物品的耐久度/数据值)_
* **%item\_amount%** _(物品数量)_
* **%item\_name%** _(物品不带颜色的名字)_
* **%item\_color\_format\_name%** _(带颜色的物品名)_
* **%item\_lore%** _(物品的描述)_
* **%item\_lore\_line\_X%** _(物品的第X行描述)_
* **%item\_color\_format\_lore%** _(物品的描述，但是带颜色)_
* **%item\_color\_format\_lore\_line\_X%** _(物品的第X行描述，但是带颜色)_
* **%item\_custom\_model\_data%** _(物品的自定义模型数据值)_
* **%item\_meta%** _(提供物品更详细内容的文本，比如药水效果之类的)_

## 方块变量

可用于方块事件

* **%block%** _(方块种类. 所有种类见此:_ [_https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html_](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html)_)_
* **%block\_x%** _(方块X坐标)_
* **%block\_y%** _(Y坐标)_
* **%block\_z%** _(Z坐标)_
* **%block\_world%** _(方块所在世界)_
* **%block\_head\_texture%** _(方块的头颅材质，如果不存在会返回空)_
* **%block\_data%** _(在 1.8-1.12 会返回数字，在1.13+一些方块属性相关的文本.比如台阶有朝向属性，小麦有年龄属性)_&#x20;
* **%block\_below\_\<distance>%** (原方块下方distance格方块的材质_._)
* **%block\_above\_\<distance>%** (上方distance格材质)

## 实体变量

用于实体事件

* **%entity%** _(实体种类. 实体种类见此:_ [_https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html_](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html)_)_
* **%entity\_name%** _(不带颜色的实体名)_
* **%entity\_color\_format\_name%** _(带颜色的实体名)_
* **%entity\_x%** _(实体X坐标)_
* **%entity\_y%** _(Y)_
* **%entity\_z%** _(Z)_
* **%entity\_world%** _(实体所在世界)_

## 受害者变量

用于一些有受害者的事件

* **%victim%** _(实体种类. 实体种类见此:_  [_https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html_](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html)_)_
* **%victim\_name%** _(不带颜色的实体名)_
* **%victim\_color\_format\_name%** _(带颜色的实体名)_
* **%victim\_block\_x%** _(X坐标)_
* **%victim\_block\_y%** _(y)_
* **%victim\_block\_z%** _(z)_
* **%victim\_block\_world%** _(实体所在世界)_

## 目标变量

在某些情况下，比如`player_attack` ,`player_kill` 或 `entity_interact` 里，你可能想要获取目标的变量，那么你只需要在变量前加上**target:**即可。

举个例子，获取目标玩家名,将**%player%**改为**%target:player%。**

或者获取目标玩家身份等级,把**%vault\_rank%** 改为 **%target:vault\_rank%**

这是一个完整的例子:

```
  example:
    type: player_attack
    conditions:
    - '%victim% equals PLAYER'
    - '%item% equals DIAMOND_SWORD'
    - '%item_name% equals Poison Sword'
    actions:
      default:
      - 'message: &a将中毒附加到了 &e%target:player% 身上'
      - 'to_target: give_potion_effect: POISON;120;1'
      - 'to_target: message: &c你被 &e%player%&c 附加了中毒效果!'
```

## 变量中的变量

有些情况下你可能需要把一个变量放在另一个变量中，比如用PlaceholderAPI的Math变量扩展来计算数据并把结果返回到CE的变量中。

格式如下：

**%placeholder\_{inside\_placeholder}%**

%%用来包裹原变量,{}用来包裹内部变量

如: **%world\_time\_{player\_world}%**

底下是完整的例子：

```
# 检查世界时间
example:
    type: player_command
    conditions:
    - "%command% == /world-time"
    actions:
      default:
      - "cancel_event: true"
      - "message: Time in your current world: %world_time_{player_world}%"
```

```
# 用命令检测玩家IP.
# 记得下载OtherPlayer变量扩展
# /papi ecloud download OtherPlayer
example2:
    type: player_command
    conditions:
    - "%command% == /ip or %command% startsWith /ip "
    - "%player_has_permission_conditionalevents.admin% == no execute error1"
    - "%args_length% < 1 execute error2"
    actions:
      default:
      - "cancel_event: true"
      - "message: &7IP of &a%arg_1% &7is: %otherplayer_ip_{arg_1}%"
      error1:
      - "cancel_event: true"
      - "message: &cYou don't have permissions."
      error2:
      - "cancel_event: true"
      - "message: &cYou must use /ip <player>"
```
