# Teilaufgabe Schüler Eichelbeger
\textauthor{Tobias Eichelberger}

## Theorie

### Was ist ein Server
Ein Server ist ein Gerät beziehungsweise ein Computer der Ressourcen, Daten oder auch Dienste für Clients bereitstellt. 
https://www.paessler.com/de/it-explained/server

### Was ist Debian
https://www.ionos.at/digitalguide/server/knowhow/debian-die-universelle-system-software/


### Was ist Proxmox
https://www.ionos.at/digitalguide/server/knowhow/proxmox/


### Was ist ein Domaincontroller
In dieser Dokumentation wird erklärt was ein Domaincontroller, kurz DC ist und welche Aufgaben beziehungsweise Funktionen er hat. Auch die Vorteile sowie Nachteile werden behandelt. https://specopssoft.com/de/blog/domaenen-controller/


### Was VPN
Virtuelles Privates Netzwerk oder auch VPN genannt.
https://de.ryte.com/wiki/VPN/
#### Tailscale
https://tailscale.com/kb/1151/what-is-tailscale

### Was ist GNS3
https://docs.gns3.com/docs/



### Was ist eine IDS-System.
In diesem Kapitel wird erlärt was ein IDS-System ist, welche Arten es gibt und warum man ein solch ein System überhaupt verwenden sollte. In dem Artikel wird erläutert was ein ein IDS-System macht und wie sie funktionieren zudem wird auch auf die verschiedenen Arten eingegangen.
https://www.ionos.at/digitalguide/server/sicherheit/intrusion-detection-system-ids/
<br>
Zudem ist wichtig zu erwähnen das solche Systeme zur Überwachung von Netzwerken immer wichtiger und wichtiger werden, mit der fortlaufenden Digitalisierung werden Computernetzwerke, besonders in Unternhemen von bösartigen Hackern angegriffen. Deswegen ist es enorm wichtig sich gegen solche Angriffe so gut es geht zu schützen um im ernstfall einen großen Schaden zu vermeiden.

#### Vergleich zwischen verschieden IDS-Systemen
Um zu entscheiden welchen System in dem Projekt angewendet wird, ist es umso wichtiger zu wissen welche Vor- und Nachteile die Systeme haben. Für diesen Projekt wurden drei bekannte Systeme miteinander verglichen, die unterschiedliche Ansätze verfolgen.

##### Wazuh
Wazuh ist ein open-source System, was bedeutet das man den Quellcode einsehen kann. Zudem ist dieses IDS-System ein HIDS (Hostbasiertes Intrusion-Detection-System), welches es in einer gratis beziehungsweise in einer bezahl Version gibt, weclche verschiedene Modelle je nach größe des Unternehmens anbietet. Das System besteht aus verschieden Komponenten die alle gemeinsame zusammen spielen um vor gefahren zu Warnen. Das Herz des System sind die zentralen Komponenten dem Wazuh-Server und dem Wazuh-Indexer. Der Wazuh-Indexer speichert die Daten die vom Wazuh-Server kommen, der diese vom Wazuh-Agenten, der auf den verschiedenen Endgeräten installiert ist. Die ganzen Informationen werden auf einem Webbasierten Dashboard angezeigt, wo sich der Wazuh-User einloggen kann. Empfohlen wird die Installation von dem Wazuh-Server auf einem Linux Betriebssystem. Weitere Informationen über Wazuh sind auf der Website unter Dokumentationen verfügbar. https://documentation.wazuh.com/current/index.html

