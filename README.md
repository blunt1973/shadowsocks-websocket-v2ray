## shadowsocks-websocket-v2ray

The client is Shadowsocks, server is V2ray behind Caddy, Caddy plays a reverse proxy role can apply and renew HTTP cert from Let's Encrypt automatically to encrypt WebSocket connections.

### PREREQUISITES

-   Ubuntu 18.04
-   V2Ray v4.39.2
-   Caddy v2.4.1
-   ShadowsocksX-NG v1.9.2

### QUICKSTART

-   Install V2ray
    
    ```shell
    bash <(curl -L https://raw.githubusercontent.com/v2fly/fhs-install-v2ray/master/install-release.sh)
    ```
    
    Replace  **YOUR_PASSWORD**  and  **YOUR_V2RAY_ID**  in  `v2ray-server-config.json`, then copy it to  `/etc/v2ray/config.json`


    remember to modify the systemd service file @ /etc/systemd/system/v2ray.service 
    Add the following line to the block starting with [Service]

    
    ```console
    LimitNOFILE=1048576
    RuntimeDirectory=ss-loop
    ```
    
    Start v2ray service
    
    ```shell
    systemctl daemon-reload
    systemctl enable v2ray.service
    systemctl start v2ray.service
    ```

-   Install Caddy 2

    ```shell
    sudo apt install -y debian-keyring debian-archive-keyring apt-transport-https
    curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' | sudo apt-key add -
    curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' | sudo tee /etc/apt/sources.list.d/caddy-stable.list
    sudo apt update
    sudo apt install caddy
    ```
    
    
    Replace  **YOUR.DOMAIN.NAME**  in  `Caddyfile`, then copy it to  `/etc/Caddyfile`
    
-   Setup Shadowsocks
    
    The config file is  `shadowsocks-client-config.json`, before filling this information into the client's configuration file please replace  **YOUR.DOMAIN.NAME**  and  **YOUR_PASSWORD**.
    

### LAST.FGW!
