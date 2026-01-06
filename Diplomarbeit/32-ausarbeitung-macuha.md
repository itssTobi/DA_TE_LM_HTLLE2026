Teilaufgabe Schüler Macuha
==========================

\\textauthor{Lukas Macuha}

Theorie
-------

### Was ist Active Directory

Active Directory (AD) ist ein von Microsoft entwickelter Verzeichnisdienst, der speziell in Windows-basierten Netzwerken zur zentralen und effizienten Verwaltung von Benutzern, Computern, Gruppen sowie verschiedenen Ressourcen wie Druckern, Dateifreigaben oder Anwendungen eingesetzt wird. Dieser Dienst bildet das Herzstück vieler Unternehmensnetzwerke und ermöglicht eine zentrale Authentifizierung und Autorisierung innerhalb einer Domäne oder sogar über mehrere Domänen hinweg in einer Forest-Struktur. Dadurch können Benutzer sich mit einem einzigen Konto nahtlos an verschiedenen Systemen, Geräten oder Diensten anmelden, was den Alltag in großen Organisationen erheblich vereinfacht und die Produktivität steigert. Gleichzeitig bieten Administratoren die Möglichkeit, Richtlinien, Sicherheitsregeln und Berechtigungen zentral zu steuern, zu überwachen und anzupassen, ohne dass jede Änderung manuell auf jedem einzelnen Gerät vorgenommen werden muss.

in wesentlicher Vorteil von Active Directory liegt in seiner beeindruckenden Skalierbarkeit, da es sowohl in kleinen Unternehmen mit nur wenigen Nutzern als auch in sehr großen, global verteilten Unternehmensnetzwerken mit Tausenden von Benutzern und Geräten problemlos eingesetzt werden kann. Es unterstützt Hierarchien, Gruppenrichtlinien (Group Policy Objects) und Integrationen mit anderen Microsoft-Produkten wie Exchange oder Azure. Dennoch stellt Active Directory aufgrund seiner zentralen Rolle ein äußerst attraktives Ziel für Cyberangreifer dar, da eine vollständige Kompromittierung der Domäne in der Regel auch den uneingeschränkten und vollständigen Zugriff auf alle angeschlossenen Systeme, Daten und Ressourcen bedeutet, was zu erheblichen Sicherheitsrisiken und potenziellen Datenlecks führen kann.

### Was ist Kerberos

Kerberos ist ein etabliertes Authentifizierungsprotokoll, das in Active Directory standardmäßig verwendet wird und auf Prinzipien der sicheren Netzwerkkommunikation basiert, die ursprünglich am Massachusetts Institute of Technology (MIT) entwickelt wurden. Es funktioniert auf Basis von Tickets und nutzt symmetrische Verschlüsselung, um die Identitäten von Benutzern, Diensten und Geräten innerhalb eines Netzwerks sicher und zuverlässig zu überprüfen, ohne dass Passwörter über das Netzwerk gesendet werden müssen. Der zentrale Bestandteil von Kerberos ist der sogenannte Key Distribution Center (KDC), welcher typischerweise auf dem Domaincontroller läuft und für die Ausstellung und Validierung von Tickets verantwortlich ist.

Kerberos arbeitet in mehreren präzisen Schritten, um eine hohe Sicherheit zu gewährleisten: Zunächst authentifiziert sich ein Benutzer am KDC und erhält ein Ticket Granting Ticket (TGT), das als eine Art "Eintrittskarte" dient und mit dem Hash des Benutzerpassworts verschlüsselt ist. Mit diesem TGT kann der Benutzer anschließend ein Service Ticket (TGS) für bestimmte Dienste oder Ressourcen anfordern, ohne sich erneut anmelden zu müssen. Diese Tickets sind zeitlich begrenzt, um Missbrauch zu verhindern, und kryptografisch geschützt, oft mit Algorithmen wie AES. Schwachstellen entstehen vor allem dann, wenn Service Accounts mit schwachen, leicht zu knackenden Passwörtern konfiguriert werden, oder wenn die Verschlüsselung nicht auf dem neuesten Stand ist, was Angreifern Türen öffnet, um das System zu kompromittieren.

### Was ist Kerberoasting

