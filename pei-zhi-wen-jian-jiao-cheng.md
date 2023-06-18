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
- '%random_1-10% >= 8'
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

## Allow Math formulas in Conditions(允许条件中使用数学方程)

如果你想在条件中
