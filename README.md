# FlyClash-Rules

一个面向 **Clash / Mihomo / sing-box / Karing / FlyClash / Shadowrocket / Surge / Stash / Hiddify / NekoBox** 等客户端的个人分流与去广告规则仓库。

本仓库不保存任何机场节点、订阅地址、账号、密码或 API Key。

## 目标

同一套规则内容，按客户端提供不同的适配层。规则集尽量不写死个人机场的代理组名称，由客户端决定命中后的策略。

## 客户端适配

详细说明见 [`clients/README.md`](clients/README.md)。

| 客户端/核心 | 推荐入口 |
|---|---|
| FlyClash | `rules/flyclash-essential.txt` |
| Mihomo / Clash Meta | `config/` |
| Clash Verge Rev | `config/`（Mihomo rule-provider） |
| FlClash | `config/`（Mihomo rule-provider） |
| Karing | `clients/karing/`；也可使用 sing-box 规则体系 |
| sing-box | `clients/sing-box/` |
| Hiddify Next | sing-box remote `.srs` 规则体系 |
| Shadowrocket | `clients/shadowrocket/` |
| Surge | 使用通用 RULE-SET 思路，策略在客户端指定 |
| Stash | Mihomo/Clash `rule-providers` |
| NekoBox | 按所使用的 Clash/Mihomo 或 sing-box 核心选择对应规则 |

## 你的 FlyClash Android 当前用法

你当前版本的界面是：

> 规则覆写 → 添加新规则 → 规则类型 / 匹配内容 / 目标

它支持多种 Mihomo 规则类型，而且「目标」除了 `DIRECT` / `REJECT` 外，还可以使用当前订阅已有的策略组。

你当前提供的代理目标包括：

- `自动选择`（本仓库默认）
- `故障转移`
- `宝可梦`

因此 `rules/flyclash-essential.txt` 已经直接使用 `自动选择`。

## FlyClash 推荐规则

文件：`rules/flyclash-essential.txt`

包含：

- OpenAI / ChatGPT → `自动选择`
- Claude / Anthropic → `自动选择`
- Gemini / Google AI → `自动选择`
- GitHub → `自动选择`
- YouTube → `自动选择`
- Telegram → `自动选择`
- X / Twitter → `自动选择`
- Discord / Reddit → `自动选择`
- Instagram / Facebook → `自动选择`
- Netflix / Spotify / TikTok → `自动选择`
- 常见广告与跟踪域名 → `REJECT`

### 添加方法

打开 FlyClash：

`规则覆写 → 右上角 +`

例如：

```text
DOMAIN-SUFFIX,openai.com,自动选择
```

填写：

- 规则类型：`DOMAIN-SUFFIX`
- 域名：`openai.com`
- 目标：`自动选择`

广告规则：

```text
DOMAIN-SUFFIX,doubleclick.net,REJECT
```

## 通用规则源

`rules/common/` 保存不绑定策略组的基础规则内容：

- `ai-proxy.list`：AI、Google、GitHub、Telegram、YouTube、社交与流媒体等国际服务
- `reject.list`：常见广告与跟踪域名

这些文件可以作为其他客户端生成/转换规则集的源数据。

## Mihomo / Clash

如果客户端支持 Mihomo `rule-providers`，推荐使用：

- `config/rule-providers.yaml`
- `config/rules-provider-rules.yaml`
- `config/rules.yaml`
- `config/base-settings.yaml`

远程入口：

```text
https://raw.githubusercontent.com/2186748980/FlyClash-Rules/main/config/rule-providers.yaml
```

配套规则：

```text
https://raw.githubusercontent.com/2186748980/FlyClash-Rules/main/config/rules-provider-rules.yaml
```

## Karing / sing-box

Karing 同时支持 Clash 配置与 sing-box 路由规则，并提供自己的 rule-set 仓库；本项目提供 Karing JSON 和 sing-box JSON 适配层，不把 Karing 的 `srs` 二进制格式伪装成普通 JSON。citeturn0search0turn0search6

- `clients/karing/ai-proxy.json`
- `clients/karing/reject.json`
- `clients/sing-box/rule-set.json`

## Hiddify Next

Hiddify Next 使用 sing-box 路由模型，官方配置示例使用 `route.rule_set` 的 remote `.srs` 规则集。仓库目前只提供可复用的 sing-box JSON 规则源，不把 JSON 冒充 `.srs`；以后如果增加构建流程，再生成真正的 SRS 文件。citeturn2search0turn2search1

## Shadowrocket / Surge / Stash

Shadowrocket 支持 `RULE-SET,<URL>,<策略>`，因此可以直接使用远程规则集思路；Surge、Stash 也采用远程规则集/Rule Provider 机制。策略名称由客户端自己的配置决定，不把 `自动选择` 等个人机场组名写进通用规则。citeturn1search0turn1search4turn1search14

Shadowrocket 适配文件：

`clients/shadowrocket/remote-rules.conf`

## 关于 Shadowrocket-ADBlock-Rules-Forever

本项目参考 `Johnshall/Shadowrocket-ADBlock-Rules-Forever` 的国内外分流与广告过滤思路，但针对不同核心重新组织适配，不直接把 Shadowrocket `.conf` 当成所有客户端的配置。

## 规则来源

主要远程规则数据来自 MetaCubeX `meta-rules-dat`。Karing/sing-box 适配同时参考 KaringX 的公开规则集结构。citeturn0search6

## 安全说明

请勿将以下内容提交到公开仓库：

- 机场订阅 URL
- UUID / 密码 / Token
- 私有节点配置
- Clash 密钥或 API Secret
- OpenAI / Anthropic / Gemini API Key
