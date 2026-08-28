# singbox and mihomo rule convert

在rule.txt添加规则集，自动生成 singbox:srs/mihomo:mrs Format。fork后自己添加想要转换的规则集。

仓库 Settings ----> Actions ----> General ----> Workflow permissions ----> Read and write permissions 勾选上

规则集源文件写法eg:  
singbox:
```json
{
  "tag": "adblock",
  "type": "remote",
  "format": "binary",
  "url": "https://gh-proxy.org/github.com/77160860/rule/raw/main/singbox/cn.srs",
  "download_detour": "DIRECT"
}
```
```json
{
  "tag": "filter",
  "type": "remote",
  "format": "source",
  "url": "https://gh-proxy.org/github.com/77160860/rule/raw/main/singbox/cn.json",
  "download_detour": "DIRECT"
}
```
mihomo:
```json
rule-anchor:
  ip: &ip {type: http, interval: 86400, behavior: ipcidr, format: mrs}
  domain: &domain {type: http, interval: 86400, behavior: domain, format: mrs}
rule-providers:
  cn:
    <<: *domain
    url: "https://gh-proxy.org/github.com/77160860/rule/raw/main/mihomo/cn.mrs"
  cnip:
    <<: *ip
    url: "https://gh-proxy.org/github.com/77160860/rule/raw/main/mihomo/cnip.mrs"
```
