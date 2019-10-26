## shadowsocks-websocket-v2ray
The client is Shadowsocks, server is V2ray behind Caddy, Caddy plays a reverse proxy role can apply and renew HTTP cert from Let's Encrypt automatically to encrypt WebSocket connections.

### PREREQUISITES

- Ubuntu 18.04
- V2Ray v4.20.0
- Caddy v1.0.3
- ShadowsocksX-NG v1.9.2



### QUICKSTART
- Install V2ray
  
  
 `curl -Ls https://install.direct/go.sh | sudo bash`
 
 Replace **YOUR_PASSWORD** and **YOUR_V2RAY_ID** in `v2ray-config.json`, then copy it to `/etc/v2ray/config.json`
 
 Start v2ray service
 
 `systemctl start v2ray`
 
 
- Install Caddy
 
 > Please DON'T use Caddy 2.0+, the configuration format is completely different.
 
  
 `curl https://getcaddy.com | bash -s personal hook.service`
 
 Replace **YOUR.DOMAIN.NAME** in `Caddyfile`, then copy it to `/etc/Caddyfile`
 
 Setup Caddy as a service
 
 `caddy -service install -conf /etc/Caddyfile`
 
 Start Caddy service
 
 `caddy -service start`
 
- Setup Shadowsocks

  The config file is `shadowsocks-client-config.json`, before filling this information into the client's configuration file please replace **YOUR.DOMAIN.NAME** and **YOUR_PASSWORD**.
  
  
### LAST.FGW!