##### Snort
Snort ist anders wie Wazuh ein NIDS (Netzwerkbasiertes Intrusion-Detection-System) aber dennoch auch open-source. Auch hier gibt es eine kostenlose Version und eine kommerzielle Version die zu bezahlen ist. Snort funktioniert so das es alle Pakete die in einem Netzwerk hin und her geschickt werden scannt und falls unregelmäsigkeiten oder potenzielle schädliche Pakte gesendet werden alarmschlägt. Dieses System ist quasi ein Packet-Sniffer. Der große Unterschied zu einen HIDS-System, wie Wazuh ist das ich nur auf einem Gerät in meinen Netzwerk Snort installiere, meist ein auf einen Server oder einem extrigen Überwachungsmaschine. Da Snort nur Logs erzeugt und diese speichert gibt es kein direktes dashboard, hierzu benötigt man extrig ein Frontend beziehungsweise eine Visualisierungsplattform. Hier gibt es verschieden Anbieter die solche Dashboards-Tools anbieten.
https://www.snort.org/documents
https://www.zenarmor.com/docs/de/netzwerksicherheitstutorials/was-ist-snort#:~:text=Snort%20untersucht%20den%20Netzwerkverkehr%20in,au%C3%9Ferhalb%20eines%20Netzwerks%20gesendet%20werden.

##### Security Onion
Security Onion ist ebenso wie die anderen zwei Systeme open-source, aber die herangehensweise von Security Onion ist anderes während sich Wazuh und Snort entweder für hostbasiertes oder Netzwerksbasiertes scannen entscheiden, nützt Security Onion beide seiten und kombiniert diese das sogennante Hybride Intrusion-Detection-System. Auch hier gibt es eine kostenlose beziehungsweise eine bezalversion. Das System wird ebenso wie Snort zentral auf einem Server installiert. Für das Netzwerksbasierte scannen verwendet Security Onion im Hintergrund Suricata und für das hostbasierte verwendet es den Elastic Agenten. Die Ereignisse werden auf einen Dashboard angezeigt.
https://docs.securityonion.net/en/2.4/index.html



