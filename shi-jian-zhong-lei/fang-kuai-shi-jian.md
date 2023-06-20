# 方块事件

## BLOCK INTERACT

玩家与方块交互时触发.

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
**变量:**

*   <mark style="color:green;">%action\_type%</mark> (RIGHT\_CLICK, LEFT\_CLICK, SHIFT\_RIGHT\_CLICK, SHIFT\_LEFT\_CLICK

    &#x20;或 PHYSICAL. PHYSICAL 用于玩家触发压力板)
* ConditionalEvents [<mark style="color:green;">方块变量</mark>](../bian-liang.md#fang-kuai-bian-liang)
* ConditionalEvents [<mark style="color:green;">物品变量</mark>](../bian-liang.md#wu-pin-bian-liang) (用于手上物品)
{% endhint %}

## BLOCK BREAK

玩家破坏方块时触发.

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
**变量:**

* ConditionalEvents [<mark style="color:green;">方块变量</mark>](../bian-liang.md#fang-kuai-bian-liang)
* ConditionalEvents [<mark style="color:green;">物品变量</mark>](../bian-liang.md#wu-pin-bian-liang) (用于手上物品)
{% endhint %}

## BLOCK PLACE

玩家放置方块时触发

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
**变量:**

* ConditionalEvents [<mark style="color:green;">方块变量</mark>](../bian-liang.md#fang-kuai-bian-liang)
* ConditionalEvents [<mark style="color:green;">物品变量</mark>](../bian-liang.md#wu-pin-bian-liang) (用于手上物品)
{% endhint %}
