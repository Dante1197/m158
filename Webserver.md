## Einrichtung eines Webservers

Wir haben uns für Apache2 als Webserver entschieden und bereits einige Pakete, einschließlich Apache2, unter Punkt "Ein Datenbankserver wurde auf Linux erfolgreich installiert und konfiguriert", installiert. Mit den folgenden Befehlen haben wir einen Ordner `/srv/www` erstellt und die Standard-WordPress-Installation an diesem Speicherort abgelegt:

```bash
sudo mkdir -p /srv/www
sudo chown www-data: /srv/www
curl https://wordpress.org/latest.tar.gz | sudo -u www-data tar zx -C /srv/www
```

Eine neue vhost-Datei namens `wordpress.conf` wurde im Verzeichnis `/etc/apache2/sites-available/` erstellt. Darin haben wir unsere Domain definiert, um später über HTTP auf WordPress zugreifen zu können. Als `DocumentRoot` haben wir `/srv/www/wordpress` festgelegt, wo wir WordPress installieren werden.

```apache
<VirtualHost *:80>
    ServerName wp-toor.m158.etlas.one
    ServerAlias ipv6.wp-toor.m158.etlas.one
    DocumentRoot /srv/www/wordpress
    <Directory /srv/www/wordpress>
        Options FollowSymLinks
        AllowOverride Limit Options FileInfo
        DirectoryIndex index.php
        Require all granted
    </Directory>
    <Directory /srv/www/wordpress/wp-content>
        Options FollowSymLinks
        Require all granted
    </Directory>
</VirtualHost>
```

Durch den Befehl `sudo a2ensite wordpress` wurde die Webseite aktiviert. Nun konnte über den Aufruf unserer Domain mit dem WordPress Wizard eine Standardinstallation durchgeführt werden. Die genaue Konfiguration spielt hier vorerst keine große Rolle, da sie später durch das Plugin (Migration der Datenbank von der Quellinstallation) ersetzt wird.

Um den Upload der Exportdatei von unserem Legacy-Server auf unseren neuen Server zu ermöglichen, mussten einige Konfigurationen für die maximale Upload-Größe angepasst werden. Sobald dies erfolgt ist, kann die Sicherungsdatei vom Legacy-Server auf den neuen Server hochgeladen werden, und das Plugin erledigt sämtliche Migrationsarbeiten.

In der `.htaccess`-Datei:

```apache
php_value upload_max_filesize 512M
php_value post_max_size 512M
php_value memory_limit 512M
php_value max_execution_time 300
php_value max_input_time 300
```

In der `wp-config.php`-Datei:

```php
@ini_set( 'upload_max_filesize' , '512M' );
@ini_set( 'post_max_size', '512M');
@ini_set( 'memory_limit', '512M' );
@ini_set( 'max_execution_time', '300' );
@ini_set( 'max_input_time', '300' );
```

![htaccess](Images/htaccess.png)

## Webserver läuft unter einem virtuellen Host Ihrer Wahl

Unter Apache2 wird immer auf "virtuelle Hosts" bzw. "vhosts" zurückgegriffen. Im Ordner `/etc/apache2/sites-available/` legen wir `.conf`-Dateien ab, in denen wir für unseren Webserver mehrere Domains und jeweils eigene Root-Verzeichnisse definieren können. Aktuell finden sich auf unserem Webserver zwei vhost-Dateien: eine für unsere WordPress-Seite unter Port 80 via HTTP und eine für dieselbe WordPress-Seite unter derselben Domain, jedoch unter Port 443 und somit erreichbar via HTTPS.

## Umleitung von HTTP auf HTTPS mit einem selbst signierten Zertifikat

Anstelle eines selbst signierten Zertifikats wurde ein Zertifikat verwendet, das automatisch von Let's Encrypt ausgestellt wurde (siehe Punkt "Website ist mit TLS-Zertifikat von Let's Encrypt ausgestattet"). In der Virtual Host-Datei für WordPress unter Apache2 (`/etc/apache2/sites-available/wordpress.conf`) legen wir die Domains fest, unter denen unsere WordPress-Seite erreichbar sein soll, sowie auch als Alias unsere ipv6-only Domain. Certbot wird nach der Erstellung des TLS-Zertifikats automatisch eine Weiterleitung von HTTP auf HTTPS einrichten. Dies könnte auch manuell erfolgen (ebenfalls in dieser `wordpress.conf`-Datei).