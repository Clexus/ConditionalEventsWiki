# 自定义事件

ConditionalEvents可以让你检查任何你想要的事件，甚至是其他插件的。在下方你可以找到更多信息。

{% hint style="warning" %}
本节主要面向具有Java知识并知道如何创建Minecraft插件的基础知识的人。如果你不明白这一点，请随时通过私人消息（在Spigot上）或在插件讨论中与作者联系。
{% endhint %}

下面是一个自定义事件的示例，当玩家放置作者的插件[DefensiveTurrets](https://www.spigotmc.org/resources/defensiveturrets-defend-yourself-using-turrets-1-8-1-16.67188/)的炮塔时，该事件将被激活。请记住，你可以添加任意数量的自定义事件，只需使用新名称添加一个新部分。要检测的插件必须有一个API才能使用自定义事件。

```
example1:
    type: custom
    custom_event_data:
      event: dt.ajneb97.api.TurretPlaceEvent
      player_variable: getPlayer()
      variables_to_capture:
     - '%turret_world%;getLocation().getWorld().getName()'
    conditions:
    - '%turret_world% equals spawn'
    actions:
      default:
      - 'cancel_event: true'
      - 'message: &cYou can''t place turrets on this world.'
      - 'playsound: %player%;NOTE_PLING;10;0.1'
```

正如你所见，上方出现了一个叫做 `custom_event_data` 的新选项，它只在自定义事件中才被使用。

| 选项                                                                                                         | 描述                                                                                                                                                                                                                                                                                                                                                                                                    |
| ---------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **event:** "dt.ajneb97.api.TurretPlaceEvent"                                                               | 此选项定义了此事件的类。如果你想要检测spigot/bukkit的事件，你可以从[https://hub.spigotmc.org/javadocs/spigot/allclasses-index.html](https://hub.spigotmc.org/javadocs/spigot/allclasses-index.html)获取所需的值。只需前往链接，搜索事件并点击，在第一行你会看见此类的"包名"，比如[org.bukkit.event.player.PlayerLevelChangeEvent](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/event/player/PlayerLevelChangeEvent.html)。 另一方面，如果你想要检测一个插件的事件，你需要它的API和那个事件的包名。 |
| **player\_variable:** "getPlayer()"                                                                        | <p>这是会返回玩家变量的方法。玩家变量包括了一切关于执行此事件用户的信息。对于spigot/bukkit事件来说它总是为getPlayer() [其实不然，有些可能是getEntity()]</p><p></p><p><strong>注意</strong>：你可以创建一些非玩家的事件，而它们没有getPlayer()方法，如果是这种情况，那么请把player_variable选项删掉</p>                                                                                                                                                                                                |
| <p><strong>variables_to_capture:</strong></p><p> - '%turret_world%;getLocation().getWorld().getName()'</p> | 在这里你需要定义要获取和储存的变量。每一个变量都会通过执行一个方法来得到。这个方法会由这个插件的API或者bukkit/spigot的类提供。举个例子，在我用过的`PlayerLevelChangeEvent`链接里，你可以看见getNewLevel() 和 getOldLevel()方法，在事件被执行时，它们分别会返回玩家现在的等级和之前的等级。                                                                                                                                                                                                                       |
