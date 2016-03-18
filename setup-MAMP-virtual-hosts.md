# Setup virtual hosts in MAMP

## Setup host names

Host names map domains to specific IP's. The referneced IP may be localhost, or remote server.

Open host name configuration file

```bash
$ open -a Atom /private/etc/hosts
```

Setup

```
# serve 127.0.0.1, when XYZ.com is requested

127.0.0.1 ABC.com
127.0.0.1 XYZ.com
```

***

## Setup virtual hosts

Open vhosts configuration file

```shell
$ open -a Atom /Applications/MAMP/conf/apache/extra/httpd-vhosts.conf
```
or
```
$ open -a Atom /private/etc/apache2/extra/httpd-vhosts.conf
```

Setup

```
<VirtualHost *:80>
  DocumentRoot "/Applications/Mamp/htdocs/multisite" ## content to be served
  ServerName apples.com
  ServerAlias www.apples.com
</VirtualHost>

<VirtualHost *:80>
  DocumentRoot "/Applications/Mamp/htdocs/multisite" ## content to be served
  ServerName oranges.com
  ServerAlias www.oranges.com
</VirtualHost>
```

## Enable virtual host

Open httpd.conf file

```
$ open -a Atom /Applications/MAMP/conf/apache/httpd.conf
```
or
```
$ open -a Atom /etc/apache2/httpd.conf
```

Add (or uncomment)

```
# Virtual hosts
Include /Applications/MAMP/conf/apache/extra/httpd-vhosts.conf
```

or

```
Include /private/etc/apache2/extra/httpd-vhosts.conf
```

Restart apache

```
$ sudo apachectl restart
```