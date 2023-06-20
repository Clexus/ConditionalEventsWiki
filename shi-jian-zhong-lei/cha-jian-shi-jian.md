# 插件事件

## CITIZENS RIGHT CLICK NPC

{% hint style="warning" %}
需要Citizens: [https://www.spigotmc.org/resources/citizens.13811/](https://www.spigotmc.org/resources/citizens.13811/)
{% endhint %}

玩家与Citizens的NPC交互时触发.

```yaml
example:
  type: citizens_right_click_npc
  conditions:
  - '%npc_id% == 50'
  actions:
    default:
    - "player_command: rtp"
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%npc\_id%</mark> (NPC的ID)
* <mark style="color:green;">%npc\_name%</mark> (NPC的名字)
{% endhint %}

## WGEVENTS REGION ENTER

{% hint style="warning" %}
需要WorldGuard Events: [https://www.spigotmc.org/resources/worldguard-events.65176/](https://www.spigotmc.org/resources/worldguard-events.65176/)
{% endhint %}

当玩家进入WorldGuard区域的时候触发.

```yaml
example:
  type: wgevents_region_enter
  conditions:
  - '%region% == main_city'
  actions:
    default:
    - "title: 20;40;20;&6&lENTERING AREA;&7City of Kryngel"
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%region%</mark> (进入的区域名)
{% endhint %}

## WGEVENTS REGION LEAVE

{% hint style="warning" %}
需要WorldGuard Events: [https://www.spigotmc.org/resources/worldguard-events.65176/](https://www.spigotmc.org/resources/worldguard-events.65176/)
{% endhint %}

玩家离开WorldGuard区域时触发.

```yaml
example:
  type: wgevents_region_leave
  conditions:
  - '%region% == main_city'
  actions:
    default:
    - "title: 20;40;20;&6&lLEAVING AREA;&7City of Kryngel"
```

{% hint style="success" %}
**变量:**

* <mark style="color:green;">%region%</mark> (离开的区域名)
{% endhint %}

## PROTOCOLLIB RECEIVE MESSAGE

{% hint style="warning" %}
需要ProtocolLib: [https://www.spigotmc.org/resources/protocollib.1997/](https://www.spigotmc.org/resources/protocollib.1997/)
{% endhint %}

玩家收到聊天消息时触发.

```yaml
example:
  type: protocollib_receive_message
  conditions:
  - "%normal_message% contains &cWelcome to the server."
  actions:
    default:
    - "cancel_event: true"
```

{% hint style="success" %}
**Variables:**

* <mark style="color:green;">%normal\_message%</mark> (包含颜色的聊天消息)
* <mark style="color:green;">%json\_message%</mark> (收到消息的完整JSON格式)
{% endhint %}
