# FlyClash-Rules

面向 **FlyClash / Mihomo** 的个人分流与去广告规则仓库。

本仓库不保存任何机场节点、订阅地址、账号、密码或 API Key。

## 你的 FlyClash Android 当前用法

你当前版本的界面是：

> 规则覆写 → 添加新规则 → 规则类型 / 匹配内容 / 目标

它支持多种 Mihomo 规则类型，并且「目标」除了 `DIRECT` / `REJECT` 外，还可以使用你当前订阅已有的策略组。

你当前提供的可用代理目标包括：

- `自动选择`（本仓库默认）
- `故障转移`
- `宝可梦`

因此 `rules/flyclash-essential.txt` 已经直接使用 `自动选择`，无需再把 `PROXY` 手动替换。

## 推荐的手机端规则

文件：

`rules/flyclash-essential.txt`

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

然后按照文件中的每一行添加。例如：

```text
DOMAIN-SUFFIX,openai.com,自动选择
```

对应填写：

- 规则类型：`DOMAIN-SUFFIX`
- 域名：`openai.com`
- 目标：`自动选择`

广告规则例如：

```text
DOMAIN-SUFFIX,doubleclick.net,REJECT
```

## 为什么默认使用「自动选择」

你现有订阅已经提供 `自动选择`、`故障转移`、`宝可梦` 等代理组。

本仓库默认让国外服务走 `自动选择`，这样由你现有的代理组自行选择节点，不把具体国家节点写死。

如果你更喜欢固定策略，可以自行把目标改成 `故障转移` 或 `宝可梦`。

## Mihomo / 完整配置用户

如果你的配置支持 Mihomo `rule-providers`，则推荐使用：

- `config/rule-providers.yaml`：远程规则提供器
- `config/rules-provider-rules.yaml`：配套 `rules:`
- `config/rules.yaml`：简洁的 GEOSITE 方案
- `config/base-settings.yaml`：基础设置参考

规则源使用 MetaCubeX 的 MRS 数据，并按 24 小时自动更新。仓库本身只保存公开规则地址，不保存节点。

### 远程 Rule Provider

```text
https://raw.githubusercontent.com/2186748980/FlyClash-Rules/main/config/rule-providers.yaml
```

配套规则：

```text
https://raw.githubusercontent.com/2186748980/FlyClash-Rules/main/config/rules-provider-rules.yaml
```

## 关于 Shadowrocket-ADBlock-Rules-Forever

本项目参考 `Johnshall/Shadowrocket-ADBlock-Rules-Forever` 的国内外分流与广告过滤思路，但针对 FlyClash / Mihomo 重新组织规则，不直接把 Shadowrocket `.conf` 当作 FlyClash 配置。

## 规则来源

主要远程规则数据来自 MetaCubeX `meta-rules-dat`。本仓库只引用公开规则地址，不复制私有节点或账号信息。

- MetaCubeX/meta-rules-dat
- Johnshall/Shadowrocket-ADBlock-Rules-Forever

## 安全说明

请勿将以下内容提交到公开仓库：

- 机场订阅 URL
- UUID / 密码 / Token
- 私有节点配置
- Clash 密钥或 API Secret
- OpenAI / Anthropic / Gemini API Key
