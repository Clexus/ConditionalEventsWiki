# 玩家事件

## PLAYER JOIN

玩家加入服务器时触发.

```yaml
example:
  type: player_join
  actions:
    default:
    - 'message: &eWelcome %player% to the server.'
```

{% hint style="info" %}
此事件没有变量，但是你仍然可以使用ConditionalEvents的变量或者PlaceholderAPI的变量。
{% endhint %}

## PLAYER LEAVE

玩家退出服务器时触发.

```yaml
example:
  type: player_leave
  actions:
    default:
    - 'to_all: message: &e%player% left the server.'
```

{% hint style="info" %}
此事件没有变量，但是你仍然可以使用ConditionalEvents的变量或者PlaceholderAPI的变量。
{% endhint %}

## PLAYER PRE JOIN

玩家准备加入服务器时触发.

```yaml
example:
  type: player_pre_join
  conditions:
  - "%name% == Ajneb"
  - "%ip% != 192.168.0.1"
  actions:
    default:
    - "console_message: &8[&c&lALERT&8] &7A user with IP &e%ip% &7tried to join the server using and administrator account."
    - "prevent_join: &c&lERROR!\n&7You can't access this account with that IP."
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%name%</mark> (要加入服务器的玩家名)
* <mark style="color:green;">%ip%</mark> (玩家IP)
* <mark style="color:green;">%uuid%</mark> (玩家UUID)
{% endhint %}

{% hint style="warning" %}
这实际上不是一个玩家事件，这意味着你不能使用玩家相关的变量. 不要感到疑惑, 虽然这个事件叫做 "player pre join", 但是它是一个不包含玩家数据的特殊事件.
{% endhint %}

{% hint style="warning" %}
你不能在这个事件中使用 `cancel_event` 动作. 如果你想阻止玩家进服, 请使用 `prevent_join`.
{% endhint %}

## PLAYER RESPAWN

玩家重生时触发

```yaml
example:
  type: player_respawn
  conditions:
  - '%player_world% == pvp1'
  actions:
    default:
    - "teleport: lobby;0;60;0;90;0"
    - "message: &cYou died. Teleporting you back to the PvP Lobby..."
```

{% hint style="info" %}
此事件没有变量，但是你仍然可以使用ConditionalEvents的变量或者PlaceholderAPI的变量。
{% endhint %}

## PLAYER DEATH

玩家死亡时触发.

```yaml
example:
  type: player_death
  actions:
    default:
    - 'message: &7You died because of: &c%cause%'
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%cause%</mark> (死亡原因. 原因列表: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityDamageEvent.DamageCause.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityDamageEvent.DamageCause.html))
* <mark style="color:green;">%killer\_type%</mark> (如果玩家死于实体，实体的类型，实体列表: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html))
* <mark style="color:green;">%killer\_name%</mark> (如果玩家死于实体，实体不带颜色的名字)
* <mark style="color:green;">%killer\_color\_format\_name%</mark> (带颜色的名字)
{% endhint %}

## PLAYER COMMAND

玩家输入命令时触发.

```yaml
example:
  type: player_command
  conditions:
  - '%command% startsWith //calc or %command% startsWith //solve'
  actions:
    default:
    - 'cancel_event: true'
    - 'kick: &cWhat are you trying to do?'
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%command%</mark> (玩家使用的完整命令，例如"/sudo A B")
* <mark style="color:green;">%main\_command%</mark> (玩家使用的主命令，例如"sudo")
* <mark style="color:green;">%arg\_X%</mark> (命令的第X个参数. 如果命令是 **`/announce hello world`** 那么 %arg\_1% 就是"hello"，%arg\_2% 就是"world")
* <mark style="color:green;">%args\_length%</mark> (命令的参数长度)
* <mark style="color:green;">%args\_substring\_\<arg1>-\<arg2>%</mark> (这个变量会列出从第arg1个参数到第arg2个参数之间的所有参数. 比如, 如果命令是**`/announce I am currently doing a Youtube livestreaming`**, 你可以用%args\_substring\_1-6%来获取第一个参数, 第二个参数,...,第六个参数，显示为**I am currencurrently doing a Youtube**. 如果你不管参数有多长都要获取, 你可以用类似于100的大数来代替6来获取所有参数)
{% endhint %}

## PLAYER CHAT

玩家聊天时触发.

```yaml
example:
  type: player_chat
  conditions:
  - '%message% contains hacker'
  actions:
    default:
    - 'cancel_event: true'
    - 'message: &cIf you found a hacker please report them on our Discord.'
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%message%</mark> (玩家输入的消息)
{% endhint %}

## PLAYER LEVELUP

&#x20;玩家等级改变时触发.