## Praktische Arbeit
Aufsetzen des Proxmox-Servers
Für die Umsetzung dieses Projekts ist es zunächst wichtig einen Server mit ausreichend Resourcen zu verfügung zu haben. In diesem FAll wurde ein HP ProLiant G7 mit 805 Gigabyte Speicher und 70 Gigabyte Arbeitsspeicher verwendet, zudem ist der Server mit 4 CPU's ausgestattet. Zunächst wurde Debian 12 auf einem PC gedownloadet und mithilfe von belenaEtcher, eine Software mit dem man USB-Sticks bootfähig bekommt, ein USB-Stick mit der ISO-Datei bootfähig und somit einsatzbereit für die installation am server gemacht. Die installation ist wiefolgt zu erledigen: USB-Stick in einen freien USB-Slot am server einstecken und den Server starten, nach dem hochfahren des Servers auswählen das er vom eingesteckten USB-Stick strarten soll. NAch ein paar Sekunden sollte ein Startbildschirm der Installationanleitung von Debian 12 erscheinen. Zunächst kann man der Installationanleitung folgen, wichtig ist hier nur ein root Passwort zu setzen, da es sonst später bei der Installation noch Proxmox zu komplikationen führen kann. Bei der Softwareauswahl ist zu beachten das nur das Standart System angehackt ist. Sollte es nach der Vollendung des Vorgangs und einem Restart einen Fehler geben, liegt dies an dem falsch zugewissenen GRUB Loader, dieser sollte auf einer bootfähigen Festplatte liegen. Hier ist vom Vorteil wenn man nach dem Restart in den Rescue Mode geht der einem Vorgeschlagen wird in mit Hilfe deer Anleitung die richtige Festplatte auswhählt. Wenn alles funktioniert kommt man in die Shell des Debian Systems wo die nächsten Schritte folgen. 
Nun ist es wichtig eine statische IP-Adresse zu setzen ansonsten kommt es zu einem Fehler bei Proxmox. Hierzu mit nano /etc/network/interfaces in das netzwerkinterfaceeinstellungen gehen und bei dem jewiligen Netzwerkadapter das dhcp löschen und an stelle dieser static hinschreiben. Darunter kommt das die IP-Adresse, Netzwerkmaske und das Gateway, wichtig ist das die richtigen Addressen in dem Netzwerk wo sich der Server befindet stimmen ansonsten gibt es schwierigkeiten mit der Interetverbindung. Mit strg + O speichern und danach mit strg + X verlassen. Als nächsten Schritt mit `nano /etc/hosts` in die datei hineingehen und in der ersten Zeile localhost zu localhost.localdomain localhost ändern und in der zweiten Zeile die IP-Adresse zu der richtigen IP-Adresse ändern, die vorhin in der netzwerkinterfaceeinstellungen datei vergeben wurde. Wenn diese einstellungen geändert wurden wieder speichern und verlassen. Anschließend kann man man mit dem Befehl hostname --ip-adress überprüfen ob alles funktioniert hat, wenn hier die richtrige IP-Adresse kommt hat alles funktioniert. Als nächstes mit ifdown + Netzwerkadaptername und ifup + Netzwerkadaptername, die Netzwerkkarteneinstellungen neu laden und anschließend mit `ip a` überprüfen ob die richtige ip-Adresse ausgegeben wird. Nun ist es an der Zeit Proxmox zu installieren, hierzu den Befehl `nano /etc/apt/sources.list.d/pve-install-repo` einegeben und enter drücken. In der Datei angekommen die folgende Zeile einfügen: `deb [arch=amd64] http://download.proxmox.com/debian/pve bullseye pve-no-subscription`. Anschließend wieder speichern und verlassen. Als nächstes mit `wget http://download.proxmox.com/debian/proxmox-release-bullseye.gpg -0 /etc/apt/trusted.gpg.d/proxmox-release-bullseye.gpg` den Proxmox GPG Key herunterladen. Nun mit apt update die Paketlisten aktualisieren und mit apt full upgrade alles nochmal auf den aktuelsten stand updaten bevor man mit apt Proxmox-ve postfix open-iscsi Proxmox installiert. Bevor man Proxmox installiert wird ist es wichtig das postfix konfiguriert wird, hierzu wählt man die option "Internet Site" aus und gibt als Systemmailnamen die Domain des Servers an. Nach der Installation ist es wichtig den Server neu zu starten, bevor man das macht den Befehl apt remove os-prober ausführen um die Sicherheit und Vermeidung von Fehlern des Systems vorzubeugen dannach mit reboot den server neustarten. Nun sollte man wenn man die Bootreihenfolge richtig eingestellt hat in den Proxmox VE Bootmanager kommen. Als nächstes ist es wichtig sich mit einem anderen PC in das Webinterface von Proxmox zu verbinden hierzu die IP-Adresse des Servers in die Adresszeile des Browsers eingeben gefolgt von `:8006` also z.B. `https://10.0.0.209:8006`. Nun sollte ein Sicherheitswarnung kommen diese kann man ignorieren und auf "Erweitert" und dann auf "Trotzdem fortfahren" klicken. Nun sollte das Proxmox Login Fenster erscheinen, hier gibt man als Benutzernamen root und als Passwort das root Passwort ein was man bei der Installation von Debian 12 gesetzt hat. Wichtig ist hier noch zu beachten das man bei Domaine Linux PAM standard authentication ausgwwählt hat, sonst gibt es einen Fehler bei der Anmeldung. Nun noch auf Anmelden klicken. Nun ist man im Proxmox Webinterface angekommen und kann mit der Konfiguration beginnen. Nun sollte man als erstes den Proxmox Server updaten hierzu auf den Reiter "Datacenter" klicken und dann auf "Updates" anschließend auf "Refresh" klicken um die Paketlisten zu aktualisieren. Wenn dies erledigt ist auf "Upgrade" klicken um alle Pakete auf den neusten Stand zu bringen. Nachdem der Update Vorgang abgeschlossen ist sollte man den Server neustarten, hierzu auf den Reiter des erstellten Node klicken und dann auf "Reboot" klicken. Nun ist der Proxmox Server erfolgreich installiert und auf dem neusten Stand. Der nächste Schritt ist es einen virtuellen Switch zu erstellen um die virtuellen Maschinen miteinander zu verbinden hierzu auf den Reiter des erstellten Node klicken und dann auf "Network" anschließend auf "Erstellen" und dann auf "Linux Bridge" klicken. In dem neuen Fenster einen Namen für den Switch vergeben z.B. vmbr1 und bei "Bridge ports" den Netzwerkadapter eingeben der mit dem Netzwerk verbunden ist z.B. eth0. Anschließend auf "Erstellen" klicken um den Switch zu erstellen. Nun ist der virtuelle Switch erstellt und kann für die virtuellen Maschinen verwendet werden. Nun Wäre der Proxmox Server bereit für die Installation der virtuellen Maschinen.

