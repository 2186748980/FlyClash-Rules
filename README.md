# 分流规则中心

一个面向多种代理客户端的个人分流、去广告与 AI/海外服务规则仓库。

目标是：**一份规则，多种客户端使用；尽量复制即用，不绑定某一个软件。**

## 快速入口

- 网页版：`web/index.html`（部署为静态网页后可使用一键复制）
- 通用规则：`rules/`
- Mihomo / Clash 系：`config/`
- 客户端专用适配：`clients/`

## 支持方向

| 客户端/核心 | 适配方式 |
|---|---|
| Mihomo / Clash Meta | YAML / Rule Provider |
| Clash Verge Rev | Mihomo 配置 |
| FlClash | Mihomo 配置 |
| FlyClash | 规则覆写 / Mihomo |
| Karing | 对应规则集 |
| sing-box | Rule Set |
| Hiddify Next | sing-box 路由规则 |
| Shadowrocket | RULE-SET / 规则列表 |
| Surge | 规则集 |
| Stash | Mihomo / Rule Provider |
| NekoBox | Clash/Mihomo 或 sing-box |

不同客户端的能力和语法并不完全一致，因此仓库不会把所有客户端强行使用同一个文件。

## 规则原则

- 广告与常见跟踪器：`REJECT`
- 国内/局域网：`DIRECT`
- AI、Google、GitHub、YouTube、Telegram、社交媒体和流媒体等海外服务：默认进入代理策略
- 不保存机场订阅、节点、UUID、密码、Token 或 API Key
- 通用规则尽量与具体代理组名称解耦

## 当前个人代理组示例

当前使用的订阅提供：

- `自动选择`
- `故障转移`
- `宝可梦`
- `DIRECT`
- `REJECT`

手动覆写版本可以直接使用这些名称；通用规则集则尽量不写死策略组，方便换软件或换订阅。

## 文件说明

### `rules/`

适合手动添加或作为简单规则列表使用。

### `config/`

面向 Mihomo/Clash 系客户端的配置片段和 Rule Provider。

### `clients/`

保存针对特定客户端能力差异整理的适配文件。

### `web/`

简单的规则复制页面。部署为静态站点后，可以在手机浏览器里直接点击“复制全部”。

## 安全

请勿提交机场订阅 URL、私有节点、UUID、密码、Token、Clash 管理密钥或任何 AI API Key。
