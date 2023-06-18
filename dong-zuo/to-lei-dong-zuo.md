# “To” 类动作

这些是特殊标签，允许你对特定用户组执行操作。需要在操作之前添加这些标签。

### TO ALL（对所有人）

这是一个需要被加在动作最前面的特殊标签。这将会使得此动作为全服玩家执行。请使用以下格式："to\_all: <动作>"

```
- 'to_all: message: &a%player% 升级啦！
```

### TO TARGET(对目标)

这是一个供 `player_attack` ,`player_kill` 和 `entity_interact` 事件使用的标签. 这将会为事件的目标执行动作，请使用以下格式："to\_target: <动作>"

```
- 'to_target: give_potion_effect: POISON;120;1'
- 'to_target: message: &c超级毒液攻击！爱来自&e%player%&c!'
```

### TO WORLD(对世界)

这是一个需要被加在动作最前面的特殊标签。这将会使得此动作为某个世界的玩家执行。请使用以下格式："to\_world: <世界名>: <动作>"

```
- 'to_world: spawn: message: &6这个消息发送给所有在spawn世界的人'
- 'to_world: %player_world%: message: &6你好世界!'
```

### TO CONDITION（对特定条件）

它将会为执行条件成功的所玩家执行动作。需要在配置文件先建立一个条件组，类似下方：

```
Config:
  to_condition_groups:
    group1:
    - "%player_world% == spawn"
    group2:
    - ...
    group3:
    - ...
```

{% hint style="info" %}
你可以像一般的条件格式一样创建多个to condtion条件组，除了"execute"选项不能用之外
{% endhint %}

下一步，在一个to\_condition动作中以`"to_condition: <group>: <action>"`的格式使用先前创建的条件组“group1”：

```yaml
to_condition: group1: message: &7This message will be received by anyone who accomplish the <group1> condition
```

#### 完整样例

```
Config:
  to_condition_groups:
    group1:
    - "%player_has_permission_conditionalevents.somepermission% == yes"
test:
    type: player_command
    conditions:
    - "%command% == /test"
    actions:
      default:
      - "cancel_event: true"
      - "to_condition: group1: message: &7Hello to people with permissions."
```

前面的事件添加了一个/test命令来向只有有`conditionalevents.somepermission`权限的玩家发送消息
