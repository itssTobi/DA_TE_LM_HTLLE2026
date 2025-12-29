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

 : Geplante Projektkosten

Am ende sollten Sie eine Projektkostensumme ermitteln und hier angeben damit man sagen kann
__Das Projekt kostet in Summe so und so viel Euro__. 


Am Ende der Diplomarbeit fügen Sie hier noch eine Liste der tatsächlich angefallenen Kosten ein.

#### Projektrisiken

| Risiko         | EW  | Auswirkungen     | Maßnahmen     |
|:--------------:|:---:| :----------------|:--------------|
| Überziehen der Kosten | 15% | Erhöhte Kosten für Schüler | Budgetierung |
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
| Auftraggeber | Auftraggeber der internen Diplomarbeit | Frank Borland |
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


### 2025-08-28: Netzwerkscan mit Nmap und Netdiscover durchgeführt	

- 

### 2025-08-31: Drei IDS-Systeme miteinander verglichen	

- Es wurden 3 verschieden IDS-Systeme verglichen

### 2025-09-07: Ausgewähltes IDS-System implementiert	

- Das ausgewählte IDS-System ist aktiv auf dem virtuellen Netzwerk

### 2025-09-13: Erste Simulation mit Mimikatz und Metasploit durchgeführt

-

### 2025-09-15: Reaktion des IDS überprüft

- Es wurde überprüft ob das IDS-System bei dem Angriff anschlägt

### 2025-11-12: Erste Zwischenpräsentation der Diplomarbeit	

- Die erste Zwischenpräsentation wurde gehalten

### 2026-02-26: Zweite Zwischenpräsentation der Diplomarbeit	

- Die zweite Zwischenpräsentation wurde gehalten

### 2026-02-28: Abschluss der Verschriftlichung der Ergebnisse und der Diplomarbeit	

- Stilfehler sind behoben
- DA Dokumentationsblatt ist unterschrieben, eingescannt und im Hauptdokument enthalten 
- Praxisteil ist ebgeschlossen und verschriftlicht
- Informationen sind im DA Portal eingegeben
- Unterschriebene DA Betreuungsprotokolle sind in der DA enthalten
- DA liegt dem Betreuer in ausgedruckter Form vor
    

## Anwendungsfälle

Hier beschreiben Sie die Anwendungsfälle (=UseCases) Ihrer Anwendung / Diplomarbeit. Dabei sollte die Beschreibung auf hohem Niveau (also ohne implementierungsspezifische Details) erfolgen und typischerweise so benannt sein, wie die Ziele aus Sicht der Akteure heißen: Mitglied anmelden, Geld abheben, Auto zurückgeben.

Jeder Anwendungsfall wird im selben Muster beschrieben. In den folgenden Absätzen ist zuerst eine allgemeine Beschreibung eines solchen Anwendungsfalls zu finden und dann ein Beispiel dazu.

Damit man auch versteht wer mit welchem Anwendungsfall agiert bietet es sich an hier eine Übersichtsgrafik zu erstellen:

![Übersicht Anwendungsfälle](img/anwendungsfalldiagramm.png){width=60%}

\newpage
### Anwendungsfallname
Anwendungsfälle haben einen eindeutigen Namen aus dem man auf den Inhalt des Anwendungsfalls schließen kann. Wenn Sie agil arbeiten dann stellt ein Anwendungsfall eine UserStory dar welche im Backlog liegt und im Laufe des Projekts (in einem Sprint) abgearbeitet wird.

#### Kurzbeschreibung
Hier erfolgt eine kurze Beschreibung, was im Anwendungsfall passiert. Kurz bedeutet, dass es zwei oder drei Zeilen sind, selten mehr.
      
#### Trigger
Der fachliche Grund bzw. die Gründe dafür, dass dieser Anwendungsfall ausgeführt 

#### Vorbedingung
Alle Bedingungen, die erfüllt sein müssen, damit dieser Anwendungsfall ausgeführt werden kann. Gibt es keine Vorbedingungen, so steht hier "keine".
      
#### Nachbedingung
Der Zustand, der nach einem erfolgreichen Durchlauf des Anwendungsfalls erwartet wird.

#### Akteure
Akteure sind beteiligte Personen oder Systeme außerhalb (!) des beschriebenen Systems. Z. B. Anwender, angemeldeter Anwender, Kunde, System, Abrechnungsprozess.

#### Standardablauf
Hier wird das typische Szenario dargestellt, das leicht zu verstehen oder der am häufigsten vorkommende Fall ist. An seinem Ende steht die Zielerreichung des Primärakteurs. Die Ablaufschritte werden nummeriert und meist in strukturierter Sprache beschrieben. Ablaufpläne können jedoch ebenfalls benutzt werden, wenn es angebracht erscheint. Mittels der UML können diese Ablaufschritte in Aktivitätsdiagrammen oder Anwendungsfall-orientierten Sequenzdiagrammen dargestellt werden.

#### Fehlersituationen
Dies sind Szenarien, die sich außerhalb des Standardablaufs auch bei der (versuchten) Zielerreichung des Anwendungsfalls ereignen können. Sie werden meistens als konditionale Verzweigungen der normalen Ablaufschritte dargestellt. An ihrem Ende steht ein Misserfolg, die Zielerreichung des Primärakteurs oder eine Rückkehr zum Standardablauf.

#### Systemzustand im Fehlerfall
Der Zustand, der nach einem erfolglosen Durchlauf des Anwendungsfalls erwartet wird.