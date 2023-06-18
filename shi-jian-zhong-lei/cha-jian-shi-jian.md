# 插件事件

## CITIZENS RIGHT CLICK NPC

{% hint style="warning" %}
Requires Citizens: [https://www.spigotmc.org/resources/citizens.13811/](https://www.spigotmc.org/resources/citizens.13811/)
{% endhint %}

Event called when a player right clicks on a Citizens NPC.

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
**Variables:**

* <mark style="color:green;">%npc\_id%</mark> (ID of the clicked NPC)
* <mark style="color:green;">%npc\_name%</mark> (Name of the clicked NPC)
{% endhint %}

## WGEVENTS REGION ENTER

{% hint style="warning" %}
Requires WorldGuard Events: [https://www.spigotmc.org/resources/worldguard-events.65176/](https://www.spigotmc.org/resources/worldguard-events.65176/)
{% endhint %}

Event called when a player enters a WorldGuard region.

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
**Variables:**

* <mark style="color:green;">%region%</mark> (Entered region)
{% endhint %}

## WGEVENTS REGION LEAVE

{% hint style="warning" %}
Requires WorldGuard Events: [https://www.spigotmc.org/resources/worldguard-events.65176/](https://www.spigotmc.org/resources/worldguard-events.65176/)
{% endhint %}

Event called when a player leaves a WorldGuard region.

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
**Variables:**

* <mark style="color:green;">%region%</mark> (Leaved region)
{% endhint %}

## PROTOCOLLIB RECEIVE MESSAGE

{% hint style="warning" %}
Requires ProtocolLib: [https://www.spigotmc.org/resources/protocollib.1997/](https://www.spigotmc.org/resources/protocollib.1997/)
{% endhint %}

Event called when a player receives a chat message.

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

* <mark style="color:green;">%normal\_message%</mark> (Message received including color codes)
* <mark style="color:green;">%json\_message%</mark> (Complete JSON format of the message received)
{% endhint %}
