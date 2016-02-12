## hackulus - Flask app for serving shell through the browser

#### Dependencies

  Upon installation, hackulus will install the following Python modules: [ *flask* ]

#### Installation

```
user@localhost:~$ sudo pip3 install hackulus
```

#### Running server

"hackulus" command will start a service in debug mode at localhost:8000

```
user@localhost:~$ hackulus
```

To serve the application behind Apache via mod_wsgi, create a new virtualhost directive in the Apache config.

Example: /etc/apache2/sites-available/hackulus.conf

```
<VirtualHost *:8000>
	ServerName hackulus
	ServerAdmin jungkumseok@gmail.com
	
	WSGIDaemonProcess hackulus python-path=/usr/local/lib/python3.4/dist-packages/hackulus
	WSGIScriptAlias / /usr/local/lib/python3.4/dist-packages/hackulus/hackulus.wsgi
	WSGIProcessGroup hackulus
	<Directory /usr/local/lib/python3.4/dist-packages/hackulus>
		Require all granted
	</Directory>
	ErrorLog ${APACHE_LOG_DIR}/hackulus-error.log
        CustomLog ${APACHE_LOG_DIR}/hackulus-access.log combined
</VirtualHost>
```

If you haven't already, also run

```
user@localhost:~$ sudo a2ensite hackulus
user@localhost:~$ sudo a2enmod wsgi
```
 
    
#### Enjoy :)