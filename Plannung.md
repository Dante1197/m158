

### Projektplan für die Migration zu WordPress auf Ubuntu 22.04 mit Proxmox:

**Anleitungen:**

- [YouTube Tutorial](https://www.youtube.com/watch?v=lD6vQBDHkqU&ab_channel=LearnLinuxTV) einer WordPress-Installation mit Virtual Host unter Ubuntu.

- [YouTube Tutorial](https://www.youtube.com/watch?v=t50UfbGvWhw&ab_channel=AkamaiDeveloper) einer FTP-Installation unter Ubuntu.

**Phase 1: Instance Setup on Proxmox (Tag ?)**
- Einrichtung einer neuen virtuellen Maschine auf Proxmox mit Ubuntu Desktop 22.04.
- Konfiguration von Netzwerkeinstellungen und Ressourcen für die virtuelle Maschine.

**Phase 2: Instance Config für Wordpress (Tag ?)**
- Aktualisierung des Ubuntu-Betriebssystems auf dem virtuellen Desktop.
- Installation von grundlegenden Tools und Diensten wie SSH für die Fernverwaltung.

**Phase 3: Apache Installation (Tag ?)**
- Installation des Apache-Webservers auf der Ubuntu-Instanz.
- Konfiguration von Apache, um grundlegende Einstellungen für die Bereitstellung von Webinhalten vorzunehmen.

**Phase 4: Database Setup für Wordpress (Tag ?)**
- Installation und Konfiguration von MariaDB als Datenbankserver auf der Ubuntu-Instanz.
- Erstellung einer leeren Datenbank und eines Datenbankbenutzers für WordPress.
- [Cron Job](https://www.spacerex.co/how-to-automatically-backup-a-mysql-or-mariadb-server-with-mysqldump/) Erstellen

**Phase 5: Download und Installation von WordPress (Tag ?)**
- Herunterladen der neuesten Version von WordPress von der offiziellen Website.
- Extrahieren und Kopieren der WordPress-Dateien in das Webserver-Verzeichnis auf der Ubuntu-Instanz.
- Bereitstellung von Berechtigungen und Konfigurationen für WordPress-Dateien.

**Phase 6: Wordpress Config File zu Apache hinzufügen (Tag ?)**
- Konfiguration von Apache, um das WordPress-Verzeichnis als Web-Root-Verzeichnis zu verwenden.
- Einrichtung von .htaccess-Dateien und anderen erforderlichen Einstellungen für WordPress.

**Phase 7: Install PHP Packages (Tag ?)**
- Installation von PHP und allen erforderlichen PHP-Erweiterungen für WordPress.
- Konfiguration von PHP, um die optimale Leistung für WordPress zu gewährleisten.

**Phase 8: Wordpress Accessing Config / Final Config (Tag ?)**
- Zugriff auf die WordPress-Installationsseite über den Webbrowser zur Durchführung der grundlegenden Konfiguration.
- Konfiguration von WordPress-Grundeinstellungen wie Sprache, Website-Titel, Administratorzugangsdaten usw.

**Phase 9: Web Certificate (Tag ?)**
- Einrichtung von HTTPS-Zertifikaten für die WordPress-Site mit Let's Encrypt oder einem anderen Zertifizierungsanbieter.
- Konfiguration von Apache, um HTTPS für die sichere Kommunikation mit der WordPress-Site zu aktivieren.