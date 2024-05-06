## Ein Datenbankserver wurde auf Linux erfolgreich installiert und konfiguriert
Zusammen mit dem apache2 sowie einigen PHP Modulen haben wir via apt mysql-server (mariadb) installiert.

sudo apt install apache2 ghostscript libapache2-mod-php mysql-server php php-bcmath php-curl php-imagick php-intl php-json php-mbstring php-mysql php-xml php-zip


Folgendermassen haben wir dann die Datenbank konfiguriert (die Angaben konnten wir der Datei "wp-config.php", welche im Export des Legacy-Servers enthalten war):

sudo mysql -u root



CREATE DATABASE wp_m158_db;
CREATE USER wp_m158_user@localhost IDENTIFIED BY '0Cc6j_6otBljfdfG';
GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,ALTER
    -> ON wp_m158_db.*
    -> TO wp_m158_user@localhost; 
FLUSH PRIVILEGES;



systemctl restart mysql


Diese Angaben müssen später beim Konfigurieren der WordPress-Installation über das Webinterface angegeben werden.

## Die Datenbank von der Quellinstallation wurde migriert

Mittels dem Plugin All-in-One WP Migration konnte auf dem Legacy Server die gesamte Datenbank sowie alle Wordbress Konfigurationen und Einstellungen exportiert werden. Via dem selben Plugin konnten wir auf dem Zielserver, nachdem eine Standard-Installation von Wordpress erfolgt ist, die Daten einlesen. Im Hindergrund sorgte das Plugin dafür, dass die Domäne sämtlicher Links entsprechend unserer Domain angepasst wurden.

## Es wurden neuen Datenbankbenutzer angelegt und entsprechende Berechtigungen vergeben
siehe Ein Datenbankserver wurde auf Linux erfolgreich installiert und konfiguriert