## Install ppp via yum:
	yum install ppp -y

## Download and install pptpd (the daemon for point-to-point tunneling).
You can find the correct package at this website http://poptop.sourceforge.net/yum/stable/packages/ :

	cd /usr/local/src
	rpm -Uhv http://poptop.sourceforge.net/yum/stable/packages/pptpd-1.3.4-2.el6.i686.rpm
	yum install pptpd -y

## Once installed, open /etc/pptpd.conf using text editor and add following line:
	vi /etc/pptpd.conf
	localip 192.168.0.1
	remoteip 192.168.0.234-238,192.168.0.245

## Open /etc/ppp/options.pptpd and add  authenticate method, encryption and DNS resolver value:
	vi /etc/ppp/options.pptpd
	require-mschap-v2
	require-mppe-128
	ms-dns 8.8.8.8
	ms-dns 8.8.4.4

## Lets create user to access the VPN server. Open /etc/ppp/chap-secrets and add the user as below:
	vi /etc/ppp/chap-secrets
	vpnuser pptpd myVPN$99 *

## We need to allow IP packet forwarding for this server. Open /etc/sysctl.conf via text editor and change line below:
	vi /etc/sysctl.conf
	net.ipv4.ip_forward = 1

## Run following command to take effect on the changes:
	sysctl -p

## Allow IP masquerading in IPtables by executing following line:
	iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
	service iptables save
	service iptables restart

Update: Once you have done with step 8, check the rules at `/etc/sysconfig/iptables`. Make sure that the POSTROUTING rules is above any REJECT rules.

## Turn on the pptpd service at startup and reboot the server:
	chkconfig pptpd on
	init 6

Once the server is online after reboot, you should now able to access the PPTP server from the VPN client. You can monitor `/var/log/messages` for ppp and pptpd related log. Cheers!
