# FlyClash-Rules

面向 **FlyClash / Mihomo** 的个人分流与去广告规则仓库。

本仓库不保存任何机场节点、订阅地址、账号、密码或 API Key。

## 你如果使用的是 FlyClash Android 的「规则覆写」

如果你的界面是：

> 规则覆写 → 添加新规则 → 规则类型 / 域名 / 目标

那么这里的功能是**逐条添加自定义规则**，不是直接导入整个 YAML。

因此最适合手机端直接录入的是：

`rules/flyclash-essential.txt`

里面已经整理了一套精简、高价值规则，覆盖：

- OpenAI / ChatGPT
- Claude / Anthropic
- Gemini / Google AI
- GitHub
- YouTube
- Telegram
- X / Twitter
- Discord
- Reddit
- Instagram / Facebook
- Netflix
- Spotify
- TikTok
- 常见广告与跟踪域名

其中 `PROXY` 是占位符。**添加时必须替换成你自己的 FlyClash 代理策略组名称**，例如 `代理`、`Proxy`、`🚀 节点选择` 等。

建议优先添加 AI、Google、Telegram、YouTube 等你实际使用的规则；不需要一次把几十条全部手动录入。

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

## 重要：不要直接把完整 YAML 填进「规则覆写」

FlyClash Android 某些版本的「规则覆写」只接受单条规则，例如：

```text
DOMAIN-SUFFIX,openai.com,你的代理组
```

它不是 `rule-providers` 导入器。因此看到这种界面时，请使用 `rules/flyclash-essential.txt`，或者使用完整 Mihomo 配置编辑/覆写功能（如果你的版本提供）。

## 推荐规则顺序

如果你手动添加规则，通常应让更明确的规则优先于兜底规则：

1. 广告 → `REJECT`
2. 局域网 / 私有网络 → `DIRECT`
3. 明确需要代理的国际服务 → 你的代理组
4. 中国大陆 → `DIRECT`
5. 最后才使用 `MATCH` 作为兜底

注意：本仓库不建议直接提供一个名为 `PROXY` 的虚拟策略组，因为你的机场配置中实际代理组名称可能不同。

## 关于 Shadowrocket-ADBlock-Rules-Forever

本项目参考 `Johnshall/Shadowrocket-ADBlock-Rules-Forever` 的国内外分流与广告过滤思路，但针对 FlyClash / Mihomo 重新组织规则，不直接把 Shadowrocket `.conf` 当作 FlyClash 配置。

## 规则来源

主要远程规则数据来自 MetaCubeX `meta-rules-dat`。本仓库只引用公开上游数据，不复制私有节点或账号信息。

- MetaCubeX/meta-rules-dat
- Johnshall/Shadowrocket-ADBlock-Rules-Forever

## 安全说明

请勿将以下内容提交到公开仓库：

- 机场订阅 URL
- UUID / 密码 / Token
- 私有节点配置
- Clash 密钥或 API Secret
- OpenAI / Anthropic / Gemini API Key
