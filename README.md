# xray-for-tiktok-private
基于 Xray VLESS TCP XTLS SOCKS5 的双重网络代理，支持tiktok分流代理到其他 ip（反机房 ip检测机制)

## chain proxy

your ip --vless+tcp+xtls--> VPS --(non-tiktok)--> direct connect
                                --(tiktok)--> proxy provider via socks5 --> connect

## What it's for
一种躲避屏蔽机房ip检测的解决方案，i.e. for Netflix, Tiktok. 具体链路见上。

连接 VPS 后一键设置双重代理，譬如用住户 ip 做二级代理：
```
curl --socks5 127.0.0.1:9001 https://ipinfo.io # inside vps
{
  "ip": "XXXX",
  "hostname": "XXXXX",
  "city": "XXXXX",
  "region": "Virginia",
  "country": "US",
  "loc": "XXXXXXX",
  "org": "Comcast Cable Communications, LLC", # residential IP
  "postal": "XXXX",
  "timezone": "America/New_York",
  "readme": "https://ipinfo.io/missingauth"
}
```