### Einrichten des Tailscale VPNs
Um das Tailscale VPN auf dem Proxmox Server einzurichten, sind folgende Schritte notwendig:
1. Zunächst muss das Tailscale Repository hinzugefügt werden. Hierzu wird in der Shell, die man in Proxmox unter dem erstelltem Node neben dem Herunterfahren Button erreichen kann der Befehl `curl -fsSL https://tailscale.com/install.sh | sh` verwendet.
2. Anschließend wird Tailscale mit dem Befehl `apt-get install tailscale` installiert.
3. Nach der Installation wird Tailscale mit dem Befehl `tailscale up` gestartet. Hierbei wird ein Authentifizierungslink generiert, der in einem Browser geöffnet werden muss, um den Server mit dem Tailscale Netzwerk zu verbinden.
4. Nach der erfolgreichen Authentifizierung ist der Proxmox Server mit dem Tailscale Netzwerk verbunden und kann über die Tailscale IP-Adresse erreicht werden.
5. Um die Verbindung zu überprüfen, kann der Befehl `tailscale status` verwendet werden, der den aktuellen Status der Tailscale Verbindung anzeigt.
6. Abschließend sollte Tailscale so konfiguriert werden, dass es beim Systemstart automatisch gestartet wird. Dies kann mit dem Befehl `systemctl enable tailscaled` erreicht werden.
Nun ist das Tailscale VPN erfolgreich auf dem Proxmox Server eingerichtet und kann für die Verbindung der virtuellen Maschinen verwendet werden.