```yaml
example:
  type: player_levelup
  actions:
    default:
    - 'message: &aLevel &6&l%old_level% &7-> &6%new_level%'
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%old\_level%</mark> (玩家先前的等级)
* <mark style="color:green;">%new\_level%</mark> (玩家现在的等级)
{% endhint %}

## PLAYER WORLD CHANGE

玩家改变所在世界时触发.

```yaml
example:
  type: player_world_change
  actions:
    default:
    - 'message: &7Moving to &e%world_to% &7world'
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%world\_from%</mark> (先前所在的世界)
* <mark style="color:green;">%world\_to%</mark> (玩家前往的世界)
* <mark style="color:green;">%online\_players\_from%</mark> (先前玩家所在世界的玩家数量)
* <mark style="color:green;">%online\_players\_to%</mark> (玩家前往世界的玩家数量)
{% endhint %}

## PLAYER ATTACK

玩家攻击时触发.

```yaml
example:
  type: player_attack
  conditions:
  - '%victim% == PLAYER'
  - '%item% == DIAMOND_SWORD'
  - '%item_name% == Super Sword'
  - '%random_1_10% >= 8'
  actions:
    default:
    - 'message: &aYour diamond sword poison effect was activated! &6%target:player_name% &ais now poisoned!'
    - 'to_target: give_potion_effect: POISON;120;1'
    - 'to_target: message: &cYou were poisoned by &e%player%&c!'
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%damage%</mark> (玩家所造成的伤害)
* <mark style="color:green;">%attack\_type%</mark> (伤害物的种类，对于抛射物来说，可以是: ARROW, TRIDENT, SNOWBALL. 如果伤害并非来源于抛射物, 那么会返回PLAYER)
* <mark style="color:green;">%original\_damage%</mark> (玩家造成的原始伤害)
* ConditionalEvents <mark style="color:green;">物品变量</mark> (用于手上物品)
* ConditionalEvents <mark style="color:green;">受害者变量</mark>
{% endhint %}

{% hint style="info" %}
此事件可以使用目标玩家变量(%target:XXXXX%)和to\_target动作.
{% endhint %}

## PLAYER KILL

玩家击杀生物时触发

```yaml
example:
  type: player_kill
  conditions:
  - '%victim% == COW'
  actions:
    default:
    - 'message: &aAre you happy killing this cow?'
```

{% hint style="success" %}
**变量:**

* ConditionalEvents [<mark style="color:green;">物品变量</mark>](../bian-liang.md#wu-pin-bian-liang) (用于手上物品)
* ConditionalEvents [<mark style="color:green;">受害者变量</mark>](../bian-liang.md#shou-hai-zhe-bian-liang)
{% endhint %}

{% hint style="info" %}
此事件可以使用目标玩家变量(%target:XXXXX%)和to\_target动作.
{% endhint %}

## PLAYER DAMAGE

玩家受伤时触发.

```yaml
example:
  type: player_damage
  conditions:
  - '%cause% == DROWNING'
  actions:
    default:
    - 'cancel_event: true'
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%cause%</mark> (受伤的原因。原因列表: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityDamageEvent.DamageCause.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityDamageEvent.DamageCause.html))
* <mark style="color:green;">%damage%</mark> (玩家受到的伤害)
* <mark style="color:green;">%original\_damage%</mark> (玩家受到的原始伤害)
* <mark style="color:green;">%damager\_type%</mark> (如果玩家受到的伤害来自实体，实体种类，种类列表: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html))
* <mark style="color:green;">%damager\_name%</mark> (如果玩家受到的伤害来自实体，实体不带颜色的名字)
* <mark style="color:green;">%damager\_color\_format\_name%</mark> (带颜色的名字)
{% endhint %}

## PLAYER ARMOR

玩家穿戴护甲时触发.

```yaml
example:
  type: player_armor
  conditions:
  - '%armor_type% == HELMET'
  - '%equip_type% == EQUIP'
  - '%item_name% == Super Diamond Helmet'
  - '%player_has_permission_items.super_diamond_helmet% == false'
  actions:
    default:
    - 'cancel_event: true'
    - "message: &cYou don't have permissions to equip that item!"
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%armor\_type%</mark> (护甲种类. 可为: HELMET, CHESTPLATE, LEGGINGS or BOOTS)
* <mark style="color:green;">%equip\_type%</mark> (可为: EQUIP(装备) 或 UNEQUIP(脱下))
* ConditionalEvents [物品变量](../bian-liang.md#wu-pin-bian-liang)
{% endhint %}

## PLAYER TELEPORT

玩家传送时触发

```yaml
example:
  type: player_teleport
  conditions:
  - "%cause% == NETHER_PORTAL"
  actions:
    default:
    - 'cancel_event: true'
    - "message: &cYou can't use nether portals!"
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%cause%</mark> (传送原因. 原因列表: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/player/PlayerTeleportEvent.TeleportCause.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/player/PlayerTeleportEvent.TeleportCause.html))
* <mark style="color:green;">%from\_x%</mark> (玩家原来所在处的X坐标)
* <mark style="color:green;">%from\_y%</mark> (Y)
* <mark style="color:green;">%from\_z%</mark> (Z)
* <mark style="color:green;">%from\_world%</mark> (原来的世界)
* <mark style="color:green;">%to\_x%</mark> (现在的X坐标)
* <mark style="color:green;">%to\_y%</mark> (Y)
* <mark style="color:green;">%to\_z%</mark> (Z)
* <mark style="color:green;">%to\_world%</mark> (现在的世界)
{% endhint %}

