Memory Cache Optimization Optimization
===

[Memory Caching optimization](https://owncloud.org/blog/making-owncloud-faster-through-caching/)

apt-get update
apt-get install php5-apcu

You need to set ```php.ini``` option ```apc.enable_cli = 1```

Then add ```'memcache.local' => '\OC\Memcache\APCu',``` in ```config.php```


X-XSS-Protection
===

If the following message is displayed in the admin settings

'''
The "X-XSS-Protection" HTTP header is not configured to equal to "1; mode=block". This is a potential security or privacy risk and we recommend adjusting this setting.
'''

do
'''
a2enmod env
a2enmod headers
'''
Restart container


LibreOffice Online
===

In the container, download the libreoffice online repo

'''
apt-get install git
cd /var/www/html
git clone https://github.com/libreoffice/online
'''

install dependencies
'''
apt-get install libreoffice libpng-dev libpoco-dev libcap-dev libcppunit-dev automake
'''

Compile loolwsd
'''
cd /var/www/html/online/loolwsd/
'''

Compile loleaflet
'''
cd /var/www/html/online/loleaflet/
MASTER=/var/www/html/online/loolwsd/bundled/
automake --add-missing
autoreconf
./configure --enable-silent-rules --with-lokit-path=${MASTER}/include --with-poco-includes=/user/include/Poco --with-poco-libs=/usr/include/Poco

'''

Compile loolwsd
