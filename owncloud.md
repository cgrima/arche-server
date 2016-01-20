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
