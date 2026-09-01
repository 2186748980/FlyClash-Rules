# FlyClash 远程覆写

## 推荐文件

`flyclash-smart.yaml`

Raw 地址：

`https://raw.githubusercontent.com/2186748980/FlyClash-Rules/main/override/flyclash-smart.yaml`

它面向 FlyClash / Mihomo，提供：

- 自动创建 `⚡ FlyClash智能代理` 策略组
- 自动包含当前配置中的所有代理节点
- 广告与跟踪域名拒绝
- 私有网络直连
- OpenAI / Google / YouTube / Telegram / GitHub 等国际服务走代理
- 中国大陆域名与 IP 直连
- 未命中流量走代理
- 规则源每 24 小时自动更新

## 在 FlyClash Android 中

FlyClash Android 已支持覆写脚本通过 URL 导入，并支持通过 URL 更新；较新的版本还支持一个配置关联多个覆写脚本。

建议先备份当前配置，再添加远程覆写。

如果你的 FlyClash 版本把 `rules:` 当成整体替换，而不是合并，请先不要启用该覆写；改用仓库 `config/` 下的手动合并方案。

## 安全

本仓库不保存机场订阅地址、节点、账号、密码或 Token。
