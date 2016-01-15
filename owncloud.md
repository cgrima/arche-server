Optimization
===

[Memory Caching optimization](https://owncloud.org/blog/making-owncloud-faster-through-caching/)

apt-get update
apt-get install php5-apcu

You need to set ```php.ini``` option ```apc.enable_cli = 1```

Then add ```'memcache.local' => '\OC\Memcache\APCu',``` in ```config.php```