## PLAYER BED ENTER

玩家上床时触发.

```yaml
example:
  type: player_bed_enter
  conditions:
  - "%result% == OK"
  - "%player_world% == spawn"
  actions:
    default:
    - "cancel_event: true"
    - "message: &cYou can't sleep on this world."
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%result%</mark> (上床原因? 原因列表: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/player/PlayerBedEnterEvent.BedEnterResult.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/player/PlayerBedEnterEvent.BedEnterResult.html))
{% endhint %}

{% hint style="warning" %}
只在1.13+可用!
{% endhint %}

## PLAYER SWAP HAND

玩家用快捷键切换主副手物品时触发.

```yaml
example:
  type: player_swap_hand
  actions:
    default:
    - "cancel_event: true"
```

{% hint style="success" %}
**变量:**

* ConditionalEvents [物品变量](../bian-liang.md#wu-pin-bian-liang) (用于手上物品)
{% endhint %}

## PLAYER FISH

玩家钓鱼时触发.

```yaml
example:
  type: player_fish
  conditions:
  - "%state% == CAUGHT_ENTITY"
  - "%caught_type% == COW or %caught_type% == PIG"
  actions:
    default:
    - "cancel_event: true"
    - "message: &cYou can't use a fishing rod on animals!"
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%state%</mark> (当前钓鱼的状态. 状态列表: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/player/PlayerFishEvent.State.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/player/PlayerFishEvent.State.html))
* <mark style="color:green;">%caught\_type%</mark> (抓到的实体. 实体列表: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html))
* ConditionalEvents [<mark style="color:green;">物品变量</mark>](../bian-liang.md#wu-pin-bian-liang) (如存在，表示钓到的物品)
{% endhint %}

## PLAYER OPEN INVENTORY

玩家打开容器时触发.

```yaml
example:
  type: player_open_inventory
  conditions:
  - "%inventory_type% == MERCHANT"
  actions:
    default:
    - "message: &cVillager trading is disabled."
    - "cancel_event: true"
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%inventory\_type%</mark> (打开容器的种类. 所有的种类: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/inventory/InventoryType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/inventory/InventoryType.html))
* <mark style="color:green;">%inventory\_title%</mark> (没有颜色代码的容器名称)
{% endhint %}

## PLAYER CLOSE INVENTORY

玩家关闭容器时触发

```yaml
example:
  type: player_close_inventory
  conditions:
  - "%inventory_type% == MERCHANT"
  actions:
    default:
    - "message: &c已关闭交易界面..."
```

## PLAYER STATISTIC

玩家统计数据更改时触发, 比如方块被破坏，跳跃，捡起物品...

```yaml
example:
  type: player_statistic
  one_time: true
  conditions:
  - "%statistic_name% == MINE_BLOCK"
  - "%block% == EMERALD_ORE"
  - "%new_value% == 5"
  actions:
    default:
    - "centered_message: &a&lAchievement Unlocked!"
    - "centered_message:  "
    - "centered_message:  &eMine 5 Emerald Blocks."
    - "centered_message:  "
    - "centered_message:  &aRewards:"
    - "centered_message:  &7- $500"
    - "console_command: eco give %player% 500"
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%statistic\_name%</mark> (发生更改的统计数据. 列表: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Statistic.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Statistic.html))
* <mark style="color:green;">%new\_value%</mark> (统计数据的新值)
* <mark style="color:green;">%previous\_value%</mark> (旧值)
* <mark style="color:green;">%entity%</mark> (如果存在的话，与统计数据相关的实体. 实体列表: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html))
* <mark style="color:green;">%block%</mark> (如果存在的话, 与统计数据相关的方块. 方块列表: [https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html))
{% endhint %}



## PLAYER SNEAK

玩家切换下蹲时触发.

```yaml
example:
  type: player_sneak
  conditions:
  - "%is_sneaking% == true execute actions1"
  actions:
    actions1:
    - "message: &eSneaking"
    default:
    - "message: &eCancelling sneak"
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%is\_sneaking%</mark> (玩家是否下蹲. 会返回 "true" 或 "false")
{% endhint %}

## PLAYER RUN

玩家切换奔跑状态时触发(开始或停止都可以)

```
example:
  type: player_run
  conditions:
  - "%is_running% == true execute actions1"
  actions:
    actions1:
    - "message: &eRunning"
    default:
    - "message: &eStopped running"
```

{% hint style="success" %}
**变量：**

* <mark style="color:green;">%is\_running%</mark> (玩家是否在奔跑，会返回“true”或“false“）
{% endhint %}

## PLAYER REGAIN HEALTH

玩家回血时触发

```yaml
example:
  type: player_regain_health
  conditions:
  - "%reason% == SATIATED"
  actions:
    default:
    - 'cancel_event: true'
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%reason%</mark> (回血的原因. 原因列表: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityRegainHealthEvent.RegainReason.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityRegainHealthEvent.RegainReason.html))
* <mark style="color:green;">%amount%</mark> (回血量)
{% endhint %}
