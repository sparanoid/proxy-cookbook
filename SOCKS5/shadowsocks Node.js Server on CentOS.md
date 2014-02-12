## Install git
	yum install git

## Install nvm
	curl https://raw.github.com/creationix/nvm/master/install.sh | sh
	. /root/.nvm/nvm.sh
	nvm install 0.8.16

## Install forever
	nvm install -g forever

## Download shadowsocks
	cd /usr/share/
	git clone git://github.com/clowwindy/shadowsocks-nodejs.git shadowsocks-nodejs

## Configurations
	vi ~/.ssconfig.json

	{
	    "server":"0.0.0.0",
	    "server_port":8388,
	    "local_port":3333,
	    "password":"pass!word!",
	    "timeout":600,
	    "method":"aes-256-cfb"
	}

## Auto start
	vi /etc/rc.local
	forever start -a -l /dev/null /usr/bin/ssserver -c ~/.ssconfig.json