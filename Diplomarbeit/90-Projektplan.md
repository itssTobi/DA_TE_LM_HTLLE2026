
# Projekthandbuch
\textauthor{Eichelberger Tobias}

## Entwicklungsplan

### Projektauftrag
Aktuell setzen die Schülerinnen und Schüler im Laborblock „Pentesting" die Testumgebung mit virtuellen Maschinen auf ihren eigenen Geräten auf. Unterschiedliche Hardwareausstattungen führen dabei zu erheblichen Abweichungen in Bearbeitungstempo und Lernfortschritt. Im Rahmen dieser Diplomarbeit soll daher eine zentrale virtuelle Laborumgebung auf einem Proxmox-Server aufgebaut werden, die von allen Schülerinnen und Schülern gleichermaßen genutzt werden kann.

#### Projektziele
Im Rahmen dieser Diplomarbeit soll evaluiert werden, ob eine virtuelle Netzwerkumgebung auf einem Server – bestehend aus Clients und einem Domaincontroller, dem die Clients untergeordnet sind, abgesichert durch ein Intrusion Detection System (IDS), das Angriffe externer Clients erkennt – im Schulunterricht eingesetzt und praktisch im Laborunterricht genutzt werden kann.

#### Nicht-Ziele bzw. nicht Inhalte
Nicht Ziel dieser Arbeit ist es, eine produktive oder hochverfügbare Infrastruktur bereitzustellen, sondern eine Testumgebung zu schaffen, die für Ausbildungszwecke geeignet ist.

#### Projektnutzen
Der Nutzen dieses Projekts besteht darin, Chancengleichheit zu schaffen, indem allen Schülerinnen und Schülern die gleiche Ausgangsituation sowie identische Hardwareressourcen zur Verfügung stehen.

#### Projektauftraggeber/in
Der Projektauftraggeber dieser Diplomarbeit ist die  HTL Leoben. 

#### Projekttermine

| Termin     | Inhalt                          |
|-----------:|:--------------------------------|
| 2025-06-23 | Projektstart                    |
| 2025-06-23 | Projektpräsentation             |
| 2025-11-12 | Erste Zwischenpräsentation      |
| 2026-02-26 | Zweite Zwischenpräsentation     |
| 2026-02-28 | Abgabe Endversion an Betreuer   |

: Projektterminübersicht


#### Projektkosten

| Meilenstein  | Kostenart | Menge  | Preis   | Gesamtkosten | Deckung durch |
|:-------------|:---------:|:------:|--------:|-------------:|---------------|
| Proxmox-Server eingerichtet     | Hardware  |  1 |   13,80 | 13,80      | Schüler       |
| Abschluss der Verschriftlichung der Ergebnisse und der Diplomarbeit	 | Druck     |  3     |   26.00 |  53.00      | Schüler       |
|Stromkosten Proxmox-Server | Betriebskosten | 7 Monate | 15 | 105 | Schüler |

 : Geplante Projektkosten

Die Gesamtkosten des Projekts belaufen sich auf 171,80 € und werden von den Schülern getragen. Die geplanten Kosten wurden nicht überschritten.


#### Projektrisiken

| Risiko         | EW  | Auswirkungen     | Maßnahmen     |
|:--------------:|:---:| :----------------|:--------------|
| Überziehen der Kosten | 20% | Erhöhte Kosten für Schüler | Budgetierung |
| Ungenaue Schätzungen | 30% | Ungenaue Schätzungen führen zu Problem bezüglich Terminen und Budget. | Schätzungen mit Fachkollegen absprechen|

: Projektrisiken

### Projektorganisation

#### Projektbeteiligte

| Vorname     | Nachname     | Organisation | Kontaktinfos      | Telefonnummer  |
|:------------|:-------------|:-------------|:------------------|:---------------|
| Tobias      | Eichelberger | HTL Leoben   | 211witb04@o365.htl-leoben.at | 0676 9024021 |
| Lukas       | Macuha       | HTL Leoben   | 211witb16@o365.htl-leoben.at   | 0660 5569396 |

: Projektbeteiligte

#### Projektrollen

| Projektrolle           | Rollenbeschreibung     | Name              |
|------------------------|------------------------|-------------------|
| Projektleiter | Verantwortlicher für Einhaltung des Projektrahmens | Eichelberger Tobias |
| Betreuer | Schulischer Betreuer | Günther Hutter |
| Betreuer | Schulischer Betreuer | Thomas Messner |

: Projektrollen

### Vorgehen bei Änderungen

Im Falle einer Änderung des Meilensteinplans sind alle Projektmitglieder und Betreuer zu informieren. Änderungen bedürfen der Zustimmung durch Betreuer und Projektmitglieder und werden in der Projektdokumentation dokumentiert.

## Meilensteine

### 2025-05-18: Proxmox-Server eingerichtet
- Auf dem Server läuft Proxmox

### 2025-11-01: VPN-Verbindung erfolgreich eingerichtet	
- Tailscale ist auf Proxmox installiert sodass Nutzer von außen zugreifen können

### 2025-11-26: GNS3 installiert	
- GNS3 Server wurde auf Proxmox installiert

### 2025-12-17: Client und Domaincontroller eingerichtet	
- Client und Domaincontroller laufen auf Proxmox
- Client ist dem Domaincontroller zugeordnet
- Demonutzer wurde erstellt

### 2025-08-31: Drei IDS-Systeme miteinander verglichen
- Es wurden drei verschiedene IDS-Systeme miteinander verglichen.
    
### 2025-09-07: Ausgewähltes IDS-System implementiert
- Das ausgewählte IDS-System ist im virtuellen Netzwerk aktiv.
    
### 2025-09-13: Erste Simulation mit Mimikatz
- Der Angriff wurde auf Windows durchgeführt, wobei NTLM-Hashes extrahiert wurden.
    
### 2025-09-15: Reaktion des IDS überprüft
- Es wurde überprüft, ob das IDS-System bei dem Angriff Alarm schlägt.
    
### 2025-10-15: Kali als Angreifer eingesetzt
- Kali Linux wurde dem Netzwerk als Angreifersystem hinzugefügt.
    
### 2025-10-20: Passwort online geknackt
- Das Passwort eines Benutzers wurde online geknackt.
    
### 2025-10-23: Domain Controller
- Es wurde versucht, mit Kali Linux Domain-Administrator-Rechte zu erlangen.
    
### 2025-11-12: Erste Zwischenpräsentation der Diplomarbeit
- Die erste Zwischenpräsentation wurde gehalten.
    
### 2025-11-20: Passwort offline geknackt
- Das Passwort wurde offline geknackt.
    
### 2025-12-18: Domain-Administrator
- Durch Kerberoasting wurden Domain-Administrator-Rechte erlangt.
    
### 2025-12-22: Golden Ticket
- Ein Golden Ticket wurde erstellt und verwendet.
    
### 2026-02-26: Zweite Zwischenpräsentation der Diplomarbeit
- Die zweite Zwischenpräsentation wurde gehalten.

### 2026-02-28: Abschluss der Verschriftlichung der Ergebnisse und der Diplomarbeit	
- Stilfehler sind behoben
- Praxisteil ist abgeschlossen und verschriftlicht
- DA liegt dem Betreuer in ausgedruckter Form vor