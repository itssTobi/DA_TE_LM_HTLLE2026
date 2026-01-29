
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

#### Einleitung zur Nachhaltigkeit im Projektkontext
Die vorliegende Diplomarbeit wurde unter Berücksichtigung der Sustainable Development Goals (SDGs) der Vereinten Nationen entwickelt. Die SDGs bilden einen globalen Rahmen für nachhaltige Entwicklung und umfassen 17 Ziele, die bis 2030 erreicht werden sollen. Im Kontext dieses Projekts zur Bereitstellung einer zentralen virtuellen Laborumgebung für den Pentesting-Unterricht an der HTL Leoben sind insbesondere die Ziele SDG 4 (Hochwertige Bildung), SDG 9 (Industrie, Innovation und Infrastruktur), SDG 10 (Weniger Ungleichheiten) und SDG 12 (Nachhaltiger Konsum und Produktion) von besonderer Relevanz.

#### SDG 4: Hochwertige Bildung
Das Projekt leistet einen wesentlichen Beitrag zur Förderung hochwertiger Bildung im Bereich der Cybersecurity. Durch die Bereitstellung einer zentralen Laborumgebung auf dem Proxmox-Server erhalten alle Schülerinnen und Schüler Zugang zu einer professionellen, realitätsnahen Testumgebung. Diese Umgebung ermöglicht praxisnahe Übungen in den Bereichen Penetrationstesting, Netzwerksicherheit und Intrusion Detection, ohne dass produktive Systeme gefährdet werden.

Die implementierte Infrastruktur mit Windows-Clients, Domaincontroller und Kali Linux bietet den Lernenden die Möglichkeit, aktuelle Angriffstechniken wie Brute-Force-Attacken, Kerberoasting oder Golden-Ticket-Angriffe in einer sicheren Umgebung zu erproben und deren Erkennung durch das Wazuh-IDS zu analysieren. Diese praktischen Erfahrungen sind essentiell für die Ausbildung zukünftiger IT-Sicherheitsexperten und tragen zur Deckung des wachsenden Fachkräftebedarfs in diesem Bereich bei.

Darüber hinaus ermöglicht der standortunabhängige Zugriff über die Tailscale-VPN-Lösung ein flexibles Lernen, das über den Präsenzunterricht hinausgeht und selbstgesteuertes Lernen fördert.

#### SDG 9: Industrie, Innovation und Infrastruktur
Das Projekt demonstriert den innovativen Einsatz von Virtualisierungstechnologien im Bildungsbereich. Die Kombination aus Proxmox VE als Virtualisierungsplattform, GNS3 für die Netzwerksimulation und Wazuh als Intrusion Detection System zeigt, wie moderne Open-Source-Technologien effektiv für Bildungszwecke eingesetzt werden können.

Die aufgebaute Infrastruktur ist skalierbar und kann bei Bedarf um weitere virtuelle Maschinen oder Netzwerksegmente erweitert werden. Dies schafft eine zukunftsfähige Basis für den Cybersecurity-Unterricht, die mit den sich ständig weiterentwickelnden Anforderungen der IT-Sicherheitsbranche Schritt halten kann.

Der Einsatz eines zentralen Servers anstelle individueller lokaler Installationen fördert zudem die Standardisierung und Professionalisierung der IT-Infrastruktur im schulischen Kontext und bereitet die Schülerinnen und Schüler auf den Umgang mit professionellen Enterprise-Umgebungen vor.

#### SDG 10: Weniger Ungleichheiten
Eines der Kernziele dieses Projekts ist die Schaffung von Chancengleichheit im Bildungsbereich. Bisher führten unterschiedliche Hardwareausstattungen der Schülerinnen und Schüler zu abweichenden Bearbeitungsgeschwindigkeiten und Lernfortschritten im Laborblock „Pentesting". Lernende mit leistungsschwächeren Geräten waren benachteiligt, da die lokale Ausführung mehrerer virtueller Maschinen hohe Anforderungen an die Hardware stellt.

Durch die zentrale Bereitstellung der virtuellen Umgebung auf dem Proxmox-Server werden diese Ungleichheiten beseitigt. Alle Schülerinnen und Schüler erhalten unabhängig von ihrer individuellen Geräteausstattung identische Rahmenbedingungen für das Lernen. Die Verbindung zum Server erfolgt über einen einfachen Remote-Zugriff, der auch mit älteren oder weniger leistungsfähigen Endgeräten problemlos möglich ist.

Diese Demokratisierung des Zugangs zu IT-Ressourcen trägt dazu bei, sozioökonomische Barrieren im Bildungsbereich abzubauen und allen Lernenden gleiche Entwicklungschancen zu bieten.

#### SDG 12: Nachhaltiger Konsum und Produktion
Die Zentralisierung der virtuellen Laborumgebung auf einem Server trägt zur Ressourceneffizienz bei. Anstatt dass jeder Schüler und jede Schülerin leistungsstarke Hardware für die lokale Ausführung virtueller Maschinen benötigt, wird die Rechenleistung zentral bereitgestellt und effizient genutzt.

Dies hat mehrere positive Auswirkungen auf den Ressourcenverbrauch:

- Reduzierung des Hardwarebedarfs: Es besteht keine Notwendigkeit für regelmäßige Hardware-Upgrades der Schülergeräte, um mit den Anforderungen der Laborübungen Schritt zu halten. Ältere Geräte können weiterhin produktiv genutzt werden.

- Optimierte Energienutzung: Ein zentraler, professionell konfigurierter Server arbeitet in der Regel energieeffizienter als die Summe vieler individueller Geräte, die jeweils für ressourcenintensive Virtualisierungsaufgaben genutzt werden.

- Verlängerte Lebensdauer von Endgeräten: Da die Schülergeräte nicht mehr die volle Rechenlast tragen müssen, werden diese weniger beansprucht und haben potenziell eine längere Nutzungsdauer, was zur Reduktion von Elektroschrott beiträgt.

- Wiederverwendung von Hardware: Der eingesetzte HP ProLiant G7 Server zeigt, dass auch ältere Serverhardware für Bildungszwecke effektiv weiterverwendet werden kann, anstatt entsorgt zu werden.
#### Fazit der Nachhaltigkeitsanalyse
Das Projekt leistet einen ganzheitlichen Beitrag zur nachhaltigen Entwicklung im Bildungsbereich. Die zentrale virtuelle Laborumgebung fördert nicht nur hochwertige, praxisnahe Bildung im zukunftsrelevanten Bereich der Cybersecurity, sondern schafft auch Chancengleichheit für alle Lernenden unabhängig von ihrer individuellen Ausstattung. Gleichzeitig werden durch die Ressourcenoptimierung ökologische Aspekte berücksichtigt.

Die entwickelte Lösung kann als Modell für ähnliche Projekte an anderen Bildungseinrichtungen dienen und zeigt, wie Digitalisierung im Bildungsbereich nachhaltig gestaltet werden kann. Die langfristige Verfügbarkeit der Infrastruktur ermöglicht es zukünftigen Jahrgängen, von der aufgebauten Umgebung zu profitieren, was den nachhaltigen Charakter des Projekts zusätzlich unterstreicht. 