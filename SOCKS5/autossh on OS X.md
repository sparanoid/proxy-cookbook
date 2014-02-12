## Install autossh

	brew install autossh

## Make a .plist to make sure autossh auto run at system startup

	vi ~/Library/LaunchAgents/com.sparanoid.ssh.plist

`com.sparanoid.ssh.plist` can be changed to `com.yourname.identifier.plist`

In com.sparanoid.ssh.plist:

	<?xml version="1.0" encoding="UTF-8"?>
	<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
	<plist version="1.0">
	<dict>
		<key>KeepAlive</key>
		<dict>
			<key>SuccessfulExit</key>
			<true/>
		</dict>
		<key>Label</key>
		<string>com.sparanoid.ssh</string>
		<key>ProgramArguments</key>
		<array>
			<string>/usr/bin/autossh</string>
			<string>-M</string>
			<string>2000</string>
			<string>-NC</string>
			<string>root@106.187.36.85</string>
			<string>-D</string>
			<string>3333</string>
		</array>
		<key>RunAtLoad</key>
		<true/>
	</dict>
	</plist>