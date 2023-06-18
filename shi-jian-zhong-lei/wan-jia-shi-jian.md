# 玩家事件

## PLAYER JOIN

Event called when a player joins the server.

```yaml
example:
  type: player_join
  actions:
    default:
    - 'message: &eWelcome %player% to the server.'
```

{% hint style="info" %}
This event has no variables, but you can still use ConditionalEvents variables or PlaceholderAPI variables.
{% endhint %}

## PLAYER LEAVE

Event called when a player leaves the server.

```yaml
example:
  type: player_leave
  actions:
    default:
    - 'to_all: message: &e%player% left the server.'
```

{% hint style="info" %}
This event has no variables, but you can still use ConditionalEvents variables or PlaceholderAPI variables.
{% endhint %}

## PLAYER PRE JOIN

Event called when a player tries to join the server.

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
**Variables:**

* <mark style="color:green;">%name%</mark> (Name of the player trying to join the server)
* <mark style="color:green;">%ip%</mark> (IP of the player)
* <mark style="color:green;">%uuid%</mark> (UUID of the player)
{% endhint %}

{% hint style="warning" %}
This is not a player event, which means you can't use player variables or player actions. Don't be confused, it is called a "player pre join", but it is a special event which doesn't contain player data.
{% endhint %}

{% hint style="warning" %}
You can't use `cancel_event` action on this event. If you want to block the player from joining, use the `prevent_join` action instead.
{% endhint %}

## PLAYER RESPAWN

Event called when a player respawns.

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
This event has no variables, but you can still use ConditionalEvents variables or PlaceholderAPI variables.
{% endhint %}

## PLAYER DEATH

Event called when a player dies.

```yaml
example:
  type: player_death
  actions:
    default:
    - 'message: &7You died because of: &c%cause%'
```

{% hint style="success" %}
**Variables:**

* <mark style="color:green;">%cause%</mark> (Cause of death. All causes here: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityDamageEvent.DamageCause.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityDamageEvent.DamageCause.html))
* <mark style="color:green;">%killer\_type%</mark> (If the player dies because of an entity, which type of entity. All types on this link: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html))
* <mark style="color:green;">%killer\_name%</mark> (If the player dies because of an entity, the name of this entity without color codes)
* <mark style="color:green;">%killer\_color\_format\_name%</mark> (The name of the killer including color codes)
{% endhint %}

## PLAYER COMMAND

Event called when a player executes a command.

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
**Variables:**

* <mark style="color:green;">%command%</mark> (The full command the player used)
* <mark style="color:green;">%main\_command%</mark> (The main command without arguments)
* <mark style="color:green;">%arg\_X%</mark> (The argument in the X position of the command. If the command is **`/announce hello world`** the %arg\_1% variable would be "hello" and the %arg\_2% would be "world")
* <mark style="color:green;">%args\_length%</mark> (The amount of arguments of the command)
* <mark style="color:green;">%args\_substring\_\<arg1>-\<arg2>%</mark> (This variable will create a text using a first argument and a last argument. For example, if the command is **`/announce I am currently doing a Youtube livestreaming`**, you could use the %args\_substring\_1-6% variable to take arg1, arg2,...,arg6 and get the text that the player is announcing. If you don't care about the arguments length, instead of 6 use a large number like 100)
{% endhint %}

## PLAYER CHAT

Event called when a player writes something in chat.

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
**Variables:**

* <mark style="color:green;">%message%</mark> (The chat message)
{% endhint %}

## PLAYER LEVELUP

&#x20;Event called when a player changes its level.

```yaml
example:
  type: player_levelup
  actions:
    default:
    - 'message: &aLevel &6&l%old_level% &7-> &6%new_level%'
```

{% hint style="success" %}
**Variables:**

* <mark style="color:green;">%old\_level%</mark> (The previous level of the player)
* <mark style="color:green;">%new\_level%</mark> (The new level of the player)
{% endhint %}

## PLAYER WORLD CHANGE

Event called when a player is moving to another world.

```yaml
example:
  type: player_world_change
  actions:
    default:
    - 'message: &7Moving to &e%world_to% &7world'
```

{% hint style="success" %}
**Variables:**

* <mark style="color:green;">%world\_from%</mark> (The previous world)
* <mark style="color:green;">%world\_to%</mark> (The world where the player is moving to)
* <mark style="color:green;">%online\_players\_from%</mark> (Amount of online players in the previous world)
* <mark style="color:green;">%online\_players\_to%</mark> (Amount of online players in the world where the player is moving to)
{% endhint %}

## PLAYER ATTACK

Event called when a player damages an entity.

```yaml
example:
  type: player_attack
  conditions:
  - '%victim% == PLAYER'
  - '%item% == DIAMOND_SWORD'
  - '%item_name% == Super Sword'
  - '%random_1-10% >= 8'
  actions:
    default:
    - 'message: &aYour diamond sword poison effect was activated! &6%target:player_name% &ais now poisoned!'
    - 'to_target: give_potion_effect: POISON;120;1'
    - 'to_target: message: &cYou were poisoned by &e%player%&c!'
```

{% hint style="success" %}
**Variables:**

* <mark style="color:green;">%damage%</mark> (Damage made by the player)
* <mark style="color:green;">%attack\_type%</mark> (Type of the damage. For projectiles it could be: ARROW, TRIDENT, SNOWBALL. If the damage is not made by a projectile, it will result in PLAYER)
* ConditionalEvents <mark style="color:green;">item variables</mark> (for item in hand)
* ConditionalEvents <mark style="color:green;">victim variables</mark>
{% endhint %}

{% hint style="info" %}
On this event you can use target player variables and to\_target actions.
{% endhint %}

## PLAYER KILL

Event called when a player kills an entity.

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
**Variables:**

* ConditionalEvents <mark style="color:green;">item variables</mark> (for item in hand)
* ConditionalEvents <mark style="color:green;">victim variables</mark>
{% endhint %}

{% hint style="info" %}
On this event you can use target player variables and to\_target actions.
{% endhint %}

## PLAYER DAMAGE

Event called when a player is taking damage.

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
**Variables:**

* <mark style="color:green;">%cause%</mark> (Cause of the event. How did the player got damaged. All causes here: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityDamageEvent.DamageCause.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityDamageEvent.DamageCause.html))
* <mark style="color:green;">%damage%</mark> (Damage taken by the player)
* <mark style="color:green;">%damager\_type%</mark> (If the player takes damage from an entity, which type of entity. All types on this link: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html))
* <mark style="color:green;">%damager\_name%</mark> (If the player takes damage from an entity, the name of this entity without color codes)
* <mark style="color:green;">%damager\_color\_format\_name%</mark> (The name of the damager including color codes)
{% endhint %}