### Einrichten der User des Proxmox Servers
Um die User auf dem Proxmox Server einzurichten, sind folgende Schritte notwendig:
1. Zunächst sollte man unter dem Reiter "Datacenter" auf "Permissions" und dann auf "Rollen" klicken.
2. In dem neuen Fenster auf "Add" klicken um eine neue Rolle zu erstellen. Hierbei einen Namen für die Rolle vergeben, z.B. "NurVMsSehen" und die gewünschten Berechtigungen auswählen, z.B. "PVEAuditor und VM.Console". Anschließend auf "Add" klicken um die Rolle zu erstellen.
3. Als nächstes auf den Reiter "Gruppen" klicken und dann auf "Add" klicken um eine neue Gruppe zu erstellen. Hierbei einen Namen für die Gruppe vergeben, z.B. "VMUser" und die zuvor erstellte Rolle auswählen. Anschließend auf "Add" klicken um die Gruppe zu erstellen.
4. Nun auf den Reiter "Benutzer" klicken und dann auf "Add" klicken um einen neuen Benutzer zu erstellen. Hierbei einen Benutzernamen, Passwort und die zuvor erstellte Gruppe auswählen. Anschließend auf "Add" klicken um den Benutzer zu erstellen.
Nun sind die User auf dem Proxmox Server erfolgreich eingerichtet und können sich mit ihren Zugangsdaten anmelden. Wichtig ist hier zu beachten das die User nur die Berechtigungen haben die in der Rolle definiert wurden. Somit ist es möglich verschiedene Benutzer mit unterschiedlichen Berechtigungen zu erstellen um die Sicherheit des Servers zu erhöhen. Somit können die Schüler sich mit ihren eigenen Zugangsdaten anmelden und die virtuellen Maschinen verwalten ohne Zugriff auf den gesamten Proxmox Server zu haben und nichts umstellen können. 
### Einrichten des GNS3 Servers
Um den GNS3 Server auf dem Proxmox Server einzurichten, sind folgende Schritte notwendig:
Bevor man mit der Installation des GNS3 Servers beginnt, ist es notwendig sich von der offizellen GNS3 Website das GNS3 VM Image herunterzuladen. Dieses Image ist eine vorgefertigte virtuelle Maschine, die speziell für die Verwendung mit GNS3 optimiert ist. Das Image kann unter folgendem Link heruntergeladen werden: https://gns3.com/software/download-vm
Nachdem das Image auf dem PC heruntergeladen wurde, muss es in das Proxmox Webinterface hochgeladen werden. Hierzu unter dem erstellten Node auf den Reiter "Storage" klicken und dann auf "Content" anschließend auf "Upload" klicken. In dem neuen Fenster die heruntergeladene GNS3 VM Image Datei auswählen und auf "Upload" klicken um die Datei in Proxmox hochzuladen.
Nachdem das Image erfolgreich hochgeladen wurde, kann mit der Erstellung der virtuellen Maschine für den GNS3 Server begonnen werden. Hierzu sind folgende Schritte notwendig:
1. Unter dem erstellten Node auf "Create VM" klicken.
2. In dem neuen Fenster einen Namen für die virtuelle Maschine vergeben, z.B. "GNS3-Server".
3. Auf den Reiter "OS" klicken und bei "Use CD/DVD disc image file (iso)" die Option "Do not use any media" auswählen.
4. Auf den Reiter "System" klicken und bei "BIOS" die Option "OVMF (UEFI)" auswählen.
5. Auf den Reiter "Hard Disk" klicken und bei "Bus/Device" die Option "SCSI" auswählen. Anschließend bei "Storage" das hochgeladene GNS3 VM Image auswählen.
6. Auf den Reiter "CPU" klicken und die Anzahl der CPU-Kerne festlegen, z.B. 2 Kerne.
7. Auf den Reiter "Memory" klicken und die Menge des Arbeitsspeichers festlegen, z.B. 4096 MB.
8. Auf den Reiter "Network" klicken und bei "Bridge" den zuvor erstellten virtuellen Switch auswählen, z.B. "vmbr1".
9. Abschließend auf "Finish" klicken um die virtuelle Maschine zu erstellen.
Nachdem die virtuelle Maschine erstellt wurde, kann sie gestartet werden. Hierzu unter dem erstellten Node auf die virtuelle Maschine klicken und dann auf "Start" klicken. Anschließend auf "Console" klicken um die Konsole der virtuellen Maschine zu öffnen.
In der Konsole angekommen, muss der GNS3 Server konfiguriert werden. Hierzu sind folgende Schritte notwendig:
1. Zunächst muss das Standardpasswort für den Benutzer "gns3" geändert werden. Hierzu den Befehl `passwd` eingeben und das neue Passwort festlegen.
2. Anschließend muss die Netzwerkkonfiguration überprüft werden. Hierzu den Befehl `ip a` eingeben um die aktuellen Netzwerkeinstellungen anzuzeigen. Falls notwendig, können die Netzwerkeinstellungen angepasst werden.
Nun ist der GNS3 Server erfolgreich auf dem Proxmox Server eingerichtet und kann über das GNS3 Client auf einem anderen PC erreicht werden. Hierzu in dem GNS3 Client unter "Edit" auf "Preferences" klicken und dann auf "GNS3 Server" anschließend die Tailscale IP-Adresse des Proxmox Servers eingeben und auf "Test Connection" klicken um die Verbindung zu überprüfen. Wenn die Verbindung erfolgreich ist, kann der GNS3 Server verwendet werden. Nun können in GNS3 verschiedene Netzwerktopologien erstellt und getestet werden.
