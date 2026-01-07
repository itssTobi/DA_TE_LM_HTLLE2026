# Projekthandbuch
\textauthor{Eichelberger Tobias}

## Entwicklungsplan

### Projektauftrag

Aktuell wird der Laborunterricht im Block „Pentesting“ so gestaltet, dass die Schülerinnen und Schüler die Testumgebung mittels virtueller Maschinen auf ihren eigenen Geräten selbst aufsetzen. Aufgrund unterschiedlicher Hardwareaustattung der einzelnen Geräte der Schülerinnen und Schüler, kommt zu erheblichen Unterschieden bzw. Fortschritten in der Abhandlung der Themenstellungen bzw. im Lernfortschritt.


#### Projektziele

Im Rahmen dieser Diplomarbeit soll evaluiert werden, ob dieser Aufbau einer virtuellen Netzwerkumgebung auf einem Server zu gestalten, bestehend aus einem Client und einem Domaincontroller, dem der Client untergeordnet ist, diese Umgebung soll durch ein IDS-System (Intrusion Detection System) abgesichert werden, das Angriffe von einem externen Client erkennen kann, im Schulunterricht eingesetzt und praktisch im Laborunterricht genutzt werden kann.


#### Nicht-Ziele bzw. nicht Inhalte

Nicht Ziel dieser Arbeit ist es, eine produktive oder hochverfügbare Infrastruktur bereitzustellen, sondern eine Testumgebung zu schaffen, die für Ausbildungszwecke geeignet ist.

#### Projektnutzen

Der Nutzen dieses Projekt besteht darin Chancengleichheit zu schaffen indem allen Schülerinnen und Schüler die gleiche Ausgangsituation beziehungsweise die gleiche Hardware zu verfügung haben.

#### Projektauftraggeber/in

Hier beschreiben Sie wer der Projektauftraggeber ist. Falls es eine externe Firma ist können Sie hier eine kurze Beschreibung des Unternehmens (sofern Projektrelevant) einfügen.

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

Hier dokumentieren Sie welche Kosten fallen Für Ihr Projekt an und wer kommt für diese Kosten auf ?

| Meilenstein  | Kostenart | Menge  | Preis   | Gesamtkosten | Deckung durch |
|:-------------|:---------:|:------:|--------:|-------------:|---------------|
| Proxmos-Server eingerichtet     | Hardware  |  1 |   13,80 | 13,80      | Schüler       |
| Abschluss der Verschriftlichung der Ergebnisse und der Diplomarbeit	 | Druck     |  3     |   26.00 |  53.00      | Schüler       |
|Stromkosten Proxmox-Server | Betriebskosten | 7 Monate | 15 | 105 | Schüler |

 : Geplante Projektkosten

Am ende sollten Sie eine Projektkostensumme ermitteln und hier angeben damit man sagen kann
__Das Projekt kostet in Summe so und so viel Euro__. 


Am Ende der Diplomarbeit fügen Sie hier noch eine Liste der tatsächlich angefallenen Kosten ein.

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
| Lukas       | Macuha       | HTL Leoben   | 211witb@o365.htl-leoben.at   | 0660 5569396 |

: Projektbeteiligte

#### Projektrollen

Hier werden den Kontakten von oben konkrete Rollen zuewiesen.

| Projektrolle           | Rollenbeschreibung     | Name              |
|------------------------|------------------------|-------------------|
| Projektleiter | Verantwortlicher für Einhaltung des Projektrahmens | Eichelberger Tobias |
| Betreuer | Schulischer Betreuer | Günther Hutter |
| Betreuer | Schulischer Betreuer | Thomas Messner |

: Projektrollen

### Vorgehen bei Änderungen

Im Falle einer Änderung des Meilensteinplans müssen alle Projektmitglieder und Betreuer informiert werden. Änderungen müssen die Betreuer sowie die Projektmitglieder zustimmen, die Änderungen werden in der Projektdokumentation festgehalten.

## Meilensteine

### 2025-05-18: Proxmox-Server eingerichtet

- Auf dem Server läuft Proxmox

### 2025-11-01: VPN-Verbindung erfolgreich eingerichtet	

- Man kann von unterwegs auf das Proxmox Dashboard zugreifen

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
    
### 2025-09-13: Erste Simulation mit Mimikatz durchgeführt

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
- DA Dokumentationsblatt ist unterschrieben, eingescannt und im Hauptdokument enthalten 
- Praxisteil ist ebgeschlossen und verschriftlicht
- Informationen sind im DA Portal eingegeben
- Unterschriebene DA Betreuungsprotokolle sind in der DA enthalten
- DA liegt dem Betreuer in ausgedruckter Form vor
    