## PLAYER ARMOR

Event called when a player equips or unequips armor.

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
**Variables:**

* <mark style="color:green;">%armor\_type%</mark> (Type of the armor. Could be: HELMET, CHESTPLATE, LEGGINGS or BOOTS)
* <mark style="color:green;">%equip\_type%</mark> (Could be: EQUIP or UNEQUIP)
* ConditionalEvents <mark style="color:green;">item variables</mark>
{% endhint %}

## PLAYER TELEPORT

Event called when a player teleports somehow.

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
**Variables:**

* <mark style="color:green;">%cause%</mark> (Cause of the event. Why is the player teleporting. All causes here: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/player/PlayerTeleportEvent.TeleportCause.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/player/PlayerTeleportEvent.TeleportCause.html))
* <mark style="color:green;">%from\_x%</mark> (Coordinate X of the previous location)
* <mark style="color:green;">%from\_y%</mark> (Coordinate Y of the previous location)
* <mark style="color:green;">%from\_z%</mark> (Coordinate Z of the previous location)
* <mark style="color:green;">%from\_world%</mark> (World of the previous location)
* <mark style="color:green;">%to\_x%</mark> (Coordinate Z of the new location)
* <mark style="color:green;">%to\_y%</mark> (Coordinate Y of the new location)
* <mark style="color:green;">%to\_x%</mark> (Coordinate X of the new location)
* <mark style="color:green;">%to\_world%</mark> (World of the new location)
{% endhint %}

## PLAYER BED ENTER

Event called when a player enters a bed.

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
**Variables:**

* <mark style="color:green;">%result%</mark> (Result of the event. Can the player really use the bed? All results here: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/player/PlayerBedEnterEvent.BedEnterResult.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/player/PlayerBedEnterEvent.BedEnterResult.html))
{% endhint %}

{% hint style="warning" %}
Only works on 1.13+!
{% endhint %}

## PLAYER SWAP HAND

Event called when a player swap items between main hand and off hand using the hotkey.

```yaml
example:
  type: player_swap_hand
  actions:
    default:
    - "cancel_event: true"
```

{% hint style="success" %}
**Variables:**

* ConditionalEvents <mark style="color:green;">item variables</mark> (for item in main hand)
{% endhint %}

## PLAYER FISH

Event called when a player is fishing.

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
**Variables:**

* <mark style="color:green;">%state%</mark> (Current state of fishing. All states here: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/player/PlayerFishEvent.State.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/player/PlayerFishEvent.State.html))
* <mark style="color:green;">%caught\_type%</mark> (Entity caught. All entity types here: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html))
* ConditionalEvents <mark style="color:green;">item variables</mark> (for caught item if present)
{% endhint %}

## PLAYER OPEN INVENTORY

Event called when a player opens an inventory.

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
**Variables:**

* <mark style="color:green;">%inventory\_type%</mark> (Type of the opened inventory. All types here: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/inventory/InventoryType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/inventory/InventoryType.html))
* <mark style="color:green;">%inventory\_title%</mark> (Title of the opened inventory without color codes)
{% endhint %}

## PLAYER STATISTIC

Event called when a player statistic is incremented, like certain blocks breaked, jumps, items pickup...

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
**Variables:**

* <mark style="color:green;">%statistic\_name%</mark> (Name of the incremented statistic. All names here: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Statistic.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Statistic.html))
* <mark style="color:green;">%new\_value%</mark> (New value of this statistic)
* <mark style="color:green;">%previous\_value%</mark> (Previous value of this statistic)
* <mark style="color:green;">%entity%</mark> (Associated entity type for this statistic, if present. All types here: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html))
* <mark style="color:green;">%block%</mark> (Associated block type for this statistic, if present. All types here: [https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html))
{% endhint %}



## PLAYER SNEAK

Event called when a player toggles their sneaking state.

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
**Variables:**

* <mark style="color:green;">%is\_sneaking%</mark> (Whether the player is sneaking or not. Will return "true" or "false")
{% endhint %}