Kerberoasting ist eine raffinierte Angriffstechnik auf Active Directory, bei der ein Angreifer Service Tickets (TGS) für Dienste mit registrierten Service Principal Names (SPN) anfordert, die in der Domäne konfiguriert sind, wie z.B. für SQL-Server oder Webdienste. Diese Tickets sind mit dem Passwort-Hash des jeweiligen Service Accounts verschlüsselt, was sie zu einem wertvollen Ziel macht, da sie Informationen über die zugrunde liegenden Credentials enthalten.

Da jeder authentifizierte Domänenbenutzer – selbst mit niedrigen Rechten – solche Tickets ohne besondere Berechtigungen anfordern darf, kann ein Angreifer diese Tickets sammeln und sie offline, also außerhalb des Netzwerks, analysieren. Mit geeigneten Tools wie Hashcat oder John the Ripper versuchen sie dann, das zugrunde liegende Passwort durch Brute-Force- oder Dictionary-Attacken zu knacken. Besonders gefährlich ist diese Technik, da das eigentliche Knacken offline erfolgt und somit keine weiteren Logs oder Spuren auf dem Domaincontroller erzeugt werden, was die Entdeckung durch Sicherheitsüberwachungssysteme erschwert und den Angreifer lange unentdeckt lassen kann.

### Was ist ein DCSync-Angriff

Ein DCSync-Angriff ist eine subtile und hochgefährliche Methode, die die normale Replikationsfunktion von Active Directory ausnutzt, um sensible Daten zu extrahieren. Domaincontroller replizieren regelmäßig Verzeichnisdaten untereinander, um Konsistenz in der gesamten Domäne oder Forest zu gewährleisten, was ein essentieller Bestandteil der Active-Directory-Architektur ist und für die Verfügbarkeit und Redundanz sorgt. Konten mit speziellen Rechten, wie z.B. Replicate Directory Changes All, dürfen diese Replikationsdaten legitim anfordern, um Änderungen zu synchronisieren.

Hat ein Angreifer Zugriff auf ein solches Konto mit diesen erweiterten Rechten – oft durch vorherige Kompromittierungen erreicht –, kann er die Passwort-Hashes aller Benutzer, inklusive hochsensibler Administratoren und des besonders kritischen krbtgt-Kontos, abrufen, ohne dass zusätzliche Werkzeuge oder Exploits benötigt werden. Der Angriff ist besonders kritisch, da er keine traditionellen Exploits oder Schwachstellen ausnutzt, sondern legitime Active-Directory-Funktionen missbraucht, was ihn schwer zu erkennen macht und potenziell zu einer vollständigen Übernahme der Domäne führen kann, mit langfristigen Konsequenzen für die Sicherheit des gesamten Netzwerks.

### Was ist ein Golden-Ticket-Angriff

Ein Golden Ticket ist ein gefälschtes Kerberos Ticket Granting Ticket (TGT), das von einem Angreifer erstellt wird, um uneingeschränkten Zugriff auf die Domäne zu erlangen. Die Voraussetzung für diesen Angriff ist der Besitz des Passwort-Hashes des krbtgt-Kontos, das als das "Goldene Konto" gilt, da es alle Kerberos-Tickets innerhalb einer Domäne signiert und somit die Integrität des gesamten Authentifizierungssystems gewährleistet.

Mit einem solchen Golden Ticket kann sich ein Angreifer als beliebiger Benutzer ausgeben, inklusive hochprivilegierter Domain Administratoren oder sogar Systemkonten, ohne dass echte Credentials benötigt werden. Diese Tickets können sehr lange gültig sein – oft Jahre – und ermöglichen einen nahezu unsichtbaren und dauerhaften Zugriff auf die Domäne, da sie nicht auf normale Authentifizierungslogs zurückgreifen und somit unter dem Radar der Sicherheitsüberwachung bleiben. Der Angriff kann nur effektiv gestoppt werden, indem das krbtgt-Passwort zweimal zurückgesetzt wird, was die Signatur aller Tickets invalidiert und den Angreifer aussperrt, aber dies erfordert sorgfältige Planung, um den Betrieb nicht zu stören.

### Was ist Impacket

