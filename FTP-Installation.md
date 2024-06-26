# FTP-Installation Dokumentation

1. Update your maschine
```bash
sudo apt update
```
2. Install VSFTP Packages
```bash
sudo apt install vsftpd ftp ufw
```
3. Check status of FTP-Server
```bash
systemctl status vsftpd
```
4. Enable the FTP-Service
```bash
sudo systemctl enable vsftpd
```
5. Start the FTP-Service
```bash
sudo systemctl start vsftpd
```
6. Create FTP-User
```bash
sudo useradd -m williams
sudo passwd williams
```
7. Test file
```bash
sudo -u williams sh -c 'echo "This is the content in the file."
> /home/williams/testfile.txt'
```
8. Test the Server
```bash
ftp localhost
william
ls /home/williams
```
9. Restart the Server
```bash
sudo systemctl restart vsftpd
systemctl status vsftpd #to check if he restartet
```
10. Backup VSFTP-config 
```bash
ls -l /etc/vsftpd.conf
sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.bak
sudo nano /etc/vsftpd.conf
sudo systemctl restart vsftp
```
edit the config just like in the Screenshot: 
![image](https://github.com/Dante1197/m158/assets/111874433/c121d9ff-62d9-40b0-96cd-21f35cd40bb6)

11. Restart the FTP-Server
```bash
sudo systemctl restart vsftp
sudo systemctl status vsftp
```

12. Download a File
```bash
ftp localhost
cd /home/ftp_client
get testfile.txt
exit
```

13. Upload a file
```bash
cd /tmp
echo "This is sample content for uploading through FTP." > test file2.txt
```
```bash
ftp localhost 
Password:
put testfile2.txt
exit
```

14. External Access (Firewall)
```bash
sudo ufw allow ssh
sudo ufw allow from any to any port 20,21 proto tcp
sudo ufw enable
```
![](Images/image-1.png)

![](Images/Ftp.png)

---


# FTP-Installation Dokumentation

1. Update deinen Computer
   ```bash
   sudo apt update
   ```

2. Installiere VSFTP-Pakete
   ```bash
   sudo apt install vsftpd ftp ufw
   ```

3. Überprüfe den Status des FTP-Servers
   ```bash
   systemctl status vsftpd
   ```

4. Aktiviere den FTP-Dienst
   ```bash
   sudo systemctl enable vsftpd
   ```

5. Starte den FTP-Dienst
   ```bash
   sudo systemctl start vsftpd
   ```

6. Erstelle einen FTP-Benutzer
   ```bash
   sudo useradd -m williams
   sudo passwd williams
   ```

7. Testdatei erstellen
   ```bash
   sudo -u williams sh -c 'echo "Dies ist der Inhalt der Datei." > /home/williams/testfile.txt'
   ```

8. Teste den Server
   ```bash
   ftp localhost
   william
   ls /home/williams
   ```

9. Server neu starten
   ```bash
   sudo systemctl restart vsftpd
   systemctl status vsftpd # zur Überprüfung des Neustarts
   ```

10. Sicherung der VSFTP-Konfiguration
    ```bash
    ls -l /etc/vsftpd.conf
    sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.bak
    sudo nano /etc/vsftpd.conf
    sudo systemctl restart vsftp
    ```
    Bearbeite die Konfiguration wie im Screenshot:
    ![image](https://github.com/Dante1197/m158/assets/111874433/c121d9ff-62d9-40b0-96cd-21f35cd40bb6)

11. FTP-Server neu starten
    ```bash
    sudo systemctl restart vsftp
    sudo systemctl status vsftp
    ```

12. Datei herunterladen
    ```bash
    ftp localhost
    cd /home/ftp_client
    get testfile.txt
    exit
    ```

13. Datei hochladen
    ```bash
    cd /tmp
    echo "Dies ist ein Beispielinhalt zum Hochladen über FTP." > testfile2.txt
    ```
    ```bash
    ftp localhost 
    Passwort:
    put testfile2.txt
    exit
    ```

14. Externer Zugriff (Firewall)
    ```bash
    sudo ufw allow ssh
    sudo ufw allow from any to any port 20,21 proto tcp
    sudo ufw enable
    ```

![](Images/image-1.png)