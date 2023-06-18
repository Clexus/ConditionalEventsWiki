# 特定事件专属动作

以下动作只在一些特定事件中才能使用

### KEEP ITEMS(保留物品)

在player\_death事件中才能使用\
保存玩家的经验，物品等，可用值：`items`, `xp`, `all`

```
keep_items: items
keep_items: all
```

### CANCEL DROP(取消掉落)

只有在block\_break事件中才有用。它将会取消方块的经验和物品掉落，只在**1.13+**工作

```
cancel_drop: true
```

### SET DAMAGE（设置伤害）

只在player\_attack中才能使用。可以调整攻击的伤害

```
//设置固定伤害
set_damage: 15

//设置百分比伤害,如下方150%就造成1.5倍伤害,25%则是0.25倍伤害
set_damage: 150%
set_damage: 25%
```

## HIDE JOIN MESSAGE(隐藏进入消息)

只在player\_join事件才可使用。可以隐藏进入消息

```
hide_join_message: true
```

## HIDE LEAVE MESSAGE(隐藏退出消息)

只在player\_leave事件中才有用。能够隐藏退出消息

```
hide_leave_message: true
```

### SET DEATH MESSAGE(设置死亡消息)

只在player\_death事件中才可使用，能够设置玩家的死亡消息，你可以设置为"no"来隐藏死亡消息

```
set_death_message: &fAn angry cactus killed &e%player%&f.
set_death_message: no
```

### PREVENT JOIN(防止进入)

只在player\_pre\_join事件中才能用。组织玩家进入服务器，同时发送消息

```
prevent_join: &c&lERROR!\n&7You can't access this account with that IP.
```
