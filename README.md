# kcp-shadowsocks-docker

A docker image for [shadowsocks-libev](https://github.com/shadowsocks/shadowsocks-libev) server with [KCPTUN](https://github.com/xtaci/kcptun) support

### Download from Docker Hub 

    docker pull imhang/kcp-shadowsocks-docker

### Usage

    docker run -p 443:443 -p 443:443/udp -p 9443:9443/udp --rm -it imhang/kcp-shadowsocks-docker

or running as a service

    docker run -d --restart=always -e "SS_PORT=443" -e "SS_PASSWORD=123456" -e "SS_METHOD=chacha20-ietf-poly1305" -e "SS_TIMEOUT=600" -e "KCP_PORT=9443" -e "KCP_MODE=fast" -e "MTU=1400" -e "SNDWND=1024" -e "RCVWND=1024" -p 443:443 -p 443:443/udp -p 9443:9443/udp --name ssserver imhang/kcp-shadowsocks-docker

### KCP Parameters for client

    --crypt none --mode fast --mtu 1400 --sndwnd 128 --rcvwnd 512 --parityshard 0 --nocomp

### Default configuration in environment variables

    SS_PORT     443

    SS_PASSWORD 123456

    SS_METHOD   chacha20-ietf-poly1305

    SS_TIMEOUT  600

    KCP_PORT    9443

    KCP_KEY     123456

    KCP_CRYPT   none

    KCP_MODE    fast

    MTU         1400

    SNDWND      512

    RCVWND      128

    DATASHARD   10

    PARITYSHARD 0