Impacket ist eine vielseitige Sammlung von Python-Bibliotheken und Tools, die speziell für die Arbeit mit Netzwerkprotokollen entwickelt wurden und in der IT-Sicherheit eine zentrale Rolle spielen, insbesondere bei Penetrationstests und der Analyse von Windows-basierten Systemen. Diese Open-Source-Lösung, die von Core Security gepflegt wird, ermöglicht die Implementierung und Manipulation von Protokollen wie SMB, MSRPC, Kerberos und WMI, was sie zu einem unverzichtbaren Werkzeug für Sicherheitsforscher und Ethical Hacker macht, die Schwachstellen in Netzwerken aufdecken und ausnutzen wollen. Impacket bietet eine Reihe von Skripten, darunter secretsdump.py für die Extraktion von Credentials aus SAM-Dateien oder NTDS.dit, sowie smbexec.py für die Ausführung von Befehlen über SMB, und unterstützt damit eine breite Palette an Szenarien von der Authentifizierung bis hin zur Remote-Code-Ausführung.

Ein wesentlicher Vorteil von Impacket liegt in seiner Flexibilität und der Fähigkeit, legitime Windows-Funktionen zu missbrauchen, ohne dass zusätzliche Exploits benötigt werden, was es Angreifern ermöglicht, unauffällig in Domänen vorzudringen und sensible Daten wie Passwort-Hashes oder Kerberos-Tickets zu erbeuten. Da die Tools auf Python basieren, sind sie plattformübergreifend einsetzbar, etwa auf Kali Linux, und integrieren sich nahtlos in andere Frameworks wie Metasploit. Besonders gefährlich ist Impacket in den Händen von Cyberkriminellen, da es eine vollständige Kompromittierung von Netzwerken erleichtern kann, indem es Protokolle wie SMB für Lateral Movement nutzt, was zu Datenexfiltration oder Ransomware-Angriffen führen kann, ohne dass herkömmliche Sicherheitslösungen es sofort erkennen. Dennoch wird es ethisch von Sicherheitsprofis genutzt, um Schwachstellen zu identifizieren und Systeme zu härten, solange es verantwortungsvoll eingesetzt wird.

### Was ist Nmap

Nmap ist ein leistungsstarkes und weit verbreitetes Open-Source-Tool für die Netzwerkscanning und -Erkundung, das von Gordon Lyon entwickelt wurde und in der IT-Sicherheit als Standardwerkzeug für die Entdeckung von Hosts, offenen Ports und laufenden Diensten gilt. Als Network Mapper bezeichnet, sendet es gezielt Pakete an Zielsysteme und analysiert die Antworten, um detaillierte Informationen über die Netzwerktopologie zu sammeln, einschließlich Betriebssystemversionen, Service-Details und potenzieller Schwachstellen. Nmap unterstützt eine Vielzahl von Scan-Techniken, wie TCP-SYN-Scans für unauffällige Erkundungen oder UDP-Scans für die Überprüfung von offenen Ports, und kann mit Skripten aus dem NSE (Nmap Scripting Engine) erweitert werden, um automatisierte Vulnerabilitätschecks durchzuführen.

Da Nmap sowohl für kleine als auch für große Netzwerke skalierbar ist und Optionen wie Rate-Limiting bietet, um Entdeckung zu vermeiden, ist es ein essenzielles Tool für Penetrationstester, die Schwachstellen kartieren und Angriffsvektoren identifizieren wollen. Mit Befehlen wie "nmap -sS -p- [IP-Bereich]" können Administratoren offene Ports scannen und Dienste wie SMB oder RDP aufspüren, was hilft, Sicherheitslücken frühzeitig zu schließen. Besonders nützlich ist Nmap in der Reconnaissance-Phase von Angriffen, da es ohne hohe Rechte funktioniert und detaillierte Berichte erzeugt, die die Basis für weitere Exploits bilden können, was es zu einem doppelschneidigen Schwert macht – wertvoll für Defender, aber gefährlich, wenn es von Angreifern genutzt wird, um Netzwerke zu kompromittieren.

### Was ist Responder

Responder ist ein spezialisiertes Open-Source-Tool, das für das Poisoning von Namensauflösungsprotokollen wie LLMNR, NBT-NS und MDNS entwickelt wurde und in Penetrationstests häufig eingesetzt wird, um fehlgeschlagene DNS-Anfragen abzufangen und sensible Credentials zu erbeuten. Dieses von SpiderLabs erstellte Programm emuliert rogue Server, die auf Broadcast-Anfragen von Windows-Systemen reagieren, wenn eine DNS-Auflösung scheitert, und fordert NTLM-Authentifizierung an, um Hashes von Benutzernamen und Passwörtern zu capturen. Responder integriert Built-in-Server für HTTP, SMB, MSSQL, FTP und LDAP, die NTLMv1/v2-Hashes sammeln, und wird typischerweise mit Befehlen wie "responder -I eth0 -dw" gestartet, um auf einem Netzwerkinterface zu lauschen.

