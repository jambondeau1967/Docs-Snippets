
code of book = 
https://github.com/leetschau/flask-by-example-notes


update os+packages ubuntu server

```
sudo apt-get apache2
sudo apt-get install libapache2-mod-wsgi-py3
```

console apache server:
```
ifconfig
```
browse to ipaddress --> Apache must show 'It works!'

login via ssh
```
cd /var/www
git clone "repo"
```


/var/www/firstapp/hello.wsgi :
```
import sys
sys.path.insert(0, "/var/www/firstapp")
from hello import app as application
```

```
cd /etc/apache2/sites-available
nano hello.conf
```

```
<VirtualHost *>
    ServerName example.com

    WSGIScriptAlias / /var/www/firstapp/hello.wsgi
    WSGIDaemonProcess hello
    <Directory /var/www/firstapp>
       WSGIProcessGroup hello
       WSGIApplicationGroup %{GLOBAL}
        Order deny,allow
        Allow from all
    </Directory>
</VirtualHost>
```

/var/www/firstapp/hello.wsgi :
```
import sys
sys.path.insert(0, "/var/www/firstapp")
from hello import app as application
```

apache commands to disable/enable sites:
(resident in sites-available folder)
```
sudo a2dissite 000-default.conf
sudo enable a2ensite hello.conf
sudo service apache2 reload
```
inspect apache2 log:
```
sudo tail -f /var/log/apache2/error.log
```

