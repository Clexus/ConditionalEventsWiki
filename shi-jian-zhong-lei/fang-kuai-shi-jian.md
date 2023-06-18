# 方块事件

## BLOCK INTERACT

Event called when a player clicks on a block.

```yaml
example:
  type: block_interact
  conditions:
  - '%block_x% == 20'
  - '%block_y% == 60'
  - '%block_z% == 20'
  - '%block_world% == lobby'
  - '%block% == STONE_BUTTON'
  - '%action_type% == RIGHT_CLICK'
  actions:
    default:
    - "message: &aYou''ve received $500!"
    - "console_command: eco give %player% 500"
```

{% hint style="success" %}
**Variables:**

*   <mark style="color:green;">%action\_type%</mark> (RIGHT\_CLICK, LEFT\_CLICK, SHIFT\_RIGHT\_CLICK, SHIFT\_LEFT\_CLICK

    &#x20;or PHYSICAL. Use PHYSICAL when you want to check players on pressure plates)
* ConditionalEvents <mark style="color:green;">block variables</mark>
* ConditionalEvents <mark style="color:green;">item variables</mark> (for item in hand)
{% endhint %}

## BLOCK BREAK

Event called when a player breaks a block.

```yaml
example:
  type: block_break
  conditions:
  - '%block_head_texture% != %empty%'
  actions:
    default:
    - 'cancel_event: true'
    - "message: &cYou can''t break heads with texture!"
    - 'playsound: BLOCK_NOTE_BLOCK_PLING;10;0.1'
```

{% hint style="success" %}
**Variables:**

* ConditionalEvents <mark style="color:green;">block variables</mark>
* ConditionalEvents <mark style="color:green;">item variables</mark> (for item in hand)
{% endhint %}

## BLOCK PLACE

Event called when a player places a block.

```yaml
example:
  type: block_place
  conditions:
  - '%block_world% == spawn'
  actions:
    default:
    - 'cancel_event: true'
    - "message: &cYou can''t place blocks on this world."
    - 'playsound: BLOCK_NOTE_BLOCK_PLING;10;0.1'
```

{% hint style="success" %}
**Variables:**

* ConditionalEvents <mark style="color:green;">block variables</mark>
* ConditionalEvents <mark style="color:green;">item variables</mark> (for item in hand)
{% endhint %}