Da Responder auf standardmäßigen Windows-Verhaltensweisen basiert und keine Exploits benötigt, kann ein Angreifer damit leicht Hashes erbeuten, die offline geknackt werden, was es zu einer effektiven Methode für Credential-Access macht. Besonders gefährlich ist diese Technik in lokalen Netzwerken, da sie auf Poisoning fehlgeschlagener DNS-Anfragen abzielt und keine hohen Rechte erfordert, wodurch Angreifer unbemerkt bleiben können, bis sie Zugriff auf privilegierte Accounts erlangen – eine gängige Taktik in Active-Directory-Umgebungen, die durch Deaktivierung von LLMNR/NBT-NS abgewehrt werden kann.

### Was ist Evil-WinRM

Evil-WinRM ist ein fortschrittliches und benutzerfreundliches Shell-Tool für die Remote-Interaktion mit Windows-Systemen über das WinRM-Protokoll (Windows Remote Management), das speziell für Penetrationstests und Hacking-Szenarien entwickelt wurde und eine nahtlose Ausführung von Befehlen ermöglicht. Als Ruby-basiertes Skript, das auf Kali Linux läuft, implementiert es das WS-Management-Protokoll von Microsoft und unterstützt Features wie Datei-Uploads/Downloads, PowerShell-Skripte und Module-Laden, was es zu einem ultimativen Tool für Post-Exploitation macht. Evil-WinRM wird mit Befehlen wie "evil-winrm -i [IP] -u [User] -p [Pass]" gestartet und bietet eine interaktive Shell, die ähnlich wie SSH funktioniert, aber auf WinRM basiert.

Ein wesentlicher Vorteil von Evil-WinRM liegt in seiner Fähigkeit, verschlüsselte Verbindungen zu nutzen und administrative Aktionen auszuführen, ohne dass zusätzliche Software auf dem Zielsystem installiert werden muss. Besonders nützlich ist es nach der Kompromittierung von Credentials, da es Lateral Movement und Persistence ermöglicht, was Angreifern hilft, tiefer in Netzwerke vorzudringen – eine Technik, die in Active-Directory-Angriffen häufig vorkommt und durch strenge WinRM-Konfigurationen erschwert werden kann.

### Was ist Metasploit

Metasploit ist ein umfassendes Open-Source-Framework für die Entwicklung, Ausführung und Testung von Exploits, das von Rapid7 gepflegt wird und in der Penetrationstesting-Community als eines der mächtigsten Tools gilt, um Schwachstellen in Systemen aufzudecken und zu demonstrieren. Es enthält Tausende von Modulen, darunter Exploits für bekannte Vulnerabilitäten, Payloads wie Meterpreter für Reverse-Shells, Auxiliary-Module für Scanning und Post-Exploitation-Module für Persistence, und integriert sich mit Datenbanken für die Verwaltung von Hosts und Sessions. Metasploit wird über eine Konsole (msfconsole) bedient, wo Befehle wie "use exploit/windows/smb/ms17_010_eternalblue" ausgewählt und konfiguriert werden können, um Angriffe auf spezifische Ziele durchzuführen.

Da Metasploit eine modulare Architektur bietet und mit Tools wie Nmap oder Armitage kombiniert werden kann, ist es ideal für simulierte Angriffe, um Sicherheitslücken zu validieren. Besonders herausfordernd ist es jedoch bei den neuesten Windows-Versionen, da viele Exploits veraltet sind und keine funktionierenden Schwachstellen gefunden werden konnten, was zu Fehlschlägen führt und alternative Methoden wie Social Engineering oder Credential-Based-Angriffe erfordert – eine Einschränkung, die die Wichtigkeit aktueller Patches unterstreicht und Metasploit dennoch zu einem essenziellen Lernwerkzeug macht.




### Was ist ein IDS-System

Ein Intrusion Detection System (IDS) dient dazu, verdächtige Aktivitäten innerhalb eines Systems oder Netzwerks zu erkennen. IDS-Systeme analysieren Logdaten, Netzwerkverkehr oder Systemereignisse und schlagen Alarm, wenn Anomalien oder bekannte Angriffsmuster erkannt werden.

