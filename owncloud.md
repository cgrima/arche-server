#### Memory Cache Optimization Optimization

[Memory Caching optimization](https://owncloud.org/blog/making-owncloud-faster-through-caching/)

```sh
apt-get update
apt-get install php5-apcu
```
You need to set `php.ini` option `apc.enable_cli = 1`
Then add `'memcache.local' => '\OC\Memcache\APCu',` in `config.php`

#### ocDownloader

```sh
apt-get install aria2 curl php5-curl
aria2c --enable-rpc --rpc-allow-origin-all -c -D --log=/var/log/aria2.log --check-certificate=false
```

#### News

```sh
apt-get install vim cron
crontab -u www-data -e
*/15  *  *  *  * php -f /var/www/html/cron.php > /dev/null 2>&1
```

#### X-XSS-Protection


If the following message is displayed in the admin settings
```sh
The "X-XSS-Protection" HTTP header is not configured to equal to "1; mode=block". This is a potential security or privacy risk and we recommend adjusting this setting.
```
do
```sh
a2enmod env
a2enmod headers
```
Restart container

#### LibreOffice Online


In the container, download the libreoffice online repo
```sh
apt-get install git
cd /var/www/html
git clone https://github.com/libreoffice/online
```

install dependencies
```sh
apt-get install libreoffice libpng-dev libpoco-dev libcap-dev libcppunit-dev nodejs npm automake
```

Install Poco
```
cd /var/www/html
git clone https://github.com/pocoproject/poco.git
cd poco
./configure
make
make install
```

Compile loolwsd
```sh
cd /var/www/html/online/loolwsd/
MASTER=/var/www/html/online/loolwsd/bundled/
automake --add-missing
autoreconf
./configure --enable-silent-rules --with-lokit-path=${MASTER}/include --with-poco-includes=/user/include/Poco --with-poco-libs=/usr/include/Poco
```

Compile loleaflet
```sh
cd /var/www/html/online/loleaflet/
npm install -g jake
npm install
```

Compile loolwsd
