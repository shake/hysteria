# ![Hysteria 2](logo.svg)

[![License][1]][2] [![Release][3]][4] [![Telegram][5]][6] [![Discussions][7]][8]

[1]: https://img.shields.io/badge/license-MIT-blue
[2]: LICENSE.md
[3]: https://img.shields.io/github/v/release/apernet/hysteria?style=flat-square
[4]: https://github.com/apernet/hysteria/releases
[5]: https://img.shields.io/badge/chat-Telegram-blue?style=flat-square
[6]: https://t.me/hysteria_github
[7]: https://img.shields.io/github/discussions/apernet/hysteria?style=flat-square
[8]: https://github.com/apernet/hysteria/discussions

<h2 style="text-align: center;">Hysteria is a powerful, lightning fast and censorship resistant proxy.</h2>

### 安装流程

安装

```
bash <(curl -fsSL https://get.hy2.sh/)
```
指定版本

```
bash <(curl -fsSL https://get.hy2.sh/) --version v2.4.4
```

卸载

```
bash <(curl -fsSL https://get.hy2.sh/) --remove

```

[官方文档参数详细说明，提供视频，文档](https://idev.dev/proxy/hysteria2.html)

### 服务器端推荐配置

```
listen: :443

tls:
  cert: 你的证书文件
  key: 你的秘钥文件

quic:
  initStreamReceiveWindow: 8388608
  maxStreamReceiveWindow: 8388608
  initConnReceiveWindow: 20971520
  maxConnReceiveWindow: 20971520
  maxIdleTimeout: 30s
  maxIncomingStreams: 1024
  disablePathMTUDiscovery: false

bandwidth:
  up: 0 gbps
  down: 0 gbps

ignoreClientBandwidth: false
disableUDP: false
udpIdleTimeout: 60s

auth:
  type: userpass
  userpass:
    elden: 你的密码

resolver:
  type: https
  https:
    addr: 1.1.1.1:443
    timeout: 10s
    sni: cloudflare-dns.com
    insecure: false

acl:
  inline:
    - reject(geoip:cn)

trafficStats:
  listen: :19999
  secret: 你的流量监测密码
 
masquerade:
  type: proxy
  proxy:
    url: https://github.com/
    rewriteHost: true
  listenHTTP: :80
  listenHTTPS: :443
  forceHTTPS: true
```

### 客户端建议配置

```
server: hysteria2://你的用户名:你的密码@你的域名或者IP

tls:
  sni: 你的域名
  insecure: false

transport:
  type: udp
  udp:
    hopInterval: 30s

quic:
  initStreamReceiveWindow: 8388608
  maxStreamReceiveWindow: 8388608
  initConnReceiveWindow: 20971520
  maxConnReceiveWindow: 20971520
  maxIdleTimeout: 30s
  keepAlivePeriod: 10s
  disablePathMTUDiscovery: false

bandwidth:
  up: 1000 mbps
  down: 1000 mbps

fastOpen: true
lazy: false

socks5:
  listen: 127.0.0.1:1080 
  username: elden 
  password: elden 
  disableUDP: false 

http:
  listen: 127.0.0.1:1081
  username: elden
  password: 123456

```




### [Get Started](https://v2.hysteria.network/)

### [中文文档](https://v2.hysteria.network/zh/)


---

<div class="feature-grid">
  <div>
    <h3>🛠️ Jack of all trades</h3>
    <p>Wide range of modes including SOCKS5, HTTP Proxy, TCP/UDP Forwarding, Linux TProxy, TUN - with more features being added constantly.</p>
  </div>

  <div>
    <h3>⚡ Blazing fast</h3>
    <p>Powered by a customized QUIC protocol, Hysteria is designed to deliver unparalleled performance over unreliable and lossy networks.</p>
  </div>

  <div>
    <h3>✊ Censorship resistant</h3>
    <p>The protocol masquerades as standard HTTP/3 traffic, making it very difficult for censors to detect and block without widespread collateral damage.</p>
  </div>
  
  <div>
    <h3>💻 Cross-platform</h3>
    <p>We have builds for every major platform and architecture. Deploy anywhere & use everywhere. Not to mention the long list of 3rd party apps.</p>
  </div>

  <div>
    <h3>🔗 Easy integration</h3>
    <p>With built-in support for custom authentication, traffic statistics & access control, Hysteria is easy to integrate into your infrastructure.</p>
  </div>
  
  <div>
    <h3>🤗 Chill and supportive</h3>
    <p>We have well-documented specifications and code for developers to contribute and/or build their own apps. And a helpful community, too.</p>
  </div>
</div>

---

**If you find Hysteria useful, consider giving it a ⭐️!**

[![Star History Chart](https://api.star-history.com/svg?repos=apernet/hysteria&type=Date)](https://star-history.com/#apernet/hysteria&Date)
