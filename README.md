# FlyClash-Rules

面向 FlyClash / Mihomo 的个人规则仓库。

本仓库不保存任何机场节点、订阅地址、账号或密钥，只提供可复用的 Mihomo 分流思路与规则片段。

## 目标

- 中国大陆常用网站与服务：DIRECT
- Google / YouTube / Telegram / OpenAI / GitHub 等国际服务：PROXY
- 广告与常见跟踪域名：REJECT
- 私有地址与局域网：DIRECT
- 中国 IP：DIRECT
- 未命中的流量：PROXY

## 使用

主规则片段位于 `config/rules.yaml`。

将其中 `rules:` 下的规则合并到自己的 Mihomo 配置，并把 `PROXY` 替换成你自己的代理策略组名称即可。

如果你的 FlyClash 已经启用 Mihomo 的 `geosite` 数据，可以直接使用 `GEOSITE` 规则，不需要额外下载一堆本地规则文件。

## 规则来源

本仓库使用 MetaCubeX `meta-rules-dat` 提供的 Mihomo geosite 数据，并参考 Johnshall/Shadowrocket-ADBlock-Rules-Forever 的“国内外分流 + 广告过滤”思路重新适配 Mihomo，而不是直接复制 Shadowrocket `.conf` 文件。

MetaCubeX 官方规则项目：
https://github.com/MetaCubeX/meta-rules-dat

Johnshall 项目：
https://github.com/Johnshall/Shadowrocket-ADBlock-Rules-Forever

## 注意

1. `PROXY` 只是示例策略组名称，不包含节点。
2. 不建议把机场订阅直接提交到公开仓库。
3. 如果某个国内服务被误代理，可在 `config/rules.yaml` 最前面添加自己的 DIRECT 规则。
4. 如果某个国外服务误直连，可添加自己的 PROXY 规则并放在通用 CN 规则之前。
