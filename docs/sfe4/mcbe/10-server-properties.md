---
title: 基岩版服务器配置文件介绍
---
## 翻译过后的配置文件
:::info

以下内容来自 BDS 1.20.14.01 并使用 Google 和 DeepL 提供的翻译服务。

:::

```ini
server-name=Dedicated Server
# 服务器介绍（将显示在 服务器名称 下方）
# 允许任何字符，除了分号，也就是“;”。

gamemode=survival
# 为新玩家设置的游戏模式
# 允许值（请填写引号内的内容）: "survival",(生存) "creative"(创造), 和 "adventure"(冒险)

force-gamemode=false
# 简单来说就是强制使用服务器设置的游戏模式，具体请看下面来自 DeepL 的翻译：
# force-gamemode=false（或 server.properties 中未定义 force-gamemode）
# 防止服务器向客户端发送游戏模式值，而不是
# 游戏模式值之外的其他游戏模式值。
# 即使这些值是在创建世界后在 server.properties 中设置的。
# force-gamemode=true 会强制服务器发送游戏模式值到客户端。
# 除了服务器在创建世界时保存的游戏模式值之外
# 如果这些值是在创建世界后在 server.properties 中设置的。

difficulty=easy
# 设置世界难度
# 允许值(请填写引号内的内容): "peaceful"(和平), "easy"(简单), "normal"(普通), 或 "hard"(困难)

allow-cheats=false
# 为世界启用作弊模式，允许使用例如 /give 等指令。
# 允许值(请填写引号内的内容): "true"开 或 "false"关
# 这两个值再往下不会继续翻译，请知悉

max-players=10
# 最大玩家在线数量
# 允许值: 任何正整数

online-mode=true
# 所有连接的玩家都必须通过 Xbox Live 身份验证
# 如果关闭，则只有局域网玩家才不需要验证，远程游玩仍需通过 Xbox Live 身份验证
# 所以不如保持默认

allow-list=false
# 白名单
# 强烈建议开启
# 允许值(请填写引号内的内容): "true" or "false"

server-port=19132
# 服务器侦听的 IPv4 端口
# 允许值: 1~65535 范围内的整数
# 不用动，反正你动了面板也会改回来（

server-portv6=19133
# 服务器侦听的 IPv6 端口
# 允许值: 1~65535 范围内的整数
# 简幻欢 暂不提供 IPv6 服务，即使配置也不生效

enable-lan-visibility=true
# 允许在局域网内被发现
# 没啥用，可以改成 false
# 允许值(请填写引号内的内容): "true" or "false"

view-distance=32
# 最大视距，降低以提升服务器性能
# 允许值(以区块为单位): 大于或等于 5 的正整数

tick-distance=4
# 当玩家距离某个区块超过设定值后，该区块将会停止加载。
# 例子：你离耕地过远，农作物就会停止生长。
# 请考虑你的刷怪塔、红石机器等等，推荐保持默认。
# 允许值: 4~12 的整数

player-idle-timeout=30
# 玩家挂机时间超过设定分钟后将被踢出，如果为 0 就不会生效。
# 允许值: 任何非负整数

max-threads=8
# 多线程，如果设置为 0 或不填，服务端将会使用尽可能多的线程。
# 允许值: 任何正整数

level-name=Bedrock level
# 地图文件夹和地图名字
# 可以填写任何字符，除了分号和文件名非法符号: "/\n\r\t\f`?*\\<>|\"

level-seed=
# 没有地图时生成世界使用的种子
# 留空应该会随机生成
# 允许值: 任何字符

default-player-permission-level=member
# 为新玩家设置的权限级别
# 允许值(请填写引号内的内容): "visitor"(访客), "member"(成员), "operator"(管理员)

texturepack-required=false
# 强制使用服务器上的资源包
# 对于反矿透资源包会有用，但也会导致玩家不能自定义资源包。
# 允许值(请填写引号内的内容): "true" or "false"

content-log-file-enabled=false
# 记录错误日志
# 允许值(请填写引号内的内容): "true" or "false"

# ==================
# 以下设置建议保持默认
# 接下来仅提供修正翻译
# 部分设置会提供些建议
# ==================

compression-threshold=1
# 确定要压缩的原始网络有效负载的最小大小
# 允许值(请填写引号内的内容): 0-65535

compression-algorithm=zlib
# 确定用于网络的压缩算法
# 允许值(请填写引号内的内容): "zlib", "snappy"

