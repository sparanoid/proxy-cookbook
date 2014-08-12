# SOCKS5 + Polipo HTTP Proxy on OS X

Polipo configurations:

```
# config file for polipo @ ~/.polipo

proxyAddress = "0.0.0.0"
proxyPort = 8119
allowedClients = 127.0.0.1, 10.0.1.0/24
allowedPorts = 1-65535
tunnelAllowedPorts = 1-65535
proxyName = "localhost"
cacheIsShared = false
socksParentProxy = "127.0.0.1:8080"
socksProxyType = socks5
# chunkHighMark = 33554432
# diskCacheRoot = ""
# localDocumentRoot = ""
disableLocalInterface = true
disableConfiguration = true
dnsUseGethostbyname = yes
disableVia = true
censoredHeaders = from,accept-language,x-pad,link
censorReferer = maybe
# maxConnectionAge = 5m
# maxConnectionRequests = 120
# serverMaxSlots = 8
# serverSlots = 2
```

## Emtpy Polipo cache via Cron

```
0 5,16 * * * bash ~/Dropbox/Mac/Backups/Scripts/cleanup-polipo.sh
```

In `cleanup-polipo.sh`:

```bash
# MAILTO=""
# Run everyday at 5:00 AM and 4:00 PM
# 0 5,16 * * * bash ~/Documents/Backups/Scripts/cleanup-polipo.sh
# 0 5,16 * * * bash ~/Dropbox/Mac/Backups/Scripts/cleanup-polipo.sh

cache_dir="/usr/local/var/cache/polipo/"

find "$cache_dir" -mtime +14 -exec rm -rf {} \;
```

## References


- Source: http://bao3.blogspot.jp/2012/01/apn-proxy-apn.html

