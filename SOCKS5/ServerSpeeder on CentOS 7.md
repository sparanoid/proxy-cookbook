http://my.serverspeeder.com/w.do?m=lsl

cd /tmp/

wget http://my.serverspeeder.com/d/ls/serverSpeederInstaller.tar.gz

tar xzvf serverSpeederInstaller.tar.gz

bash serverSpeederInstaller.sh

ps -ef | grep serverspeeder

ps -ef | grep ssserver

/serverspeeder/bin/serverSpeeder.sh start
/serverspeeder/bin/serverSpeeder.sh reload
/serverspeeder/bin/serverSpeeder.sh restart
/serverspeeder/bin/serverSpeeder.sh stop
/serverspeeder/bin/serverSpeeder.sh stats
/serverspeeder/bin/serverSpeeder.sh status

https://github.com/shadowsocks/shadowsocks/wiki/Optimizing-Shadowsocks
sysctl -p /etc/sysctl.conf

Not implemented:
systemctl list-unit-files --type=service | grep serverspeeder
service serverspeeder status
systemctl enable serverspeeder.service