server-authoritative-movement=server-auth
# 允许值(请填写引号内的内容): "client-auth", "server-auth", "server-auth-with-rewind"
# 启用服务器授权移动
# 如果使用 "server-auth"（服务器授权），服务器将重放本地用户输入
# 如果启用 "server-auth-with-rewind"，服务器将重放本地用户的输入，并在客户端位置与服务器位置不一致时发送更正。
# 如果启用了 "server-auth-with-rewind"，并且服务器发送了修正信息，客户端将被指示
# 将时间倒回修正时间，应用修正，然后重放玩家此后的所有输入。这将使修正更流畅、更频繁。
# 只有当 correct-player-movement 设置为 true 时，才会进行修正。

player-movement-score-threshold=20
# 报告异常行为之前所需的不一致时间间隔数。
# 通过 server-authoritative-movement 禁用

player-movement-action-direction-threshold=0.85
# 玩家的攻击方向和视线方向的差异量。
# 允许值(请填写引号内的内容): 0~1 内任何值
# 其中 1 表示玩家的视线方向和玩家的攻击方向必须完全一致。
# 0 表示两个方向可以相差 90 度（含 90 度）。
# 这个设置应该是用来限制第三人称视角的攻击范围

player-movement-distance-threshold=0.3
# 在检测到异常行为之前需要超过的服务器和客户端位置之间的差值。
# 通过 server-authoritative-movement 禁用。

player-movement-duration-threshold-in-ms=500
# 服务器和客户端位置不同步的持续时间（由玩家移动距离阈值定义）。
# 在异常移动分数递增之前，服务器和客户端位置不同步的持续时间（由玩家移动距离阈值定义）。该值以毫秒为单位。
# 通过 server-authoritative-movement 禁用。

correct-player-movement=false
# 如果为 true，如果移动分数超过阈值，客户端位置将被修正为服务器位置。

server-authoritative-block-breaking=false
# 如果为 true，服务器将与客户端同步计算方块挖掘操作，以便验证客户端是否能在它认为可以时破坏方块。
# 这个设置可能可以防秒挖掘(除了急迫效果)，请根据服务器配置选择。

chat-restriction=None
# 允许值(请填写引号内的内容): "None", "Dropped", "Disabled"
# 这表示对每个加入服务器的玩家的聊天限制级别。
# 默认为 "None"，表示正常的自由聊天。
# "Dropped" 表示聊天信息被丢弃，不会发送到任何客户端。玩家会收到一条信息，告诉他们“聊天被禁用”。
# "Disabled" 表示除非玩家是操作员，否则聊天界面甚至不会出现。不会向玩家显示任何信息。

disable-player-interaction=false
# 如果为 "true"，服务器将通知客户端在与世界交互时应忽略其他玩家。这不是服务器权威。

client-side-chunk-generation-enabled=true
# 如果为 "true"，服务器将通知客户端，他们可以在玩家交互距离之外生成可视化区块。

block-network-ids-are-hashes=true
# 如果为 "true"，服务器将发送散列的区块网络 ID，而不是从 0 开始向上的 ID。 这些 ID 是稳定的，不会因其他区块的变化而改变。

disable-persona=false
# 仅限内部使用
# 应该是禁用玩家的皮肤编辑器。

disable-custom-skins=false
# 如果为 "true"，则禁用玩家在 Minecraft 商店资产或游戏资产之外自定义的皮肤。 这用于禁用玩家自定义的可能具有攻击性的皮肤。

server-build-radius-ratio=Disabled
# 允许值(请填写引号内的内容): "Disabled" 或范围 0.0~1.0 中的任何值
# 如果为 "Disabled"，服务器将动态计算生成多少玩家视图，并将其余视图分配给客户端构建。
# 否则，服务器将根据重载比例来计算要生成多少玩家视图，而不考虑客户端的硬件能力。
# 仅在启用 client-side-chunk-generation-enabled 功能时有效
```

## 隐藏的 op-permission-level
在 BDS 压缩包内置的文档及 Minecraft Wiki 中，有一个未出现的配置，这个配置在 Java 版是默认写在配置文件里的，但在基岩版的配置文件并未出现。

但它却有作用，当设置为 4 之后，最明显的区别就是：游戏设置内的世界选项变得可以调整，例如打开坐标显示、死亡不掉落等设置。

如何使用？在 **server.properties** 中添加以下配置并重新启动服务器即可应用。

```ini
op-permission-level=4
```
