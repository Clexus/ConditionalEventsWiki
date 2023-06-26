# 条件

## 基本功能

此选项将为事件添加一些条件。如果玩家完成了条件，那么将执行默认操作。

**条件列表**的每一行都指向一个**必须**为真的条件。你可以使用所有类型的变量，可以是PAPI或ConditionalEvents的变量。一般使用之前在 [事件种类](shi-jian-zhong-lei/) 页面或[变量](bian-liang.md)页面中显示的变量。

{% hint style="info" %}
举个例子，在下方例子中PlayerAttack事件有三个条件。受害者必须为玩家，**并且**，必须是使用钻石剑攻击，**并且**，这个钻石剑的名字必须为"极霸剑"：
{% endhint %}

```
conditions:
- '%victim% == PLAYER'
- '%item% == DIAMOND_SWORD'
- '%item_name% == 极霸剑'
```

{% hint style="info" %}
你也可以用"or"检查事件，这意味着这一行条件中只需有一个被完成了整一行就会被通过。举个例子，在下方的Player Command事件中只有一行条件，它判断的是命令是否以//clac **或** //solve **或** //eval 开头:
{% endhint %}

```
conditions:
- '%command% startsWith //calc or %command% startsWith //solve or %command% startsWith //eval'
```

## 进阶功能

{% hint style="info" %}
你可以在一行中比较两个变量
{% endhint %}

```
conditions:
- '%item_name% !contains %player_name%'
```

{% hint style="info" %}
你甚至可以用数学公式计算变量并进行对比。只需记住这些公式必须放在比较标识符后。但是记住，要在事件中开启以下选项：

```
allow_math_formulas_in_conditions: true
```
{% endhint %}

```
conditions:
- '%command% equals /test-kills'
- '%statistic_player_kills% >= %statistic_deaths%*2'

conditions:
- '%player_x% == (%player_z%*3)-1000'
```

## 比较标识符的种类

| 用于比较数字       | 用于比较字符串           | 字符串类的描述       |
| ------------ | ----------------- | ------------- |
| ==(或equals)  | equals(或==)       | 等于            |
| !=(或!equals) | !equals(或!=)      | 不等于           |
| >=           | equalsIgnoreCase  | 忽略大小写后比较是否等于  |
| <=           | !equalsIgnoreCase | 忽略大小写后比较是否不等于 |
| >            | startsWith        | 是否以某字符串起头     |
| <            | !startsWith       | 是否不以某字符串起头    |
|              | contains          | 包含            |
|              | !contains         | 不包含           |

注意，用于比较字符串的比较标识符也可以用于比较数字

## 执行(execute)类选项

有时候你可能会需要根据不同的条件来执行不同的动作。举个例子：

```
example:
    type: player_join
    conditions:
    - '%vault_rank% equals admin execute actions1'
    - '%vault_rank% equals vip execute actions2'
    actions:
      default:
      - 'to_all: message: &a%player% &e加入了游戏.'
      actions1:
      - 'to_all: message: &4&l管理员 &c%player% &e加入了游戏.'
      actions2:
      - 'to_all: message: &b&lVIP &a%player% &e加入了游戏.'
```

此事件会在玩家进入服务器时进行检测。如果玩家的等级为admin，那么actions1的动作就会被执行。当玩家的等级为VIP时就会执行actions2的动作。最后，如果没有满足任何execute类条件，那么就会执行default的动作

{% hint style="warning" %}
带"execute"的条件中，"execute"需要被加在最后面。你可以创建尽你所需的数量的动作。
{% endhint %}

### 参数

在execute条件中你可以添加可选的参数来减少动作组数量，以此精简你的配置。

例如，我们原来有这么一个事件：

```yaml
# 这个事件会在玩家使用/vip <玩家名> 的时候进行检查 
# 然后将玩家设置为特定的VIP组. 
# 如果玩家没有权限的话，报错信息会显示
# 如果玩家的命令没有参数，另一个报错信息会显示
vip_rank:
    type: player_command
    conditions:
    - "%main_command% == /vip"
    - "%player_has_permission_conditionalevents.admin% != yes execute error_action1"
    - "%args_length% < 1 execute error_action2"
    actions:
      default:
      - "cancel_event: true"
      - "player_command: lp user %arg_1% parent set vip"
      error_action1:
      - "cancel_event: true"
      - "centered_message: &c&m                    &r &c&l错误! &c&m                    "
      - "centered_message:  "
      - "centered_message: &c你没有权限这么做"
      - "centered_message:  "
      - "centered_message: &c&m                                                    "
      - "playsound: BLOCK_NOTE_BLOCK_PLING;10;0.1"
      error_action2:
      - "cancel_event: true"
      - "centered_message: &c&m                    &r &c&l错误! &c&m                    "
      - "centered_message:  "
      - "centered_message: &c必须按照以下格式 &7/vip <玩家名>"
      - "centered_message:  "
      - "centered_message: &c&m                                                    "
      - "playsound: BLOCK_NOTE_BLOCK_PLING;10;0.1"
```

