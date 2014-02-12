**WIP**

autossh + polipo method:

	#config file for polipo @ /usr/local/etc/polipo/

	proxyAddress = "0.0.0.0"    # IPv4 only
	proxyPort = 8119
	allowedClients = 127.0.0.1,211.161.103.253
	allowedPorts=1-65535
	proxyName = "APN代理"
	socksParentProxy = "localhost:7070"
	socksProxyType = socks5
	chunkHighMark = 819200
	objectHighMark = 128
	diskCacheFilePermissions=0640
	diskCacheDirectoryPermissions=0750
	disableIndexing = false
	disableServersList = false
	dnsQueryIPv6 = no
	disableVia=false
	censoredHeaders = from, accept-language
	pmmFirstSize = 16384
	pmmSize = 8192
	maxConnectionAge = 5m
	maxConnectionRequests = 120
	serverMaxSlots = 8
	serverSlots = 4
	tunnelAllowedPorts = 1-65535

Source: http://bao3.blogspot.jp/2012/01/apn-proxy-apn.html