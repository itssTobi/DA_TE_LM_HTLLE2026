# Teilaufgabe Schüler Eichelbeger
\textauthor{Tobias Eichelbeger}

## Theorie

* Was ist ein Server.
* Was ist Debian.
* Was ist Proxmox.
* Was ist Tailscale.
* Was ist ein Domaincontroller
### Was ist eine IDS-System.
In diesem Kapitel wird erlärt was ein IDS-System ist, welche Arten es gibt und warum man ein solch ein System überhaupt verwenden sollte.
In dem Artikel wird genau erläutert was ein solch ein System macht und wie sie funktionieren zudem wird auch die die verschiedenen Arten eingegangen.
https://www.ionos.at/digitalguide/server/sicherheit/intrusion-detection-system-ids/
<br>
Zudem ist wichtig zu erwähnen das solche Systeme zur Überwachung von Netzwerken immer wichtiger und wichtiger werden, mit der fortlaufenden Digitalisierung werden Computernetzwerke, besonders in Unternhemen von bösartigen Hackern angegriffen. Deswegen ist es enorm wichtig sich gegen solche Angriffe so gut es geht zu schützen um im ernstfall einen großen Schaden zu vermeiden.

### Vergleich zwischen verschieden IDS-Systemen
Um zu entscheiden welchen System in dem Projekt angewendet wird, ist es umso wichtiger zu wissen welche Vor- und Nachteile die Systeme haben. Für diesen Projekt wurden drei bekannte Systeme miteinander verglichen, die unterschiedliche Ansätze verfolgen.
* Wazuh
* Snort
* Security Onion

#### Wazuh
Wazuh ist ein open-source System, was bedeutet das man den Quellcode einsehen kann. Zudem ist dieses IDS-System ein HIDS (Hostbasiertes Intrusion-Detection-System), welches es in einer gratis beziehungsweise in einer bezahl Version gibt, weclche verschiedene Modelle je nach größe des Unternehmens anbietet. Das System besteht aus verschieden Komponenten die alle gemeinsame zusammen spielen um vor gefahren zu Warnen. Das Herz des System sind die zentralen Komponenten dem Wazuh-Server und dem Wazuh-Indexer. Der Wazuh-Indexer speichert die Daten die vom Wazuh-Server kommen, der diese vom Wazuh-Agenten, der auf den verschiedenen Endgeräten installiert ist. Die ganzen Informationen werden auf einem Webbasierten Dashboard angezeigt, wo sich der Wazuh-User einloggen kann. Empfohlen wird die Installation von dem Wazuh-Server auf einem Linux Betriebssystem. Weitere Informationen über Wazuh sind auf der Website unter Dokumentationen verfügbar. https://documentation.wazuh.com/current/index.html

#### Snort
Snort ist anders wie Wazuh ein NIDS (Netzwerkbasiertes Intrusion-Detection-System) aber dennoch auch open-source. Auch hier gibt es eine kostenlose Version und eine kommerzielle Version die zu bezahlen ist. Snort funktioniert so das es alle Pakete die in einem Netzwerk hin und her geschickt werden scannt und falls unregelmäsigkeiten oder potenzielle schädliche Pakte gesendet werden alarmschlägt. Dieses System ist quasi ein Packet-Sniffer. Der große Unterschied zu einen HIDS-System, wie Wazuh ist das ich nur auf einem Gerät in meinen Netzwerk Snort installiere, meist ein auf einen Server oder einem extrigen Überwachungsmaschine. Da Snort nur Logs erzeugt und diese speichert gibt es kein direktes dashboard, hierzu benötigt man extrig ein Frontend beziehungsweise eine Visualisierungsplattform. Hier gibt es verschieden Anbieter die solche Dashboards-Tools anbieten.
https://www.snort.org/documents
https://www.zenarmor.com/docs/de/netzwerksicherheitstutorials/was-ist-snort#:~:text=Snort%20untersucht%20den%20Netzwerkverkehr%20in,au%C3%9Ferhalb%20eines%20Netzwerks%20gesendet%20werden.

