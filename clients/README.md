# 多客户端适配

本仓库以“规则内容”和“客户端策略”分离为原则：规则集尽量不写死你的机场代理组名称，由客户端决定命中后走哪个策略。

## 已适配/推荐方式

| 客户端 | 适配方式 | 文件 |
|---|---|---|
| FlyClash | 手动规则覆写 | `../rules/flyclash-essential.txt` |
| Mihomo / Clash Meta | `rule-providers` | `../config/rule-providers.yaml` |
| Clash Verge Rev | Mihomo 配置 / rule-provider | `../config/` |
| FlClash | Mihomo 配置 / rule-provider | `../config/` |
| Karing | JSON ruleset / sing-box ruleset | `karing/` |
| sing-box | JSON rule-set | `sing-box/rule-set.json` |
| Hiddify Next | sing-box remote rule-set | 建议使用 `sing-box` 规则体系；Hiddify 的官方示例使用 `.srs` remote rule-set |
| Shadowrocket | `RULE-SET` / 规则列表 | `shadowrocket/remote-rules.conf` |
| Surge | `RULE-SET` | 可使用同类文本规则列表，策略在 Surge 配置中指定 |
| Stash | `rule-providers` + `rules` | 使用 Mihomo/Clash 目录中的规则提供器 |
| NekoBox | Clash/Mihomo 或 sing-box 规则体系 | 根据所用核心选择 `config/` 或 `sing-box/` |

## 策略说明

规则集本身尽量只描述“哪些域名属于哪个类别”。

- 广告：客户端策略设为 `REJECT` / `block`
- 国内：客户端策略设为 `DIRECT`
- AI / Google / Telegram / YouTube / GitHub 等国际服务：客户端策略设为你的代理策略组

你当前 FlyClash 的代理组包括 `自动选择`、`故障转移`、`宝可梦`，所以 FlyClash 手动规则版本可以直接指定 `自动选择`；通用规则集不写死这些名字。

## Hiddify 注意

Hiddify Next 基于 sing-box 路由模型，官方配置示例使用 `route.rule_set` 的 remote `.srs` 文件。不要把本仓库的 JSON 规则文件伪装成 `.srs`；如需 Hiddify 原生二进制 rule-set，应由构建流程生成对应 SRS 后再发布。

## Shadowrocket / Surge / Loon / Stash

这些客户端虽然语法细节不同，但都支持远程规则集思路。Shadowrocket 官方格式使用 `RULE-SET,<URL>,<策略>`；Surge/Loon/Stash 也分别有自己的远程规则集入口。请在客户端配置中指定策略，不要把 `自动选择` 等个人机场组名写进通用文件。
