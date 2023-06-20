# 其他事件

## ENTITY INTERACT

玩家与实体交互时触发

```yaml
example:
  type: entity_interact
  conditions:
  - '%entity% == PLAYER'
  - '%player_is_sneaking% == yes'
  actions:
    default:
    - "player_command: trade %target:player_name%"
```

{% hint style="success" %}
**变量:**

* ConditionalEvents [实体变量](../bian-liang.md#shi-ti-bian-liang)(用于点击的实体)
* ConditionalEvents [<mark style="color:green;">物品变量</mark>](../bian-liang.md#wu-pin-bian-liang)(用于手上物品)
{% endhint %}

{% hint style="info" %}
此事件可以使用目标玩家变量(%target:XXXXX%)和to\_target动作.
{% endhint %}

## ENTITY SPAWN

实体将要生成时触发.

```yaml
example:
  type: entity_spawn
  conditions:
  - '%entity% == WITHER'
  - '%entity_world% == survival'
  actions:
    default:
    - "cancel_event: true"
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%reason%</mark> (生成原因. 原因列表: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/CreatureSpawnEvent.SpawnReason.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/CreatureSpawnEvent.SpawnReason.html))
* ConditionalEvents [实体变量](../bian-liang.md#shi-ti-bian-liang) (用于将要生成的实体)
{% endhint %}

{% hint style="warning" %}
这个事件不是玩家事件，你不能使用玩家相关的变量.
{% endhint %}

## CONSOLE COMMAND

后台执行命令时触发.

```yaml
example:
  type: console_command
  conditions:
  - '%command% startsWith addperm'
  actions:
    default:
    - 'cancel_event: true'
    - 'console_command: lp group %arg_1% permission set %arg_2%'
```

{% hint style="success" %}
**变量:**

* 同[PLAYER\_COMMAND](wan-jia-shi-jian.md#player-command)
{% endhint %}

{% hint style="warning" %}
这个事件不是玩家事件，你不能使用玩家相关的变量.
{% endhint %}

## REPETITIVE

repetitive事件为每个**玩家**周期性地检查条件。时间在`repetitive_time`下定义，以刻为单位，20秒为1刻

```yaml
example:
  type: repetitive
  repetitive_time: 10
  conditions:
  - '%player_world% == plotworld'
  - '%player_gamemode% != CREATIVE'
  actions:
    default:
    - 'gamemode: CREATIVE'
    - 'actionbar: &6Changing gamemode to creative.;100'
```

{% hint style="info" %}
此事件没有变量，但是你仍然可以使用ConditionalEvents的变量或者PlaceholderAPI的变量。
{% endhint %}

## REPETITIVE SERVER

repetitive server事件为**服务器**周期性地检查条件 (比如本地时间，不能使用玩家变量). 时间在`repetitive_time`下定义，以刻为单位，20秒为1刻

```yaml
example:
  type: repetitive_server
  repetitive_time: 1200
  actions:
    default:
    - 'to_all: message: &7There are &a%server_online% &7players on the server.'
```

{% hint style="info" %}
此事件没有变量，但是你仍然可以使用ConditionalEvents的变量或者PlaceholderAPI的变量。
{% endhint %}

{% hint style="warning" %}
这个事件不是玩家事件，你不能使用玩家相关的变量.
{% endhint %}

## CALL

call 事件是一种特殊的事件，它只能由别的事件通过call\_event执行

```yaml
example:
    type: player_command
    conditions:
    - "%main_command% == /test"
    actions:
      default:
      - "cancel_event: true"
      - "message: This is a test message from event 'example'"
      - "call_event: example2"
example2:
    type: call
    actions:
      default:
      - "message: This message will be sent only when event 'example2' is called"
```

这意味着你现在可以在动作执行后检查条件，只需使用一个补充的call事件. 你也可以从一个事件传递变量到另一个事件来让它变得更具体

```yaml
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

{% hint style="info" %}
此事件没有变量，但是你仍然可以使用ConditionalEvents的变量或者PlaceholderAPI的变量。

记住，call类事件可以用来执行一些将变量传递到别的事件的事情。
{% endhint %}

{% hint style="info" %}
如果某事件由玩家事件唤起，那么此事件也会变成玩家事件。
{% endhint %}

## CUSTOM

可以是任何你想要的自定义事件. 你可以使用别的插件的事件, 更多信息看[自定义事件](../zi-ding-yi-shi-jian.md)页面.
