# Item Catalog Application at Amazon Lightsail

## Server Configuration

IP Address: 34.201.136.104
Application Address: http://34.201.136.104/catalog
SSH port: 2200
HTTP port: 80

##Installed Softwares

Virtualenv
SQLAlchemy
Flask
Psycopg2 (PostgresSQL)
Apache2

## Configurations

- Generate a private/public key via ssh-keygen.
- SSH port changed from 22 to 2200.
- Create a 'grader' user and granted sudo access.
- Enable ufw firewall to accept just connections from 80(HTTP), 2200(SSH) and 123(NTP).
- Time was setted to UTC.
- Changed original database (SQLite) to PostgresSQL.
- Configurate Apache and mod_wsgi.

## catalog.conf

<VirtualHost *:80>
                ServerName 34.201.136.104
                ServerAdmin cassioafonso@gmail.com
                WSGIScriptAlias /catalog /var/www/catalog/catalog.wsgi
                <Directory /var/www/catalog/catalog/>
                        Order allow,deny
                        Allow from all
                </Directory>
                Alias /static /var/www/catalog/catalog/static
                <Directory /var/www/catalog/catalog/static/>
                        Order allow,deny
                        Allow from all
                </Directory>
                ErrorLog ${APACHE_LOG_DIR}/error.log
                LogLevel warn
                CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>


## catalog.wsgi

<VirtualHost *:80>
                ServerName 34.201.136.104
                ServerAdmin cassioafonso@gmail.com
                WSGIScriptAlias /catalog /var/www/catalog/catalog.wsgi
                <Directory /var/www/catalog/catalog/>
                        Order allow,deny
                        Allow from all
                </Directory>
                Alias /static /var/www/catalog/catalog/static
                <Directory /var/www/catalog/catalog/static/>
                        Order allow,deny
                        Allow from all
                </Directory>
                ErrorLog ${APACHE_LOG_DIR}/error.log
                LogLevel warn
                CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

## References

- How to configure mod_wsgi (http://flask.pocoo.org/docs/0.12/deploying/mod_wsgi/#configuring-apache)
- Deploy Flask Application with Apache (http://www.devfuria.com.br/python/flask-apache/)
