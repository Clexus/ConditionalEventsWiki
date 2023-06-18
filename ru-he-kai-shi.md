# 如何开始

## 需求

#### 1) Spigot

{% hint style="warning" %}
你需要Spigot或者Paper来运行此插件，不要用Craftbukkit.
{% endhint %}

#### 2) PlaceholderAPI

{% hint style="info" %}
此依赖完全可选.\
如果你需要验证某些变量，那么你需要这个插件.\
[https://www.spigotmc.org/resources/placeholderapi.6245/](https://www.spigotmc.org/resources/placeholderapi.6245/)
{% endhint %}

{% hint style="warning" %}
记住下载变量的方法，这里以Player扩展为例: `1) /papi ecloud download Player`\
`2) /papi reload`
{% endhint %}

## 安装

下载此插件，放入你的服务器的plugin文件夹. 例子会自动生成在config里面，你可以把它们用作参考或是删除它们.

## Config.yml

要创建一个新的事件，只需在配置文件中的Events路径下添加新的配置段。记得不同的事件要用不同的名字。

## Events文件夹

可以在events文件夹下创建更多的事件文件，合理安排事件文件可以让你的事件井井有条，事件同样需要在Events路径下声明。

{% hint style="warning" %}
每个事件的名字不能相同！无论它们在哪个文件里
{% endhint %}
