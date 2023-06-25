# 物品事件

## ITEM INTERACT

玩家与物品交互时触发.

```yaml
example:
  type: item_interact
  conditions:
  - '%item% == REDSTONE'
  actions:
    default:
    - 'cancel_event: true'
    - "message: &cYou can''t use redstone."
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%action\_type%</mark> (可为: RIGHT\_CLICK, LEFT\_CLICK, SHIFT\_RIGHT\_CLICK, SHIFT\_LEFT\_CLICK)
* ConditionalEvents [<mark style="color:green;">物品变量</mark>](../bian-liang.md#wu-pin-bian-liang)
{% endhint %}

## ITEM CONSUME

玩家消耗物品时触发(比如吃东西)

```yaml
example:
  type: item_consume
  conditions:
  - '%item% == GOLDEN_APPLE'
  - '%random_1-10% >= 8'
  actions:
    default:
    - "give_potion_effect: INCREASE_DAMAGE;120;1;false"
```

{% hint style="success" %}
**变量:**

* ConditionalEvents [<mark style="color:green;">物品变量</mark>](../bian-liang.md#wu-pin-bian-liang)
{% endhint %}

## ITEM PICKUP

玩家捡起物品时触发.

```yaml
example:
  type: item_pickup
  conditions:
  - '%player_world% == minigames'
  actions:
    default:
    - "cancel_event: true"
```

{% hint style="success" %}
**变量:**

* ConditionalEvents [物品变量](../bian-liang.md#wu-pin-bian-liang)
{% endhint %}

## ITEM MOVE

玩家移动容器中的物品时触发.

```yaml
example:
  type: item_move
  conditions:
  - "%inventory_type% == ANVIL"
  actions:
    default:
    - "message: &cNope!"
    - "cancel_event: true"
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%inventory\_type%</mark> (开启容器的种类. 种类列表: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/inventory/InventoryType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/inventory/InventoryType.html))
* <mark style="color:green;">%slot%</mark> (选中的栏位)
* ConditionalEvents [<mark style="color:green;">物品变量</mark>](../bian-liang.md#wu-pin-bian-liang)
{% endhint %}

## ITEM CRAFT

玩家制作物品时触发.

```yaml
example:
  type: item_craft
  conditions:
  - "%item% == WRITABLE_BOOK"
  actions:
    default:
    - "message: &cYou can't craft writable books!"
    - "cancel_event: true"
```

{% hint style="success" %}
**变量:**

* ConditionalEvents [<mark style="color:green;">物品变量</mark>](../bian-liang.md#wu-pin-bian-liang)
{% endhint %}

## ITEM DROP

玩家掉落物品时触发

```yaml
example:
  type: item_drop
  conditions:
  - '%player_world% == minigames'
  actions:
    default:
    - "cancel_event: true"
```

{% hint style="success" %}
**变量:**

* ConditionalEvents [<mark style="color:green;">物品变量</mark>](../bian-liang.md#wu-pin-bian-liang)
{% endhint %}

## ITEM SELECT

玩家选中/取消选中快捷栏里的物品时触发.

```yaml
example:
  type: item_select
  conditions:
  - '%item% == DIAMOND_SWORD'
  - '%item_name% == Super Diamond Sword'
  - '%select_type% == SELECT'
  actions:
    default:
    - "actionbar: &6Equipping your Super Diamond Sword;60"
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%select\_type%</mark> (可为: SELECT 或 DESELECT)
* ConditionalEvents [<mark style="color:green;">物品变量</mark>](../bian-liang.md#wu-pin-bian-liang)
{% endhint %}

## ITEM ENCHANT

玩家附魔时触发.

```yaml
example:
  type: item_enchant
  conditions:
  - "%item% contains _SWORD"
  - "%enchantment_list% contains DURABILITY"
  actions:
    default:
    - "cancel_event: true"
    - "message: &cYou can't enchant swords with durability!"
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%enchantment\_list%</mark> (物品的附魔列表. 会返回一个以下格式的列表: `<enchantment1>:<level1>;<enchantment2>:<level2>;...`)
* ConditionalEvents [<mark style="color:green;">物品变量</mark>](../bian-liang.md#wu-pin-bian-liang)
{% endhint %}

## ITEM REPAIR

玩家修复物品时触发.

```yaml
example:
  type: item_repair
  conditions:
  - "%item% == NETHERITE_SWORD"
  - "%rename_text% == Super Sword"
  actions:
    default:
    - "cancel_event: true"
    - "message: &cYou can't rename a netherite sword to that name!"
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%rename\_text%</mark> (玩家重命名物品之后的物品名)
* ConditionalEvents [<mark style="color:green;">物品变量</mark>](../bian-liang.md#wu-pin-bian-liang)
{% endhint %}

{% hint style="warning" %}
只能在1.13+使用!
{% endhint %}
