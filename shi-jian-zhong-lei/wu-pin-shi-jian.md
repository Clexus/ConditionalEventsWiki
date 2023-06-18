# 物品事件

## ITEM INTERACT

Event called when a player clicks on an item.

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
**Variables:**

* <mark style="color:green;">%action\_type%</mark> (Could be: RIGHT\_CLICK, LEFT\_CLICK, SHIFT\_RIGHT\_CLICK, SHIFT\_LEFT\_CLICK or PHYSICAL. Use PHYSICAL when you want to check players on pressure plates)
* ConditionalEvents <mark style="color:green;">item variables</mark>
{% endhint %}

## ITEM CONSUME

Event called when a player consumes an item (eat food for example)

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
**Variables:**

* ConditionalEvents <mark style="color:green;">item variables</mark>
{% endhint %}

## ITEM PICKUP

Event called when a player pickups an item.

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
**Variables:**

* ConditionalEvents <mark style="color:green;">item variables</mark>
{% endhint %}

## ITEM MOVE

Event called when a player tries to move an item from its inventory.

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
**Variables:**

* <mark style="color:green;">%inventory\_type%</mark> (Type of the open inventory. All types on this link: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/inventory/InventoryType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/inventory/InventoryType.html))
* <mark style="color:green;">%slot%</mark> (Selected slot)
* ConditionalEvents <mark style="color:green;">item variables</mark>
{% endhint %}

## ITEM CRAFT

Event called when a player is about to craft an item.

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
**Variables:**

* ConditionalEvents <mark style="color:green;">item variables</mark>
{% endhint %}

## ITEM DROP

Event called when a player drops an item.

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
**Variables:**

* ConditionalEvents <mark style="color:green;">item variables</mark>
{% endhint %}

## ITEM SELECT

Event called when a player selects/deselects an item in their hotbar.

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
**Variables:**

* <mark style="color:green;">%select\_type%</mark> (Could be: SELECT or DESELECT)
* ConditionalEvents <mark style="color:green;">item variables</mark>
{% endhint %}

## ITEM ENCHANT

Event called when a player enchants an item.

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
**Variables:**

* <mark style="color:green;">%enchantment\_list%</mark> (List of enchantments to be applied to the item. It will return a string with the following format: `<enchantment1>:<level1>;<enchantment2>:<level2>;...`)
* ConditionalEvents <mark style="color:green;">item variables</mark>
{% endhint %}

## ITEM REPAIR

Event called when a player repairs an item.

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
V**ariables:**

* <mark style="color:green;">%rename\_text%</mark> (New name of the item if the player is renaming it)
* ConditionalEvents <mark style="color:green;">item variables</mark>
{% endhint %}

{% hint style="warning" %}
Only works on 1.13+!
{% endhint %}
