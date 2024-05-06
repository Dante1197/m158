## Es wurde PHP installiert und aktiviert
Wir haben PHP 8.2 aus den Standard-Ubuntu-Packetquellen installiert und entsporechend unter Apache2 auch enabled:

sudo apt install php8.2 
sudo apt install php8.2-mysql php8.2-bcmath php8.2-curl php8.2-imagick php8.2-dom php8.2-zip php8.2-intl
a2dismod php8.1
sudo a2enmod php8.2




## Es wird min. PHP Version 8.2 eingesetzt
siehe Abschnitt zur PHP Installation

## phpmyadmin

![](Images/phpmyadmin.png)