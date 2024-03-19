# Tailscale Installation 

1. Pfsense Firewall installieren & configurieren in unserem fall haben wir ein **WAN** netz und ein **LAN** netz 
- Wan = DHCP 
- LAN = 192.168.11.18/24 (Subnet 11 ist unseres)

2. Auf das Webgui anmelden (IP-adresse)
3. Unter **System** --> **Package Manager** --> **Availiable Packages** --> nach **Tailscale** suchen --> **Install** --> **Confirm**
4. Danach gehst du unter **VPN** --> **Tailscale** --> **Settings** (Siehe Screenshot) ![](Tailscaleconfig.png)
5. Wir navigieren auf die [Tailscale webseite](https://tailscale.com/download) und Downloaden es für Windows
6. anmelden unten-rechts tailscale app
7. auf die admin-console gehen 
8. auth key generieren 
9. im tailscale hinterlegen 
10. subnet zulassen auf tailscale 