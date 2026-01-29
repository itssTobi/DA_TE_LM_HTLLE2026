
\newpage
## Projektabschlussbericht

### Erfolgsmessung

#### Erreichung Leistungs-/Qualitätsziele
Die gesetzten Leistungs- und Qualitätsziele des Projekts wurden erreicht. Die virtuelle Netzwerkumgebung wurde erfolgreich auf dem Proxmox-Server eingerichtet; sie umfasst Clients und einen Domaincontroller, die regelkonform miteinander kommunizieren. Das implementierte Intrusion Detection System (IDS) erkennt Angriffe eines externen Clients, die im Rahmen der Tests erfolgreich simuliert wurden.

#### Erreichung Terminziele
Die meisten Meilensteine wurden innerhalb des vorgesehenen Zeitrahmens erreicht; vereinzelt traten jedoch Verzögerungen auf. Insbesondere bei der Simulation und den Tests des IDS-Systems ergaben sich unerwartete Herausforderungen, die zeitliche Verschiebungen zur Folge hatten. Dennoch konnten alle wesentlichen Meilensteine abgeschlossen werden, teilweise mit geringfügigen Verzögerungen.

#### Erreichung Kosten-/Aufwandsziele
Das Projektbudget wurde weitgehend eingehalten. Die geplanten Kosten für defekte Hardware und den Druck der Diplomarbeit wurden wie vorgesehen gedeckt. Allerdings fielen unerwartete Betriebskosten für den Proxmox-Server an, die über der ursprünglichen Kalkulation lagen.

### Reflexion / Lessons Learned

#### Teamarbeit
Das Projekt verdeutlichte, dass eine effektive Kommunikation zwischen den Teammitgliedern essenziell für einen erfolgreichen Projektabschluss ist. Wichtig ist zudem eine klare Aufgabenverteilung, damit jedes Mitglied seine Verantwortlichkeiten kennt und Missverständnisse vermieden werden. Regelmäßige Meetings und der kontinuierliche Austausch per Textnachrichten erwiesen sich als hilfreich, um den Projektfortschritt zu besprechen und potenzielle Probleme frühzeitig zu identifizieren und zu lösen.

#### Projektmanagement
Im Bereich des Projektmanagements wurde deutlich, dass Planung und insbesondere Zeitmanagement von zentraler Bedeutung für einen erfolgreichen Projektabschluss sind. Als Projektleitung ist es erforderlich, stets den Überblick über den Fortschritt der einzelnen Teilbereiche zu behalten, um bei auftretenden Problemen rechtzeitig gegensteuern zu können. Wichtig ist zudem, dass die Projektleitung die Teammitglieder konsequent an bevorstehende Termine erinnert, um deren Einhaltung sicherzustellen.

#### Sonstige Lernerfahrungen
Das Projekt bot umfassende Einblicke in die technischen Aspekte der Einrichtung virtueller Netzwerkumgebungen. Die praktischen Erfahrungen erweiterten das Verständnis für Netzwerksicherheit und virtuelle Infrastrukturen erheblich.

### Nachhaltigkeitsanalyse

Die vorliegende Diplomarbeit wurde unter Berücksichtigung der Sustainable Development Goals (SDGs) der Vereinten Nationen entwickelt. Im Kontext dieses Projekts zur Bereitstellung einer zentralen virtuellen Laborumgebung für den Pentesting-Unterricht an der HTL Leoben sind insbesondere die Ziele SDG 4 (Hochwertige Bildung), SDG 10 (Weniger Ungleichheiten) und SDG 12 (Nachhaltiger Konsum und Produktion) von besonderer Relevanz.

#### SDG 4: Hochwertige Bildung
Das Projekt leistet einen wesentlichen Beitrag zur Förderung hochwertiger Bildung im Bereich der Cybersecurity. Durch die Bereitstellung einer zentralen Laborumgebung auf dem Proxmox-Server erhalten alle Schülerinnen und Schüler Zugang zu einer professionellen, realitätsnahen Testumgebung für Penetrationstesting und Intrusion Detection.