Man unterscheidet grundsätzlich zwischen hostbasierten IDS-Systemen (HIDS) und netzwerkbasierten IDS-Systemen (NIDS). In diesem Projekt wird ein hostbasiertes IDS verwendet, da insbesondere Angriffe auf Active Directory stark auf System- und Sicherheitslogs basieren.

### Wazuh

Wazuh ist ein quelloffenes, hostbasiertes Intrusion-Detection-System, das zur Überwachung einzelner Systeme eingesetzt wird. Die Architektur besteht aus einem zentralen Wazuh-Server sowie mehreren Wazuh-Agenten, welche auf den zu überwachenden Endgeräten installiert sind. Diese Agenten erfassen kontinuierlich Logdateien und sicherheitsrelevante Systemereignisse und übermitteln die gesammelten Daten an den Server. Dort werden sie zentral analysiert, korreliert und übersichtlich in einem Dashboard dargestellt.

Besonders für Windows-Umgebungen ist Wazuh gut geeignet, da es sicherheitsrelevante Windows-Events, Sysmon-Protokolle sowie Active-Directory-spezifische Ereignisse auswerten kann. Auf diese Weise lassen sich verdächtige Aktivitäten und bekannte Angriffstechniken, wie beispielsweise Kerberoasting oder DCSync, zuverlässig erkennen und nachvollziehen.


##Praktische Arbeit



### Aufbau der Laborumgebung

Die praktische Umsetzung dieses Projekts erfolgte in einer sorgfältig isolierten Active-Directory-Testumgebung, welche auf dem leistungsstarken und flexiblen Virtualisierungssystem Proxmox betrieben wurde, das sich durch seine Open-Source-Natur und umfangreiche Features für Homelabs und professionelle Setups eignet. Das primäre Ziel war es, einen hochgradig realistischen Unternehmensaufbau nachzubilden, der typische Strukturen und Konfigurationen widerspiegelt, und anschließend einen vollständigen, schrittweisen Angriffspfad zu demonstrieren, um Schwachstellen und Gegenmaßnahmen anschaulich zu machen. Diese Art von Laborumgebung ermöglicht es, risikofrei Experimente durchzuführen, ohne reale Produktionssysteme zu gefährden, und dient als wertvolles Lernwerkzeug für Sicherheitsfachkräfte und Administratoren.

Die Umgebung bestand aus folgenden sorgfältig konfigurierten virtuellen Maschinen, die jeweils spezifische Rollen übernahmen, um ein kohärentes Netzwerk zu simulieren:

*   **Domaincontroller**
    
    *   Betriebssystem: Windows Server 2019
        
    *   Hostname: WINSERVER-DOMAINCONTROLLER
        
    *   FQDN: winserver-domaincontroller.datelm.local
        
    *   IP-Adresse: 192.168.122.66
        
*   **Client**
    
    *   Betriebssystem: Windows 11
        
    *   Mitglied der Domäne datelm.local
        
    *   Standardbenutzer: maxmustermann
        
*   **Angreifer**
    
    *   Betriebssystem: Kali Linux
        
    *   Verwendete Tools: Impacket, Hashcat, evil-winrm
        

Zusätzlich wurden auf den Windows-Systemen Sysmon und Wazuh-Agenten installiert, um alle sicherheitsrelevanten Ereignisse zentral zu erfassen.

### Netzwerkreconnaissance mit Nmap

Bevor mit gezielten Angriffen begonnen wurde, führte der Angreifer eine umfassende Netzwerkreconnaissance durch, um offene Ports und erreichbare Dienste im simulierten Netzwerk zu identifizieren. Hierzu wurde das leistungsstarke Tool Nmap auf dem Kali-Linux-System eingesetzt, das als Standardwerkzeug für Port-Scans in Penetrationstests gilt und eine Vielzahl von Scan-Techniken unterstützt, darunter TCP-SYN-Scans für schnelle und unauffällige Erkundungen. Der Scan wurde so konfiguriert, dass er das gesamte Subnetz 192.168.122.0/24 abdeckte, um alle potenziellen Hosts zu entdecken, ohne unnötige Aufmerksamkeit zu erregen.

