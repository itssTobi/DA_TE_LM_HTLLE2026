
# Zusammenfassung
Diese Diplomarbeit dokumentiert die Planung und Umsetzung einer virtuellen Laborumgebung für die HTL Leoben. Zentrales Ziel war die Evaluierung und Implementierung eines zentralen Servers, der die IT-Infrastruktur für den Laborblock „Pentesting“ bereitstellt, in dem Cyberangriffe kontrolliert simuliert werden können.

## Durchgeführte Arbeiten

### Infrastruktur-Aufbau
Das Projekt startete mit der Installation und Konfiguration eines Proxmox-VE-Servers auf einem HP ProLiant G7 (80 GB Speicher, 70 GB RAM) als zentraler Virtualisierungsplattform. Der Server basiert auf Debian 12 und wurde mit statischer IP-Adresse für einen stabilen Betrieb konfiguriert.

### Sicherer Fernzugriff
Für den externen Zugang zur Laborumgebung wurde Tailscale als VPN auf Basis von WireGuard eingerichtet. Die Lösung ermöglicht Schülerinnen, Schülern und Lehrenden einen standortunabhängigen, abgesicherten Zugriff auf die virtuellen Maschinen; sie wurde sowohl auf dem Proxmox-Server als auch auf Endgeräten konfiguriert.

### Netzwerk-Design
Mit GNS3 wurde eine flexible virtuelle Netzwerktopologie aufgebaut und über mehrere virtuelle Bridges segmentiert, um unterschiedliche Netzwerkbereiche abzubilden.

### Virtualisierte Systeme
Folgende virtuelle Maschinen wurden bereitgestellt:
- Windows 11 Client als Zielsystem für Penetrationstests
- Windows 10 Client als Zielsystem für Penetrationstests
- Windows Server 2019 als Domaincontroller
- Ubuntu 22.04 LTS als Basis für das IDS-System
- Kali Linux für Penetrationstests

### Active-Directory-Implementierung
Der Windows Server 2019 wurde als Domaincontroller mit Active Directory-Domänendiensten konfiguriert. Eine Domäne mit Benutzerkonten wurde aufgebaut und die Windows-Clients erfolgreich eingebunden – eine für Schulungszwecke typische Unternehmensumgebung.

### Intrusion Detection System (IDS)
Wazuh wurde als IDS implementiert. Der Wazuh-Server läuft auf Ubuntu, die Agenten auf den Windows-Clients und dem Domaincontroller. Über ein grafisches Dashboard werden Sicherheitsereignisse zentral überwacht.

### Sicherheitstests und Angriffsszenarien
Zur Überprüfung der Umgebung und der Erkennungsleistung des IDS wurden unter anderem durchgeführt:
- Passwortangriffe (online und offline Brute-Force)
- Kerberoasting zur Erlangung erweiterter Berechtigungen
- Golden-Ticket-Angriffe zur Demonstration von Kerberos-Schwachstellen
- Exploits mit Impacket, Nmap, Responder, Metasploit, Evil-WinRM
- Analyse der IDS-Erkennungen über verschiedene Angriffsvektoren

## Fazit

Die Arbeit belegt, dass eine zentralisierte nutzbare Laborumgebung auf Basis von Proxmox, Tailscale, GNS3 und Wazuh praxistauglich umgesetzt werden kann. Die Tests bestätigen die Funktionsfähigkeit der Plattform und ermöglichen realitätsnahe Übungen, ohne produktive Systeme zu gefährden. Damit entsteht eine belastbare Grundlage für vertiefte Cybersecurity-Schulungen an der HTL Leoben.