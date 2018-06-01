# php-71-migration
#Sparehire PHP 5.6 to PHP 7.1 migration

## Default extensions:
calendar
Core
ctype
date
exif
fileinfo
filter
ftp
gettext
hash
iconv
imagick
json
libxml
openssl
pcntl
pcre
Phar
posix
readline
Reflection
session
shmop
SimpleXML
sockets
sodium
SPL
standard
sysvmsg
sysvsem
sysvshm
tokenizer
wddx
xml
xmlreader
xmlwriter
xsl
Zend OPcache
zlib

## Required extensions for SH
curl		php71-curl
dom		php71-dom
gd		php71-gd
imagick		php71-imagick
json		php71-json
mbstring	php71-mbstring
mysql		php71-mysql
pdo		php71-pdo
pdo_mysql*	
pecl_memcached	php71-pecl-imagick -y

## Instalation guide
In order to have both php 5.6 and 7.1 in the same environment:
- After installing php7.1 and extensions
- Run `update-alternatives --set php /usr/bin/php7.1` (advise to keep php 5.6 around in case of necessary rollback)
- Update apache:
	- Run `a2dismod php5.6`;
	- Run `a2enmod php7.1`;
	- Run `service apache2 restart`.
- That should be it!

## Troubleshooting:
PHP 7.1 should run smooth if all required extensions are enabled. In case any unusual extension comes up, we can see if there are missing extensions with the following steps:
	- Run `php -m` to list all extensions and browse the current list of extensions;
	- Use next step instructions to rollback to php5.6;
	- Run `php -m` again to see the current installed extensions and compare both lists.

- You can always rollback the installation to PHP5.6 with:
	- Run `update-alternatives --set php /usr/bin/php5.6` (advise to keep php 5.6 around in case of necessary rollback)
	- Update apache:
		- Run `a2dismod php7.1`
		- Run `a2enmod php5.6`
		- Run `service apache2 restart`

## Remarks
Those procedures were tested in Ubuntu 16.4 environment and some commands might vary in AmazonLinux CentOS. One difference notable is the php libs notation. In Ubuntu we use php5.6-* and Amazon php56-* that 
 