Mit Befehlen wie "nmap -sS 192.168.122.0/24" wurden alle 65.535 Ports auf offene TCP-Verbindungen überprüft, wobei der SYN-Scan-Modus verwendet wurde, um die Scans effizient und stealthy durchzuführen, da er keine vollständige TCP-Handschake erfordert und somit weniger Logs erzeugt. Die Ergebnisse zeigten offene Ports auf dem Domaincontroller, wie Port 445 für SMB, Port 389 für LDAP und Port 88 für Kerberos, sowie auf dem Client-Gerät Ports wie 3389 für RDP, was wertvolle Einblicke in die Netzwerktopologie und potenzielle Angriffsvektoren lieferte. Dieser Schritt ist essenziell in realen Szenarien, da er hilft, Schwachstellen zu kartieren und den Angriffspfad zu planen, ohne sofort invasive Maßnahmen zu ergreifen.

### Credential Capture mit Responder

Nach der Identifikation der Netzwerkkomponenten nutzte der Angreifer das Tool Responder auf Kali Linux, um eine LLMNR- und NBT-NS-Poisoning-Attacke durchzuführen, die darauf abzielt, fehlgeschlagene Namensauflösungsanfragen abzufangen und sensible Credentials zu erfassen. Responder wurde mit dem Befehl "responder -I eth0 -dw" gestartet, um auf dem Netzwerkinterface zu lauschen und rogue Server für LLMNR, NBT-NS und MDNS zu emulieren, die auf Anfragen von Windows-Systemen reagieren, wenn DNS-Auflösungen fehlschlagen

Um die Attacke auszulösen, wurde auf dem Client-Gerät eine absichtliche Fehlanfrage simuliert, z.B. durch den Versuch, auf eine nicht existierende Ressource wie "\bogusshare" zuzugreifen, was das System dazu veranlasste, auf LLMNR/NBT-NS zurückzugreifen und eine Broadcast-Anfrage zu senden. Responder poisonte diese Anfrage, indem es sich als der angefragte Host ausgab, und forderte NTLM-Authentifizierung an, wodurch der NTLM-Hash des Basisbenutzers maxmustermann erbeutet wurde. Dieser Hash konnte anschließend offline mit Tools wie Hashcat geknackt werden, um das Passwort Datelm25# zu rekonstruieren, was den Einstieg in die Domäne als normaler Benutzer ermöglichte. Diese Technik ist besonders effektiv in Windows-Netzwerken, da sie auf standardmäßigen Protokollen basiert und keine hohen Rechte erfordert, aber zu erheblichen Kompromittierungen führen kann, wenn nicht durch Gruppenrichtlinien deaktiviert.

### Ausgangssituation

Nach dem erfolgreichen Capture der Credentials stand dem Angreifer nun ein normaler, nicht privilegierter Domänenbenutzer zur Verfügung, der durch die obigen Schritte erlangt wurde:

Benutzername: maxmustermann
Passwort: Datelm25#

Dieser Benutzer besitzt keinerlei administrative Rechte oder erweiterte Berechtigungen, was ihn zu einem typischen Low-Privilege-Account macht. Dieses Szenario entspricht einem realistischen Angriffsfall, bei dem initiale Zugangsdaten durch Netzwerkpoisoning oder ähnliche Techniken erbeutet werden, und unterstreicht, wie Angreifer mit minimalem Ausgangszugang schrittweise eskalieren können.

### Durchführung des Kerberoasting-Angriffs

Zunächst wurde ein dedizierter Service Account mit einem zugehörigen Service Principal Name (SPN) im Active Directory konfiguriert, um eine authentische Umgebung zu schaffen. Service Accounts werden häufig für den Betrieb von Diensten wie Datenbanken oder Webservern verwendet und besitzen oft implizit oder explizit erhöhte Berechtigungen, was sie zu attraktiven Zielen macht.

Der Angreifer forderte mit einem standardmäßigen Kerberos-Request ein Service Ticket für diesen Account an, was ohne besondere Rechte möglich ist. Das erhaltene Ticket enthielt einen verschlüsselten Hash, der offline, also außerhalb des Netzwerks, analysiert werden konnte. Mithilfe des leistungsstarken Tools Hashcat wurde das Passwort des Service Accounts durch Brute-Force- oder Dictionary-Methoden erfolgreich rekonstruiert, oft innerhalb kurzer Zeit bei schwachen Passwörtern.

Dieser Schritt verdeutlicht eindringlich, wie gefährlich schwache oder vorhersagbare Passwörter bei Service Accounts sind, da der Angriff keine besondere Berechtigung erfordert, vollständig offline abläuft und somit schwer zu erkennen ist, ohne spezialisierte Monitoring-Lösungen.

