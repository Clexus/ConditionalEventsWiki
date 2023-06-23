---
description: >-
  在这里你将学会如何使用此插件：https://www.spigotmc.org/resources/82271/                                   
  来自PCD小组
---

# ConditionalEvents Wiki

## 描述

此插件让你能够为某个事件添加不同的需求条件。如果条件通过，自定义动作将会被执行。你能用此插件实现的可能性是无限的。为了让你能够更简单地了解这个插件，下面是几个例子：

{% tabs %}
{% tab title="例子1" %}
如果一个玩家在某个坐标按下了一个按钮(或者任何方块), 你就可以为此玩家执行某些动作，比如执行指令，给他发一条消息，应用一些药水效果等等。

```
example1:
    type: block_interact
    conditions:
    - '%block_x% == 20'
    - '%block_y% == 60'
    - '%block_z% == 20'
    - '%block_world% equals lobby'
    - '%block% equals STONE_BUTTON'
    - '%action_type% equals RIGHT_CLICK'
    actions:
      default:
      - 'message: &a你获得了 $500!'
      - 'console_command: eco give %player% 500'
      - 'playsound: ENTITY_PLAYER_LEVELUP;10;2'
```
{% endtab %}

{% tab title="例子2" %}
当一个玩家用某个物品攻击了另一个玩家，被打的玩家会有几率受到中毒效果。

```
example2:
    type: player_attack
    conditions:
    - '%victim% equals PLAYER'
    - '%item% equals DIAMOND_SWORD'
    - '%item_name% equals VIP Sword'
    - '%random_1-10% >= 8'
    actions:
      default:
      - 'message: &a你的淬毒钻石剑效果已激活!'
      - 'to_target: give_potion_effect: POISON;120;1'
      - 'to_target: message: &c你被&e%player%&c注入了毒液!'
```
{% endtab %}

{% tab title="例子3" %}
你可以用ConditionalEvents阻止命令执行，然后踢出玩家或者播放声音

```
example3:
    type: player_command
    conditions:
    - '%command% startsWith //calc or %command% startsWith //solve or %command% startsWith
      //eval'
    actions:
      default:
      - 'cancel_event: true'
      - 'kick: &c你想干什么?'
    ignore_with_permission: conditionalevents.ignore.example3
```
{% endtab %}

{% tab title="例子4" %}
你可以取消某个世界挖/放方块的事件.

```
example4:
    type: block_break;block_place
    conditions:
    - '%block_world% equals spawn'
    actions:
      default:
      - 'cancel_event: true'
      - 'message: &c你不能在此世界破坏或放置方块.'
      - 'playsound: BLOCK_NOTE_BLOCK_PLING;10;0.1'
    ignore_with_permission: conditionalevents.ignore.event4
```
{% endtab %}

{% tab title="例子5" %}
你可以根据玩家所在的世界把他们传送到不同地方.

```
example5:
    type: player_respawn
    conditions:
    - '%player_world% equals pvp1 or %player_world% equals pvp2'
    actions:
      default:
      - 'teleport: lobby;0;60;0;90;0'
      - 'message: &c你已死亡，已将你传送到PVP大厅...'
```
{% endtab %}

{% tab title="例子6" %}
你可以一直检测一个玩家是否进入一个区域并为他执行动作.

```
example6:
    type: repetitive
    repetitive_time: 10
    conditions:
    - '%player_world% equals spawn'
    - '%worldguard_region_name% equals survival_entrance'
    actions:
      default:
      - 'console_command: warp %player% Survival'
```
{% endtab %}

{% tab title="例子7" %}
你可以根据玩家VIP等级给予玩家不同的钱.

```
example7:
    type: player_kill
    conditions:
    - '%victim% equals PLAYER'
    - '%target:vault_rank% equals vip execute actions1'
    - '%target:vault_rank% equals admin execute actions2'
    actions:
      default:
      - "message: &6你杀死了 &e%target:player%"
      - "message: &7你获得了: &a$100"
      - "console_command: eco give %player% 100"
      actions1:
      - "message: &6你杀死了 &e%target:player%"
      - "message: &7因为他是VIP玩家，你获得了: &a$500"
      - "console_command: eco give %player% 500"
      actions2:
      - "message: &6你杀死了 &e%target:player%"
      - "message: &7因为他是管理员，你获得了: &a$1000"
      - "console_command: eco give %player% 1000"
```
{% endtab %}

{% tab title="例子8" %}
用命令来检测别的玩家的等级

```
example8:
    type: player_command
    conditions:
    - "%main_command% == /checklevel"
    - "%args_length% < 1 execute error1"
    - "%parseother_{arg_1}_{player_online}% == no execute error2"
    actions:
      default:
      - "cancel_event: true"
      - "message: &e%arg_1% &a的等级为: &e%otherplayer_level_{arg_1}%"
      error1:
      - "cancel_event: true"
      - "message: &c请按照以下格式使用 &7/checklevel <player>"
      error2:
      - "cancel_event: true"
      - "message: &c此玩家不在线."
```
{% endtab %}
{% endtabs %}

## 图像

![阻止命令](https://2337802743-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-MIjuzV9CA6Qb\_sn8uPn%2F-MIk-wr4y\_SXqUZjWB56%2F-MIk1BXxwMju3prxlJvM%2F05b7038f1503dc4db38642e06d0df7a417f51950.gif?alt=media\&token=5354f3bd-d840-437a-9538-281a6ec1cb57)

![检查位置](https://2337802743-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-MIjuzV9CA6Qb\_sn8uPn%2F-MIk-wr4y\_SXqUZjWB56%2F-MIk1F3eJhzswa4oS\_aH%2F93cd2d59655f99924770d7a206753365e54d8588.gif?alt=media\&token=9e0e2086-19cb-4776-8c63-e3922bf4c866)

![击杀实体消息](https://2337802743-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-MIjuzV9CA6Qb\_sn8uPn%2F-MIk-wr4y\_SXqUZjWB56%2F-MIk10gIVXZPw9s55V-o%2Fef3861ffa5944c6876758b7ba11af81d62ab1336.gif?alt=media\&token=bfed0607-7a24-4d1c-9720-c4b5bc709f7b)
