Since Shadowsocks Node.js is [deprecated](https://github.com/shadowsocks/shadowsocks-nodejs), here's a libev version:

## Uninstall shadowsocks Node.js version first
    npm uninstall -g shadowsocks

## Install
    yum install python-setuptools && easy_install pip
    pip install shadowsocks

## Upgrade

    pip install shadowsocks --upgrade

## Configurations
    vi ~/.ssconfig.json

    {
        "server":"0.0.0.0",
        "server_port":8388,
        "local_port":3333,
        "password":"pass!word!",
        "timeout":600,
        "workers":2,
        "fast_open":true,
        "method":"aes-256-cfb"
    }

    ssserver -c ~/.ssconfig.json -d start

## Auto start
    vi /etc/rc.local
    ssserver -c ~/.ssconfig.json -d start

## Stop
    ssserver -c ~/.ssconfig.json -d stop

## Restart
    ssserver -c ~/.ssconfig.json -d restart