### Privilegieneskalation mittels DCSync

Mit den nun kompromittierten Zugangsdaten des Service Accounts wurde ein DCSync-Angriff durchgeführt, der die legitime Replikationsfunktion von Active Directory ausnutzt. Dabei wurden Replikationsdaten direkt vom Domaincontroller angefordert, als ob es sich um eine normale Synchronisation zwischen Controllern handeln würde.

Als Ergebnis konnten sämtliche Passwort-Hashes der gesamten Domäne extrahiert werden, darunter auch der Hash des Administrators sowie des besonders kritischen krbtgt-Kontos, das für die Ticket-Signatur verantwortlich ist. Ab diesem Zeitpunkt war die Domäne als vollständig kompromittiert zu betrachten, da der Angreifer nun Zugriff auf alle sensiblen Credentials hatte und weitere Eskalationen einleiten konnte.

### Erstellen eines Golden Tickets

Anhand des extrahierten krbtgt-Hashes wurde ein Golden Ticket erzeugt, ein gefälschtes Kerberos Ticket Granting Ticket, das uneingeschränkten Zugriff ermöglicht. Dieses Ticket wurde speziell für den Administrator-Account erstellt und lokal auf dem Angreifersystem gespeichert, um es bei Bedarf zu verwenden.

Durch die Verwendung dieses Tickets war es möglich, sich als Domain Administrator auszugeben, ohne dass eine klassische Anmeldung am Domaincontroller erforderlich war oder Logs erzeugt wurden. Der Zugriff erfolgte vollständig über das Kerberos-Protokoll und war somit nur schwer zu erkennen, da es sich um eine legitime Authentifizierung handelt.

### Post-Exploitation und Persistenz

Nach der erfolgreichen Authentifizierung mit dem Golden Ticket konnten eine Vielzahl administrativer Aktionen im Netzwerk durchgeführt werden, die über die anfängliche Kompromittierung hinausgehen. Dazu gehörten unter anderem das Ausführen von Befehlen auf dem Domaincontroller, das Anlegen neuer Dienste für Backdoors oder das Manipulieren von Richtlinien, um langfristigen Zugriff zu sichern.

Dieser Schritt zeigt eindrucksvoll, wie Angreifer nach der initialen Kompromittierung langfristige Kontrolle über ein Netzwerk erlangen können, indem sie Persistence-Mechanismen etablieren, die eine Entdeckung erschweren und eine Wiederherstellung komplizieren.

### Erkennung durch Wazuh und Sysmon

Während des gesamten Angriffs wurden alle sicherheitsrelevanten Ereignisse durch die Kombination aus Sysmon für granulare Systemüberwachung und Wazuh für zentrale Log-Aggregation und -Analyse aufgezeichnet und in Echtzeit verarbeitet. Besonders auffällig waren dabei folgende Events, die typische Indikatoren für Angriffe darstellen:

	*Kerberos Service Ticket Requests (Event ID 4769), die auf ungewöhnliche Ticket-Anfragen hinweisen.

	*Directory Service Access Events (Event ID 4662), die Zugriffe auf sensible AD-Objekte protokollieren.	

	*Anmeldungen mit erhöhten Rechten (Event ID 4672), die Eskalationen signalisieren.

	*Zusätzlich erfasste Sysmon Netzwerkscans (Event ID 3) und ungewöhnliche Broadcast-Anfragen, die auf Poisoning-Angriffe hindeuten.

Diese Logs wurden im Wazuh-Dashboard korreliert, visualisiert und ermöglichten eine detaillierte, schrittweise Rekonstruktion des gesamten Angriffspfades, einschließlich Timestamps und beteiligter Entitäten, was für Incident Response essenziell ist.

## Fazit

Diese Arbeit zeigt, dass ein vollständiger Active-Directory-Angriff auch ohne klassische Exploits möglich ist. Fehlkonfigurationen, schwache Passwörter und übermäßige Berechtigungen reichen aus, um eine Domäne vollständig zu kompromittieren.

Gleichzeitig wird deutlich, dass solche Angriffe mit geeigneten Monitoring-Systemen erkennbar sind. Eine Kombination aus Härtung der Active-Directory-Konfiguration und zentralem Logging stellt eine essenzielle Grundlage für die Absicherung moderner Unternehmensnetzwerke dar.
