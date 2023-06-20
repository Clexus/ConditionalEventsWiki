# 命令和权限

{% hint style="info" %}
如果你使用/ce命令有问题，请使用命令全称`/conditionalevents`
{% endhint %}

| 命令                                                  | 描述                                                               |
| --------------------------------------------------- | ---------------------------------------------------------------- |
| **/ce help**                                        | 显示插件命令                                                           |
| **/ce reload**                                      | 重载插件配置文件                                                         |
| **/ce verify**                                      | 检查配置文件是否出错                                                       |
| **/ce debug \<event>**                              | 切换事件的调试模式，建议在后台使用否则会刷屏.                                          |
| **/ce reset \<player> \<event/all>**                | 重置某个玩家的事件/所有事件数据                                                 |
| **/ce enable/disale \<event>**                      | 开启/关闭一个事件                                                        |
| **/ce call \<event> (可选)%variable1%=;%variableN%=** | (配合一些变量)执行一个 'call' 类事件. 例如: /ce call event1 %test\_variable%=25 |

{% hint style="info" %}
只有唯一一个权限来访问所有这些命令：

`conditionalevents.admin`

conditionalevents.bypasscooldown.\<event> 能够跳过某一事件的冷却.
{% endhint %}
