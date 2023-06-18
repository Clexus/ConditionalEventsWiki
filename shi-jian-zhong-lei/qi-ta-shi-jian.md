# 其他事件

## ENTITY INTERACT

Event called when a player right clicks an entity.

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
**Variables:**

* ConditionalEvents <mark style="color:green;">entity variables</mark> (for clicked entity)
* ConditionalEvents <mark style="color:green;">item variables</mark> (for item in hand)
{% endhint %}

{% hint style="info" %}
On this event you can use target player variables and to\_target actions.
{% endhint %}

## ENTITY SPAWN

Event called when an entity (animal or monster) is going to spawn.

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
**Variables:**

* <mark style="color:green;">%reason%</mark> (The reason of the event, why is the entity going to spawn. All reasons here: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/CreatureSpawnEvent.SpawnReason.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/CreatureSpawnEvent.SpawnReason.html))
* ConditionalEvents <mark style="color:green;">entity variables</mark> (for entity about to spawn)
{% endhint %}

{% hint style="warning" %}
This is not a player event, which means you can't use player variables or player action.
{% endhint %}

## CONSOLE COMMAND

Event called when the console executes a command.

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
**Variables:**

* <mark style="color:green;">%command%</mark> (The full command the console used)
* <mark style="color:green;">%main\_command%</mark> (The main command without arguments)
* <mark style="color:green;">%arg\_X%</mark> (The argument in the X position of the command. If the command is **`announce hello world`** the %arg\_1% variable would be "hello" and the %arg\_2% would be "world")
* <mark style="color:green;">%args\_length%</mark> (The amount of arguments of the command)
* <mark style="color:green;">%args\_substring\_\<arg1>-\<arg2>%</mark> (This variable will create a text using a first argument and a last argument. For example, if the command is **`announce I am currently doing a Youtube livestreaming`**, you could use the %args\_substring\_1-6% variable to take arg1, arg2,...,arg6 and get the text that the player is announcing. If you don't care about the arguments length, instead of 6 use a large number like 100)
{% endhint %}

{% hint style="warning" %}
This is not a player event, which means you can't use player variables or player action.
{% endhint %}

## REPETITIVE

The repetitive event works by checking for conditions **for each player** periodically. The time is defined in the `repetitive_time` option. This option defines the period of time in TICKS (20 ticks = 1 second) when checking the conditions.

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
This event has no variables, but you can still use ConditionalEvents variables or PlaceholderAPI variables.
{% endhint %}

## REPETITIVE SERVER

The repetitive server event works by checking for conditions **of the server** periodically (like local time, but no player variables). The time is defined in the `repetitive_time` option. This option defines the period of time in TICKS (20 ticks = 1 second) when checking the conditions.

```yaml
example:
  type: repetitive_server
  repetitive_time: 1200
  actions:
    default:
    - 'to_all: message: &7There are &a%server_online% &7players on the server.'
```

{% hint style="info" %}
This event has no variables, but you can still use ConditionalEvents variables or PlaceholderAPI variables.
{% endhint %}

{% hint style="warning" %}
This is not a player event, which means you can't use player variables or player action.
{% endhint %}

## CALL

The call event is a special event that will be executed ONLY from the actions of another event (using the call\_event action).

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

This means you can now check for conditions after actions execution, using a complementary call event. You can also pass variables from an event to another to make it more specific.

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
This event has no variables, but you can still use ConditionalEvents variables or PlaceholderAPI variables. Remember that a call event can be executed passing some variables from another event.
{% endhint %}

{% hint style="info" %}
This event will be a player event if the original event which was called from is a player event.
{% endhint %}

## CUSTOM

Any custom event that you want. You can use events from other plugins, more info on the [**Custom Events**](broken-reference) page.
