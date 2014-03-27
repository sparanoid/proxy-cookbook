# How to Make Sure Dropbox Notify Server Accessible Without Global Proxy

## Edit config

	vi /usr/local/etc/privoxy/config

## At the end of the config, add the following rule:

	forward          .dropbox.com:443         .

## Restart privoxy:

	privoxy /usr/local/etc/privoxy/config