如你所见，`error_action1`和`error_action2`十分相似,只有报错信息有差别，我们可以简化它，让它只有一个error\_action组，只需使用参数。

参数可以在execute选项之后使用`{ }`包围表达。

{% hint style="info" %}
如下

`execute error_action{%variable1%=Variable 1 value;%variable2%=Variable 2 value}`
{% endhint %}

参数的意义在于创建动作组之间可以使用的临时变量。你可以创建多个参数，只需用`;`号分割，如果我们在上面的例子使用参数，结果如下：

```yaml
vip_rank:
    type: player_command
    conditions:
    - "%main_command% == /vip"
    - "%player_has_permission_conditionalevents.admin% != yes execute error_action{%error_message%=&c没有权限}"
    - "%args_length% < 1 execute error_action{%error_message%=&c必须参照以下格式 &7/vip <player>}"
    actions:
      default:
      - "cancel_event: true"
      - "player_command: lp user %arg_1% parent set vip"
      error_action:
      - "cancel_event: true"
      - "centered_message: &c&m                    &r &c&l错误! &c&m                    "
      - "centered_message:  "
      - "centered_message: %error_message%"
      - "centered_message:  "
      - "centered_message: &c&m                                                    "
      - "playsound: BLOCK_NOTE_BLOCK_PLING;10;0.1"
```

## 例子

{% tabs %}
{% tab title="例子1" %}
这是一个完整的玩家攻击事件的配置:

```aspnet
example1:
    type: player_attack
    conditions:
    - '%victim% equals PLAYER'
    - '%item% equals DIAMOND_SWORD'
    - '%item_name% equals 极霸剑'
    - '%random_1_10% >= 8'
    actions:
      default:
      - 'message: &aYour diamond sword poison effect was activated!'
      - 'to_target: give_potion_effect: POISON;120;1'
```

在此案例中，当一名玩家用一把名为“极霸剑”的钻石剑攻击另一名玩家时，插件将进行检查并生成一个1-10的随机数。如果这个数字大于等于8，则会向玩家发送消息，目标玩家将受到中毒效果的影响。(相当于30%的几率)
{% endtab %}

{% tab title="例子2" %}
这是另一个关于 "execute" 选项的例子:

```
example2:
    type: block_interact
    conditions:
    - '%block_x% == 40'
    - '%block_y% == 60'
    - '%block_z% == 40'
    - '%block_world% equals lobby'
    - '%block% equals STONE_BUTTON'
    - '%action_type% equals RIGHT_CLICK'
    - '%statistic_jump% < 1000 execute actions2'
    actions:
      default:
      - 'message: &aYou''ve received $5000!'
      - 'console_command: eco give %player% 5000'
      actions2:
      - 'message: &cYou need at least 1000 jumps to use this button.'
```

在这种情况下，玩家必须在特定坐标按下按钮。但最后一个条件检测的是，如果他的跳跃次数不超过1000次，那么将执行“actions2”中的操作，而不是default(默认)操作。
{% endtab %}

{% tab title="例子3" %}
这是一个比较两个变量的例子:

```
example3:
    type: item_interact
    conditions:
    - '%item_name% startsWith Axe of'
    - '%item_name% !contains %player_name%'
    actions:
      default:
      - 'message: &c这不是你的斧子，你不能使用它.'
      - 'cancel_event: true'
```

想象一下，你的服务器中有一个名为"Axe of \<player>"的物品。每个玩家都有一把刻着他们名字的斧头。在这种情况下，插件将检查玩家是否与以“Axe of”开头的物品交互。然后，如果物品名称不包含玩家名字，它将取消该事件并告诉玩家该物品不是他们的。
{% endtab %}

{% tab title="例子4" %}
这是个包含数学方程的例子:

```
example4:
    type: player_command
    conditions:
    - '%command% equals /test-kills'
    - '%statistic_player_kills% >= %statistic_deaths%*2 execute actions1'
    actions:
      actions1:
      - 'message: &a你杀了很多人，恭喜你!'
      - 'cancel_event: true'
      default:
      - 'message: &c你的击杀数量至少得比死亡数大两倍'
      - 'message: &c才能使用此命令，下面是你的数据:'
      - 'message: &7击杀: &6%statistic_player_kills%'
      - 'message: &7死亡: &6%statistic_deaths%'
      - 'cancel_event: true'
```

在本例中，我们创建以下命令：/test kills。当玩家执行命令时，插件将检查玩家的击杀玩家次数是否至少比死亡次数多两倍。一个有40次死亡和20次死亡的玩家可以使用这个命令，因为40>=20\*2
{% endtab %}
{% endtabs %}
