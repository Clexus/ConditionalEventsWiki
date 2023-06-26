# 配置文件教程

每一个事件都遵循一定的格式，在下方你可以找到可用选项。每次更改文件后，请使用/ce reload重载

## Type(事件种类)

需要检测事件的种类，你可以在[此页面](shi-jian-zhong-lei/)找到更多关于事件种类的信息。

```
type: block_interact
```

## Conditions(条件)

事件需要检测的条件。如果条件通过，一些特定的动作会被执行。你可以在[此页面](tiao-jian.md)找到更多关于条件的信息

```
conditions:
- '%victim% == PLAYER'
- '%item% == DIAMOND_SWORD'
- '%item_name% == 极霸剑'
- '%random_1_10% >= 8'
```

## Actions(动作)

条件通过后事件需要执行的动作，更多信息[见此](dong-zuo/)

```
actions:
  default:
  - "cancel_event: true"
  - "message: &c此世界不能破坏方块."
  - "playsound: BLOCK_NOTE_BLOCK_PLING;10;0.1"
```

## Action Groups(动作组)

动作永远都会在特定名称的动作组下被执行。当事件的条件被完成时，默认执行"default"组下的事件，除非指定了其他动作组。

例如，如果你向事件添加了冷却，如果玩家的事件未处于冷却中，default组的事件将会被执行。如果玩家处于冷却中，那么将会执行cooldown组的动作。

```
actions:
  default: []
  cooldown: []
```

[execute](tiao-jian.md#zhi-hang-execute-lei-xuan-xiang)选项可以让你从不同的动作组中执行动作

## Ignore With Permission(忽略权限)

你可以设置一个忽略此事件的权限，如果一个玩家有对应的权限，那么他在完成条件后将不会执行对应动作

```
ignore_with_permission: conditionalevents.ignore.event4
```

## Ignore If Cancelled(如取消则忽略)

当此选项开启时，如果这个事件被其他插件取消了，那么动作将不会执行。

```
ignore_if_cancelled: true
```

## Allow Math formulas in Conditions(允许条件中使用数学公式)

如果你想在条件中使用数学公式，你需要开启此选项

```
allow_math_formulas_in_conditions: true
conditions:
- '%command% equals /test-kills'
- '%statistic_player_kills% >= %statistic_deaths%*2'
```

## One Time(一次性)

如果设置为true，则此事件只会执行一次。你可以设置一个动作组来执行玩家执行一次之后的动作。

{% hint style="warning" %}
动作组名**必须为**“one\_time”
{% endhint %}

```
one_time: true
actions:
  one_time:
  - "message: &cYou can claim this reward just once!"
```

## Cooldown(冷却)

用这个你可以设置时间的冷却时间。添加专门的动作组可以在玩家处于冷却时间内时执行动作。

{% hint style="warning" %}
动作组名**必须为**“cooldown”
{% endhint %}

{% hint style="warning" %}
OP会跳过冷却时间，所以确保你测试的时候不是OP
{% endhint %}

```
cooldown: 3600
actions:
  cooldown:
  - "cancel_event: true"
  - "message: &cYou need to wait &e%time% &cbefore claiming your reward again."
```

## Enabled(是否开启)

设置为true开启此事件，设置为false关闭

```
enabled: false
```

## Repetitive Time(重复时间)

如果事件种类设置为repetitive或者repetitive\_server，此选项会定义事件重复的时间间隔(以刻计，20刻=1秒)

```
type: repetitive
repetitive_time: 10
```

## Prevent Cooldown/One Time Activation(阻止冷却/一次性事件执行)

使用execute执行其他动作时这个选项很有用，你可以定义一个动作列表，把你不想触发冷却/一次性事件的动作放进去。

```
prevent_cooldown_activation:
- "actions2"
prevent_one_time_activation:
- "actions2"
- "actions3"
```

在某些情况下，一些动作组仅用于向玩家显示某些错误。如果不将此选项添加到此类事件，则会导致用户执行动作组以获取错误消息，并同时激活一次性事件，这意味着玩家将无法再使用此事件。而真正要触发的事件实际上并未真正执行，因此此选项可帮助您解决此问题。

## Custom Event Data(自定义事件数据)

ConditionalEvents可以让你检查任何你想要的事件，甚至是其他插件的。具体详见[此页](zi-ding-yi-shi-jian.md)

```
custom_event_data:
  event: dt.ajneb97.api.TurretPlaceEvent
  player_variable: getPlayer()
  variables_to_capture:
  - '%turret_world%;getLocation().getWorld().getName()'
```