#### Security Onion
Security Onion ist ebenso wie die anderen zwei Systeme open-source, aber die herangehensweise von Security Onion ist anderes während sich Wazuh und Snort entweder für hostbasiertes oder Netzwerksbasiertes scannen entscheiden, nützt Security Onion beide seiten und kombiniert diese das sogennante Hybride Intrusion-Detection-System. Auch hier gibt es eine kostenlose beziehungsweise eine bezalversion. Das System wird ebenso wie Snort zentral auf einem Server installiert. Für das Netzwerksbasierte scannen verwendet Security Onion im Hintergrund Suricata und für das hostbasierte verwendet es den Elastic Agenten. Die Ereignisse werden auf einen Dashboard angezeigt.
https://docs.securityonion.net/en/2.4/index.html



## Praktische Arbeit
Aufsetzen des Proxmox-Servers
Für die Umsetzung dieses Projekts ist es zunächst wichtig einen Server mit ausreichend Resourcen zu verfügung zu haben. In diesem FAll wurde ein HP ProLiant G7 mit 805 Gigabyte Speicher und 70 Gigabyte Arbeitsspeicher verwendet, zudem ist der Server mit 4 CPU's ausgestattet. Zunächst wurde Debian 12 auf einem PC gedownloadet und mithilfe von belenaEtcher, eine Software mit dem man USB-Sticks bootfähig bekommt, ein USB-Stick mit der ISO-Datei bootfähig und somit einsatzbereit für die installation am server gemacht. Die installation ist wiefolgt zu erledigen: USB-Stick in einen freien USB-Slot am server einstecken und den Server starten, nach dem hochfahren des Servers auswählen das er vom eingesteckten USB-Stick strarten soll. NAch ein paar Sekunden sollte ein Startbildschirm der Installationanleitung von Debian 12 erscheinen. Zunächst kann man der Installationanleitung folgen, wichtig ist hier nur ein root Passwort zu setzen, da es sonst später bei der Installation noch Proxmox zu komplikationen führen kann. Bei der Softwareauswahl ist zu beachten das nur das Standart System angehackt ist. Sollte es nach der Vollendung des Vorgangs und einem Restart einen Fehler geben, liegt dies an dem falsch zugewissenen GRUB Loader, dieser sollte auf einer bootfähigen Festplatte liegen. Hier ist vom Vorteil wenn man nach dem Restart in den Rescue Mode geht der einem Vorgeschlagen wird in mit Hilfe deer Anleitung die richtige Festplatte auswhählt. Wenn alles funktioniert kommt man in die Shell des Debian Systems wo die nächsten Schritte folgen. 
Nun ist es wichtig eine statische IP-Adresse zu setzen ansonsten kommt es zu einem Fehler bei Proxmox. Hierzu mit nano /etc/network/interfaces in das netzwerkinterfaceeinstellungen gehen und bei dem jewiligen Netzwerkadapter das dhcp löschen und an stelle dieser static hinschreiben. Darunter kommt das die IP-Adresse, Netzwerkmaske und das Gateway, wichtig ist das die richtigen Addressen in dem Netzwerk wo sich der Server befindet stimmen ansonsten gibt es schwierigkeiten mit der Interetverbindung. Mit strg + O speichern und danach mit strg + X verlassen. Als nächsten Schritt mit nano /etc/hosts in die datei hineingehen und in der ersten Zeile localhost zu localhost.localdomain localhost ändern und in der zweiten Zeile die IP-Adresse zu der richtigen IP-Adresse ändern, die vorhin in der netzwerkinterfaceeinstellungen datei vergeben wurde. Wenn diese einstellungen geändert wurden wieder speichern und verlassen. Anschließend kann man man mit dem Befehl hostname --ip-adress überprüfen ob alles funktioniert hat, wenn hier die richtrige IP-Adresse kommt hat alles funktioniert. Als nächstes mit ifdown + Netzwerkadaptername und ifup + Netzwerkadaptername, die Netzwerkkarteneinstellungen neu laden und anschließend mit ip a überprüfen ob die richtige ip-Adresse ausgegeben wird. 
