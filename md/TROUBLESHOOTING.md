# `@uchilaka/mw--cami--cms`: Troubleshooting your local environment

## Setup of server hostnames did not succeed

Check where your local NGINX service is set up by running `brew info nginx`. The output will look like this:

```shell
==> nginx: stable 1.27.4 (bottled), HEAD
HTTP(S) server and reverse proxy, and IMAP/POP3 proxy server
https://nginx.org/
Installed
/opt/homebrew/Cellar/nginx/1.25.5 (26 files, 2.4MB) *
  Poured from bottle using the formulae.brew.sh API on 2024-04-17 at 18:01:18
From: https://github.com/Homebrew/homebrew-core/blob/HEAD/Formula/n/nginx.rb
License: BSD-2-Clause
==> Dependencies
Required: openssl@3 ✘, pcre2 ✔
==> Options
--HEAD
 Install HEAD version
==> Caveats
Docroot is: /opt/homebrew/var/www

The default port has been set in /opt/homebrew/etc/nginx/nginx.conf to 8080 so that
nginx can run without sudo.

nginx will load all files in /opt/homebrew/etc/nginx/servers/.

To restart nginx after an upgrade:
  brew services restart nginx
Or, if you don't want/need a background service you can just run:
  /opt/homebrew/opt/nginx/bin/nginx -g daemon\ off\;
==> Analytics
install: 14,710 (30 days), 39,202 (90 days), 166,574 (365 days)
install-on-request: 14,655 (30 days), 39,074 (90 days), 166,135 (365 days)
build-error: 8 (30 days)
```

Make a note of where nginx will load files from (in the example above, that location is `/opt/homebrew/etc/nginx/servers/`).

Next, run the following script to symlink the project's NGINX server configurations:

```shell
export NGINX_PATH="/opt/homebrew/etc/nginx"
export NGINX_SERVERS_PATH="${NGINX_PATH}/servers"

# Ensure the location is created (if it doesn't exist)
mkdir -vp $NGINX_SERVERS_PATH

# Next, from the project root directory, symlink the compliance host configurations
ln -s $(pwd)/.nginx/development.conf "${NGINX_SERVERS_PATH}/larcity-crm.conf"

# Restart your nginx service
brew services restart nginx

# Check the status of your nginx service to make sure the configurations loaded correctly
brew services info nginx
```
