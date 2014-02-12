此方法如果將 autossh 端放在境外服務器，privoxy + polipo 放在境內服務器，既為「APN」的搭建方法。本文所述的方法（privoxy + polipo 在境外），不會有翻牆效果，只有下載加速＋隱藏 IP 之功效

## Generate auth keys, leave password empty

On remote server:

	ssh-keygen

## Make sure autossh can bypass password

	cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys

## Install autossh

	yum install -y autossh

## Start autossh

	autossh -M 9000 -f -q -N -D 7070 root@localhost

## Check if autossh works

	ps aux | grep autossh
	pidof autossh

## Make sure autossh is running, run every hour

	crontab -e
	50 * * * *    autossh -M 9000 -f -q -N -D 7070 root@localhost

## Install privoxy

	yum install -y privoxy

## Edit config

	vi /etc/privoxy/config

	# listen-address  0.0.0.0:8118 # If you don't need polipo to provide cache feature, uncomment this line and delete the next line below.
	listen-address  127.0.0.1:8118 # Make sure privoxy listen on all addresses
	forward-socks5   /               127.0.0.1:7070 .

## Start privoxy server

	chkconfig privoxy on
	service privoxy start

Then point browser to `http://config.privoxy.org/` to see if it works

## Install polipo

	yum install -y polipo

## Edit config
	vi /etc/polipo/config

	proxyAddress = "0.0.0.0" # Listen on all address
	proxyPort = 8123 # polipo proxy address
	parentProxy = "127.0.0.1:8118" # privoxy HTTP proxy
	proxyName = "polipo.private.local"
	chunkHighMark = 50331648
	objectHighMark = 16384
	dnsQueryIPv6 = no

## Start polipo server

	chkconfig polipo on
	service polipo start

Then use `your.ip:8123` as your HTTP proxy server to see if it works.