Die implementierte Infrastruktur mit Windows-Clients, Domaincontroller und Kali Linux ermöglicht es den Lernenden, aktuelle Angriffstechniken wie Brute-Force-Attacken, Kerberoasting oder Golden-Ticket-Angriffe in einer sicheren Umgebung zu erproben. Diese praktischen Erfahrungen sind essentiell für die Ausbildung zukünftiger IT-Sicherheitsexperten. Zusätzlich ermöglicht der standortunabhängige Zugriff über die Tailscale-VPN-Lösung flexibles und selbstgesteuertes Lernen.

#### SDG 10: Weniger Ungleichheiten
Eines der Kernziele dieses Projekts ist die Schaffung von Chancengleichheit im Bildungsbereich. Bisher führten unterschiedliche Hardwareausstattungen der Schülerinnen und Schüler zu abweichenden Bearbeitungsgeschwindigkeiten und Lernfortschritten im Laborblock „Pentesting". Lernende mit leistungsschwächeren Geräten waren benachteiligt, da die lokale Ausführung mehrerer virtueller Maschinen hohe Anforderungen an die Hardware stellt.

Durch die zentrale Bereitstellung der virtuellen Umgebung auf dem Proxmox-Server werden diese Ungleichheiten beseitigt. Alle Schülerinnen und Schüler erhalten unabhängig von ihrer individuellen Geräteausstattung identische Rahmenbedingungen für das Lernen. Die Verbindung zum Server erfolgt über einen einfachen Remote-Zugriff, der auch mit älteren oder weniger leistungsfähigen Endgeräten problemlos möglich ist. Diese Demokratisierung des Zugangs zu IT-Ressourcen trägt dazu bei, sozioökonomische Barrieren im Bildungsbereich abzubauen.

#### SDG 12: Nachhaltiger Konsum und Produktion
Die Zentralisierung der virtuellen Laborumgebung auf einem Server trägt zur Ressourceneffizienz bei. Anstatt dass jeder Schüler und jede Schülerin leistungsstarke Hardware für die lokale Ausführung virtueller Maschinen benötigt, wird die Rechenleistung zentral bereitgestellt und effizient genutzt. Dies hat mehrere positive Auswirkungen:

- **Reduzierung des Hardwarebedarfs**: Es besteht keine Notwendigkeit für regelmäßige Hardware-Upgrades der Schülergeräte. Ältere Geräte können weiterhin produktiv genutzt werden.
- **Optimierte Energienutzung**: Ein zentraler Server arbeitet energieeffizienter als viele individuelle Geräte, die für ressourcenintensive Virtualisierungsaufgaben genutzt werden.
- **Verlängerte Lebensdauer von Endgeräten**: Da die Schülergeräte nicht die volle Rechenlast tragen, haben sie eine längere Nutzungsdauer, was zur Reduktion von Elektroschrott beiträgt.
- **Wiederverwendung von Hardware**: Der eingesetzte HP ProLiant G7 Server zeigt, dass auch ältere Serverhardware für Bildungszwecke effektiv weiterverwendet werden kann.

#### Fazit
Das Projekt leistet einen ganzheitlichen Beitrag zur nachhaltigen Entwicklung im Bildungsbereich. Die zentrale virtuelle Laborumgebung fördert hochwertige, praxisnahe Bildung im Bereich der Cybersecurity und schafft Chancengleichheit für alle Lernenden. Gleichzeitig werden durch die Ressourcenoptimierung ökologische Aspekte berücksichtigt. Die entwickelte Lösung kann als Modell für ähnliche Projekte an anderen Bildungseinrichtungen dienen und ermöglicht es zukünftigen Jahrgängen, von der aufgebauten Umgebung zu profitieren. 