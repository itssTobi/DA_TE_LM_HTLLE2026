
# Zusammenfassung
Diese Diplomarbeit dokumentiert die erfolgreiche Planung und Umsetzung einer komplexen virtuellen Laborumgebung für die HTL Leoben. Das zentrale Ziel war die Evaluierung und Implementierung eines zentralen Servers, der die gesamte IT-Infrastruktur für den Laborbetrieb im Block "Pentestesting" bereitstellt, in der Cyberattacken auf sichere Weise simuliert werden können.

## Durchgeführte Arbeiten

### Infrastruktur-Aufbau
Das Projekt begann mit der Installation und Konfiguration eines Proxmox VE-Servers auf einem HP ProLiant G7 Server (mit 80GB Speicher und 70GB RAM), der als zentrale Virtualisierungsplattform dient. Der Proxmox-Server wurde auf Debian 12 basierend aufgebaut und mit einer statischen IP-Adresse konfiguriert, um eine stabile Infrastruktur zu gewährleisten.

### Sicherer Fernzugriff
Um den Zugriff auf die Laborumgebung von außerhalb des Schulnetzwerks zu ermöglichen, wurde Tailscale als VPN-System implementiert. Diese WireGuard-basierte Lösung ermöglicht es Schülern und Lehrpersonen, sicher und einfach auf die virtuellen Maschinen zuzugreifen, unabhängig von ihrem Standort. Das Tailscale-VPN wurde sowohl auf dem Proxmox-Server als auch auf Endgeräten konfiguriert.

### Netzwerk-Design
Mit GNS3 wurde eine flexible virtuelle Netzwerktopologie aufgebaut, die die Verbindung mehrerer virtueller Maschinen ermöglicht. Das System wurde mit mehreren virtuellen Bridges konfiguriert, um verschiedene Netzwerksegmente zu simulieren.

### Virtualisierte Systeme
Es wurden mehrere virtuelle Maschinen installiert und konfiguriert:
- Windows 11 Client als Zielsystem für Penetrationstests
- Windows 10 Client als Zielsystem für Penetrationstests
- Windows Server 2019 als Domain Controller
- Ubuntu 22.04 LTS als Basis für das IDS-System
- Kali Linux für Penetrationstests

### Active Directory Implementierung
Der Windows Server 2019 wurde als Domaincontroller mit Active Directory-Domänendiensten konfiguriert. Es wurde eine Domäne mit  Benutzern aufgebaut, und die Windows-Clients wurden erfolgreich in diese Domäne integriert. Dies ist eine typische Unternehmensumgebung, die für Schulungszwecke ideal ist.

### Intrusion Detection System (IDS)
Wazuh wurde als IDS-System implementiert, um die Sicherheitsüberwachung des Netzwerks zu ermöglichen. Der Wazuh-Server wurde auf der Ubuntu-VM installiert, und Wazuh-Agenten wurden auf den Windows-Clients und dem Domain Controller installiert. Dies ermöglicht die zentrale Überwachung aller Sicherheitsereignisse über ein grafisches Dashboard.

### Sicherheitstests und Angriffsszenarien
Umfangreiche Penetrationstests wurden durchgeführt, um die Umgebung und die Erkennungsfähigkeiten des IDS zu testen.:
- Passwortangriffe (online und offline Brute-Force-Attacken)
- Kerberoasting-Angriffe zur Erlangung von Domain-Administrator-Rechten
- Golden-Ticket-Angriffe zur Demonstration von Kerberos-Schwachstellen
- Verschiedene Exploits mithilfe von Tools wie Impacket, Nmap, Responder, Metasploit und Evil-WinRM
- Analyse der IDS-Erkennungsfähigkeiten bei verschiedenen Angriffsvektoren

## Fazit

Diese Diplomarbeit zeigt die erfolgreiche Planung und Implementierung einer sicheren und pädagogisch Laborumgebung für die HTL Leoben. Die Kombination von Proxmox-Virtualisierung, Tailscale-VPN, GNS3-Netzwerk-Simulation und Wazuh-IDS schafft eine flexible Plattform für technische Ausbildung im Bereich der Cybersecurity. Die durchgeführten Sicherheitstests bestätigen die Funktionsfähigkeit des Systems und zeigen, dass Schüler auf dieser Plattform umfassende praktische Erfahrungen in realistischen IT-Sicherheitsszenarien sammeln können, ohne dabei produktive Systeme zu gefährden. Insgesamt bietet diese Arbeit wertvolle Einblicke in die Implementierung einer unternehmensartigen IT-Infrastruktur für Schulungszwecke und legt den Grundstein für zukünftige erweiterte Cybersecurity-Schulungen an der HTL Leoben.
