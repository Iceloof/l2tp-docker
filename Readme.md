# L2TP server docker

## Config

### Predefined user/passwd and ip

Change `chap-secrets.example` to `chap-secrets`

Edit as following format
```
"user" l2tp "password" * //auto assign ip
"user" l2tp "password" 192.168.28.1 //set static ip for user
```
### Enviromnent setting

Change `l2tp.env.example` to `l2tp.env`

Edit as following format
```
VPN_IPSEC_PSK=your_psk
VPN_USER=user
VPN_PASSWORD=passwd
VPN_PUBLIC_IP=
VPN_L2TP_NET=
VPN_L2TP_LOCAL=
VPN_L2TP_REMOTE=
VPN_XAUTH_NET=
VPN_XAUTH_REMOTE=
VPN_DNS1=
VPN_DNS2=
VPN_SHA2_TRUNCBUG=
```

You must set `VPN_IPSEC_PSK`, `VPN_USER` and `VPN_PASSWORD`

If your VPS has multiple public IP addresses, maybe public IP need to specified in `VPN_PUBLIC_IP`.

If you want to specify a other private network, maybe need to specified in `VPN_L2TP_NET` (default `192.168.18.0/24`).

If you want to specify a other private network, maybe need to specified in `VPN_XAUTH_NET` (default `192.168.20.0/24`).

If you want to specify a `local ip` for `xl2tpd.conf`, maybe need to specified in `VPN_L2TP_LOCAL` (default `192.168.18.1`).

If you want to specify a `ip range` for `xl2tpd.conf`, maybe need to specified in `VPN_L2TP_REMOTE` (default `192.168.18.10-192.168.18.250`).

If you want to specify a `rightaddresspool` for `ipsec.conf`, maybe need to specified in `VPN_XAUTH_REMOTE` (default `192.168.20.10-192.168.20.250`).

If you want to specify a other DNS servers, maybe need to specified in `VPN_DNS1` and `VPN_DNS2` (default `8.8.8.8`, `8.8.4.4`).

**Android 6 and 7 users**: If you encounter connection issues, you may set `sha2-truncbug=yes` (default is no) in `/etc/ipsec.conf` by adding `VPN_SHA2_TRUNCBUG=yes` to `/etc/l2tp.env` file, then re-create the Docker container.

## Build & run
```
./build
```

## Support
[Teddysun - L2TP Docker](https://github.com/teddysun/across/tree/master/docker/l2tp)
