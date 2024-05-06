## Erfolgreiche Installation und Konfiguration eines Datenbankservers auf Linux

Ein Datenbanksystem wurde erfolgreich auf Linux installiert und konfiguriert. Zusammen mit Apache2 und einigen PHP-Modulen haben wir über `apt` den MySQL-Server (MariaDB) installiert.

```bash
sudo apt install apache2 ghostscript libapache2-mod-php mysql-server php php-bcmath php-curl php-imagick php-intl php-json php-mbstring php-mysql php-xml php-zip
```

Die Konfiguration der Datenbank erfolgte wie folgt (die Informationen wurden aus der Datei "wp-config.php" im Export des Legacy-Servers entnommen):

```bash
sudo mysql -u root

CREATE DATABASE wp_m158_db;
CREATE USER wp_m158_user@localhost IDENTIFIED BY '0Cc6j_6otBljfdfG';
GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,ALTER
    -> ON wp_m158_db.*
    -> TO wp_m158_user@localhost; 
FLUSH PRIVILEGES;

systemctl restart mysql
```

Diese Informationen müssen später während der Konfiguration der WordPress-Installation über das Webinterface angegeben werden.

## Migration der Datenbank von der Quellinstallation

Mittels des Plugins All-in-One WP Migration konnten wir auf dem Legacy-Server die gesamte Datenbank sowie alle WordPress-Konfigurationen und Einstellungen exportieren. Mit demselben Plugin konnten wir auf dem Zielserver, nachdem eine Standardinstallation von WordPress durchgeführt wurde, die Daten importieren. Im Hintergrund sorgte das Plugin dafür, dass die Domain sämtlicher Links entsprechend unserer Domain angepasst wurden.

## Erstellung neuer Datenbankbenutzer und Vergabe entsprechender Berechtigungen

Siehe Abschnitt "Erfolgreiche Installation und Konfiguration eines Datenbankservers auf Linux".