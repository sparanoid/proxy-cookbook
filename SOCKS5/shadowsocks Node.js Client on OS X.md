## Download shadowsocks and forever
	npm install shadowsocks forever

## Configurations
	mate /usr/local/share/npm/lib/node_modules/shadowsocks/config.json

	{
	  "server":"remote.server",
	  "server_port":11111,
	  "local_port":3333,
	  "password":"passwd"
	}


## Auto start
	forever start -a -l /dev/null /usr/local/share/npm/bin/sslocal