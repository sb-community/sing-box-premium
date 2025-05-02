# 自动构建sing box 内核
* 支持 proxy-provider
* full tag (except "with_embedded_tor")
* 来自于[sing-box下游仓库](https://github.com/reF1nd/sing-box/blob/reF1nd-dev/)
* 手动构建:
```
CGO_ENABLED=0 go build -v -trimpath -ldflags "-checklinkname=0 -X 'github.com/sagernet/sing-box/constant.Version=$(curl -s https://api.github.com/repos/SagerNet/sing-box/releases | grep '"tag_name"' | head -n 1 | cut -d ":" -f2 | sed 's/[",v ]//g')' -s -w -buildid=" -tags "with_quic with_grpc with_dhcp with_wireguard with_ech with_utls with_reality_server with_acme with_clash_api with_v2ray_api with_gvisor with_tailscale" ./cmd/sing-box
```

## 使用说明
* [官方文档](https://sing-box.sagernet.org/zh/configuration/)
* [更多特性](https://github.com/reF1nd/sing-box/blob/reF1nd-dev/README.md)
* 引用proxy-provider:
```
{
    // 通过出站组引用，否则订阅不起作用。
    "type": "selector", // selector, loadbalance, urltest...
    "exclude": "",
    "include": "",
    "providers": [
      "provider"
    ]
}
```
* 一个[示例配置](https://gist.githubusercontent.com/krisstibex/82ec9d8c05f0fb1a596d3d40739314c8/raw/config.json) 修改自[Lucy](https://github.com/Repcz)的[sing-box配置](https://raw.githubusercontent.com/Repcz/Tool/refs/heads/X/sing-box/Client/v1.12/config.json)
