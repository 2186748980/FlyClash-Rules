# FlyClash-Rules

面向 **FlyClash / Mihomo** 的个人分流与去广告规则仓库。

本仓库不保存任何机场节点、订阅地址、账号、密码或密钥。

## 推荐用法

如果你的 FlyClash 使用的是 Mihomo 内核，推荐使用 **Rule Provider 方案**：

- `config/rule-providers.yaml`：远程规则提供器
- `config/rules-provider-rules.yaml`：与上述 Provider 配套的 `rules:`
- `config/rules.yaml`：不依赖远程 Rule Provider 的 GEOSITE 简洁版
- `config/base-settings.yaml`：GEOSITE / GeoData 可选基础设置

Mihomo 原生支持 `rule-providers`，HTTP Provider 可以按 `interval` 自动更新，支持 `domain` / `ipcidr` / `classical` 等行为，并支持 YAML / text / MRS 格式。

## 规则逻辑

默认设计为：

1. 广告与常见跟踪域名 → `REJECT`
2. 局域网 / 私有地址 → `DIRECT`
3. OpenAI / Google / YouTube / Telegram / GitHub / Twitter / Facebook / Instagram / Netflix / Spotify / Reddit / Discord / TikTok → `PROXY`
4. 中国大陆域名与中国 IP → `DIRECT`
5. 其余未知流量 → `PROXY`

**注意：** `PROXY` 只是示例策略组名称。你的 FlyClash 配置如果叫 `Proxy`、`代理`、`🚀 节点选择` 等，需要把规则里的 `PROXY` 替换成自己的策略组名称。

## 直接引用本仓库

主规则 Provider：

```text
https://raw.githubusercontent.com/2186748980/FlyClash-Rules/main/config/rule-providers.yaml
```

配套规则：

```text
https://raw.githubusercontent.com/2186748980/FlyClash-Rules/main/config/rules-provider-rules.yaml
```

## 手动合并示例

在自己的 Mihomo 配置中加入：

```yaml
rule-anchor:
  domain: &domain
    type: http
    interval: 86400
    behavior: domain
    format: mrs

rule-providers:
  ads:
    <<: *domain
    url: "https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/meta/geo/geosite/category-ads-all.mrs"
  openai:
    <<: *domain
    url: "https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/meta/geo/geosite/openai.mrs"
  telegram:
    <<: *domain
    url: "https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/meta/geo/geosite/telegram.mrs"
```

然后把 `config/rules-provider-rules.yaml` 的 `rules:` 合并进去。

## 关于 Shadowrocket-ADBlock-Rules-Forever

本项目参考 Johnshall/Shadowrocket-ADBlock-Rules-Forever 的“国内外分流 + 广告过滤”思路，但**不直接使用 Shadowrocket `.conf`**，而是按 Mihomo 的 `RULE-SET` / `rule-providers` 机制重新组织。

## 规则来源

主要规则数据来自 MetaCubeX `meta-rules-dat`，其官方 Mihomo 配置示例也采用远程 MRS Rule Provider 的方式。

- MetaCubeX/meta-rules-dat：`https://github.com/MetaCubeX/meta-rules-dat`
- Johnshall/Shadowrocket-ADBlock-Rules-Forever：`https://github.com/Johnshall/Shadowrocket-ADBlock-Rules-Forever`

## 安全说明

不要把以下内容提交到公开仓库：

- 机场订阅 URL
- UUID / 密码 / Token
- 私有节点配置
- Clash 密钥或 API Secret

本仓库只存规则和公开的上游规则地址。
