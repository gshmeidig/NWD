# HF – NWD GNS3 Labor: VPN Technologien
![GNS3 Labor - VPN](/Bilder/GNS3LaborVPN.png)

## Auftrag

### 1 Einleitung
Sie haben als Netzwerkingenieur den Auftrag erhalten in einem KMU einen zusätzlichen Geschäftsstandort per VPN zu
erschliessen. Das KMU hat keinen eigenen Betriebsinformatiker. Jedes Mal, wenn eine Erweiterung des Netzwerkes
benötigt wurde, hat das KMU eine andere IT-Firma beauftrag. Das hat zur Folge, dass überall unterschiedliche Geräte und
VPN-Technologien eingesetzt wurden. Das ist eine optimale Gelegenheit, um neue VPN-Technologien kennenzulernen
und zu vergleichen!
Die Wahl des Gerätes für Lausanne steht Ihnen frei. Alle anderen Standorte haben einen funktionierenden
Internetanschluss und eine funktionierende VPN-Verbindung an den Hauptstandort in Zürich. In der Mitte finden Sie ein
Netzwerk eines fiktiven ISP. Der verwendet OSPF als internes Routing-Protokoll (iBGP eignet sich für ISP besser). Über den
ISP können sie auch auf das Internet zugreifen.
Lernziele:
- Unterschiedliche VPN-Technologien kennenlernen
- VPN auf einem Router konfigurieren, testen und dokumentieren
Die messbaren Ziele sind direkt im GNS3 Projekt zu finden (siehe Screenshot oben)

### 2 Themengebite
Diese Laborübung beinhaltet folgende Themengebiete:
- Kernthema: VPN Technologien OpenVPN, Wireguard, IPsec
- IP-Protokolle, namentlich IPv4 und IPv6
- Standardprotokolle wie HTTP, DHCP, DNS, ARP, ICMP, usw.
- Bedienung bzw. Konfiguration und Steuerung von Netzwerkgeräten und Server über die CLI
- Betriebssysteme: Cisco IOS, MikroTik RouterOS, pfsense
- Netzwerkdokumentation

### 3 Allgemeine Instruktion
Bitte lesen Sie diese Instruktionen sorgfältig durch und fragen Sie bei Unklarheiten den Kursleiter.
In diesem Modul arbeiten Sie mit der Netzwerksimulationssoftware GNS3, mit der Sie per Drag-and-Drop Topologien in Sekundenschnelle aufbauen können. Im Hintergrund arbeitet GNS3 mit Qemu-KVM VMs für die Switche und Router und verbindet diese bezüglich Ihrer Topologie mit Linux-Bridges. Weitere Informationen zum Aufbau der TBZ Cloud Infrastruktur finden Sie im Repository https://gitlab.com/ch-tbz-it/Stud/allgemein/tbzcloud-gns3
Sie arbeiten jeweils in Zweier-Teams am selben Labor auf demselben Server bzw. derselben TBZ Cloud GNS3 Instanz. Wie Sie eine Verbindung zu Ihrer Instanz aufbauen können, erfahren Sie unter https://gitlab.com/ch-tbzit/Stud/allgemein/bzcloud-gns3/-/tree/main/02_Bedienungsanleitung . Den OpenVPN Key zu Ihrer Instanz erhalten Sie vom Kursleiter.
Damit Sie die Aufgaben lösen können, müssen Sie selbstständig im Internet recherchieren. Nicht alle notwendigen
Informationen sind in diesem Dokument vorhanden.
Folgende Zugangsdaten sind bekannt:
- MikroTik: Benutzername: admin, Passwort: tbz1234
- Debian: Benutzername: debian, Passwort: debian
- Cisco: Passwort: tbz1234
- Standardpasswörter zum Ausprobieren: cisco, debian, admin1234, admin

### 4 Aufgaben
#### 4.1 VPN Technologien per Packet Capture analysieren
Die drei verwendeten VPN-Technologien bauen auf unterschiedlichen Netzwerkstacks auf. Analysieren Sie die
unterschiedlichen Protokolle mithilfe von Wireshark Captures und halten Sie Unterschiede in den Netzwerkstacks fest.
Beantworten Sie mithilfe der Packet Caputes zusätzlich folgende Fragen in Ihrem Bericht: Weshalb kann IPSec und NAT
ein Problem darstellen?
#### 4.2 Neuen Standort Anbinden
1. Lesen Sie die Anforderungen an das Netzwerk und das Ziel. Entscheiden Sie sich für einen Router-Typ und richten das Gerät ein.
2. Richten Sie den Zugriff für Worker1 ein. Worker1 hat bereits via OpenVPN und Wireguard Zugriff auf zwei Standorte.
3. Testen und Konfigurieren Sie so lange bis alle Anforderungen erfüllt sind.
4. Dokumentieren Sie alle getätigten Konfigurationen so, dass eine andere Fachperson Ihre Konfiguration möglichst
schnell nachbauen kann und versteht, was sie dabei tut (Dazu gehört unter anderen auch, dass sie z.B. alle Befehle per Copy-Paste einfügen kann)

Wenn Sie den Bericht abgeben, muss ihr Netzwerk in einem funktionsfähigen Zustand sein. Der Kursleiter wird nebst dem
Bericht auch ihr GNS3 Labor überprüfen.

### 5 Hinweise zur Dokumentation
- Beschränken Sie sich auf das Wesentliche. Unterlassen Sie es leere Sätze oder persönliche Statements zu schreiben. Fokussieren Sie sich auf die Sachlage.
- Nachvollziehbarkeit: Anhand ihrer Dokumentation müssen Dritte in der Lage sein, alles exakt genau gleich nachbauen zu können.
- Erstellen Sie pro Gruppe ein eigenes privates Repository mit dem Namen HF_NWD und pushen Sie dieses auf GitLab (Alternativ GitHub). Gewähren Sie der Lehrperson den Zugriff auf das Repository.
- Machen Sie bei der Abgabe einen Export des aktuellen Repository-Standes und geben diesen als ZIP-File via Teams-Aufgabe ab.
- Die gesamte Dokumentation muss in Markdown erfolgen. Fügen Sie erstellte Netzwerktopologien als Grafiken ein.
- Alle Grafiken sind scharf und müssen gut zu lesen sein.
- Als Inspiration können Sie die Vorlagen von diesem Repository verwenden: https://gitlab.com/alptbz/beispiellernjournal-fuer-laboruebungen. Lassen Sie die Reflexion und das aufführen ihrer neuen Lerninhalte weg.

### 6 Regeln
- Es dürfen keine Geräte entfernt oder hinzugefügt werden – ausser am Standort Lausanne.
- Es ist erlaubt zu Testzwecken z.B. ein Ubuntu Desktop an einem Port anzuschliessen – wie wenn Sie ein Laptop an einem «echten» Router oder Switch einstecken.
- Alle Kabelverbindungen zwischen den Geräten sind fix. Erstellen Sie keine neuen (Ausser die für Lausanne – siehe Hinweis im GNS3 Projekt).

### 7 Bewertungskriterien und Abgabetermin
Informieren Sie sich bei der Kursleitung betreffend Abgabetermin und Bewertungskriterien. Zu spät abgegebene (bis 24h)
Arbeiten erhalten Abzug nach Ermessen der Kursleitung. 24 Stunden nach dem Abgabetermin werden keine Arbeiten
akzeptiert und die Aufgabe gilt als nicht erfüllt.

# Dokumentation

## VPN Technologien analysiert

## VPN Frage
### Weshalb kann IPSec und NAT ein Problem darstellen?
<p>
IPSec (Internet Protocol Security) und NAT (Network Address Translation) können in bestimmten Szenarien zu Problemen führen, da sie unterschiedliche Ansätze zur Verarbeitung von IP-Paketen verfolgen.

IPSec ist ein Protokollsuite, das verwendet wird, um die Kommunikation über IP-Netzwerke abzusichern. Es bietet Vertraulichkeit, Integrität und Authentizität der übertragenen Daten. IPSec verschlüsselt die IP-Pakete und fügt zusätzliche Headerinformationen hinzu, um die Sicherheit zu gewährleisten. Diese Änderungen an den Paketen können sich jedoch auf die Fähigkeit von NAT auswirken, sie ordnungsgemäß zu verarbeiten.

NAT wiederum ist eine Technik, bei der private IP-Adressen in öffentliche IP-Adressen umgewandelt werden, um den Internetzugriff für Geräte in einem lokalen Netzwerk zu ermöglichen. NAT führt Änderungen an den IP-Headern durch, um die Adressübersetzung durchzuführen. Dabei werden die Quell- und Zieladressen der IP-Pakete geändert. Dies kann Konflikte mit den zusätzlichen IPSec-Headern verursachen, da NAT die ursprünglichen IP-Adressen ändert, die für die IPSec-Sicherheitsmechanismen wichtig sind.

Das Hauptproblem besteht darin, dass IPSec in den meisten Fällen vor der NAT-Verarbeitung angewendet werden sollte, da die Sicherheitseigenschaften von IPSec auf den ursprünglichen IP-Adressen basieren. Wenn NAT jedoch zuerst angewendet wird, bevor IPSec die Pakete erreicht, kann es zu Konflikten kommen. Die Änderungen durch NAT können die IPSec-Header unleserlich machen oder die Sicherheitsmechanismen von IPSec beeinträchtigen.

Es gibt jedoch Techniken wie NAT-Traversal (NAT-T), die entwickelt wurden, um diese Probleme zu überwinden. NAT-T ermöglicht die Verwendung von IPSec über NAT-Geräten, indem es den IPSec-Traffic so modifiziert, dass er über NAT-Geräte hinweg geleitet werden kann, ohne die Integrität und Authentizität der Daten zu beeinträchtigen. NAT-T fügt zusätzliche Protokollinformationen hinzu, um die Kommunikation zwischen den IPSec-Endpunkten zu ermöglichen, selbst wenn NAT beteiligt ist.

Insgesamt erfordert die Kombination von IPSec und NAT eine sorgfältige Konfiguration und gegebenenfalls den Einsatz von Techniken wie NAT-T, um sicherzustellen, dass sowohl die Sicherheitsanforderungen von IPSec als auch die Funktionen von NAT erfüllt werden.
</p>

## Dokumentation

<p>Der Standort Lausanne ist wie folgt konfiguriert:<p>

Zuerst haben wir den Namen für den Router mit folgendem Befehl gesetzt:

    /system identity
    set name=LS-R1
<br>
Anschliessend muss die IP Adresse gesetzt werden.
Für das Interface "ether1" haben wir die IP Adresse 203.0.113.70 mit der CIDR 30 gesetzt.
Mit dem "network" wird sozusagen das Gateway "203.0.113.69" definiert.

    /ip address 
    add address=203.0.113.70/30 interface=ether1 network=203.0.113.69
<br>
Das Routing wird hier definiert. mit dst-address wird das Zielnetzwerk definiert bzw die Standardroute wo die Pakete weitergeleitet werden.

    /ip route 
    add dst-address=0.0.0.0/0 gateway=203.0.113.69
<br>
Als nächstes wird die DNS konfiguriert.
Dafür gibt es die beiden Befehle "set allow-remote-requests" und "servers"

Mit "allow-remote-requests=yes" wird gesetzt, dass externe Geräte DNS-Anfragen über diesen Router stellen können. Somit kann der Router DNS-Anfragen von externen Quellen beantworten.

    /ip dns
    set allow-remote-requests=yes servers=8.8.8.8
<br>
Hier wird eine zusätzliche IP Adresse gesetzt aber für das interrface "ether2".

    /ip address 
    add address=192.168.13.1/24 interface=ether2 network=192.168.13.0
<br>
Im Verzeichnis /ip pool
add name=dhcp_pool1 wird der Name gesetzt
Der IP Pool wird gesetzt mit dem Range von 192.168.13.50 bis 192.168.13.100.
Somit wird über den DHCP Server des Routers die IP Adresse der Geräte in diesem Range dynamisch gesetzt

    /ip pool
    add name=dhcp_pool1 ranges=192.168.13.50-192.168.13.100
<br>
Nun werden die Parameter für den DHCP-Server Netzwerk gesetzt

Mit "adress" wird die IP Adresse inkl. CIDR 24 gesetzt<br>
Mit DNS-Server wird die Adresse vom DNS Server gesetzt und mit gateway natürlich die Gateway Adresse.

    ip dhcp-server network
    add address=192.168.13.0/24 dns-server=192.168.13.1 gateway=192.168.13.1
<br>
Mit "address-pool=dhcp_pool1" wird der Adress Pool festgelegt und gilt für den Interface "ether2".
Zusätzlich wird der Name "dhcp1" festgelegt.

    /ip dhcp-server/
    add address-pool=dhcp_pool1 interface=ether2 name=dhcp1
<br>
Mit "action=masquerade" wird der Datenverkehr verschleiert.

mit "chain=srcnat" wird die Firewall-Kette angegeben. Wir haben sie in den "srcnat"Kette platziert, die für den ausgehenden Datenverkehr verwendet wird.

Konfigurationen für die Firewall NAT werden festgelegt, um den ausgehenden Verkehr zu regeln.
mit "out-interface=ether1" wird der Ausgangsinterface definiert bzw über welchen interface er die Verschleierung anwenden soll.

    /ip firewall nat
    add action=masquerade chain=srcnat out-interface=ether1
<br>

### IPsec Site to Site - Lausanne to Basel
Alle Konfigurationen wurden über das Terminal getätigt. Mit dem Interface werden manchmal unnötige Einstellungen aktivert, welche man nur über das Terminal löschen kann.

#### Konfiguration Router Lausanne - LS-R1

Als aller erst wird ein IPsec Profile erstellt. Dabei werden mittels "dh-group" die Verhandlungsmethode für den Schlüsselaustausch gewählt und danach den Verschlüsselungsalgorithmus gewält.

    /ip ipsec profile
    add dh-group=modp2048 enc-algorithm=aes-128 name=ike1-BS
<br>
Nun wird der Proposal erstellt, in welchem ebenfalls die Verhandlungsmethode und Verschlüsselungsalgorithmus eingestllt wird.

    /ip ipsec proposal
    add enc-algorithms=aes-128-cbc name=ike1-BS pfs-group=modp2048
<br>
Weiter wird die so gennante "Gegenstelle" das Peer konfiguriert. Dabei wird die IP des zuerreichenden Router eingegeben.
    /ip ipsec peer
    add address=203.0.113.82/32 name=ike1-BS profile=ike1-BS
<br>
Als näcshter Schritt wird die "Identity" erstellt, wobei ein gemeinsamen sogennanten "Pre-Shared Key" defineirt wrid. Der Pre-Shared Key wird ebenfalls auf dem entfernten Router hinterlegt.

    /ip ipsec identity
    add peer=ike1-BS secret=tbz1234
<br>
Weiter wird eine Richtlinie erstellen, die die Netze/Hosts steuert, zwischen denen der Datenverkehr verschlüsselt werden soll.

    /ip ipsec policy
    add dst-address=192.168.11.0/24 peer=ike1-BS proposal=ike1-BS src-address=192.168.13.0/24 tunnel=yes
<br>
Nun wird zwar der IPsec Tunnel aufgebaut, jeodch können noch keine Daten über den IPsec-Tunnel gesendet werden.
Dies liegt daran, dass beide Router NAT-Regeln (Masquerade) haben, die die Quelladressen ändern, bevor ein Paket verschlüsselt wird. Der Router ist nicht in der Lage, das Paket zu verschlüsseln, weil die Quelladresse nicht mit der in der Richtlinienkonfiguration angegebenen Adresse übereinstimmt.

Um dies zu beheben, müssen wir eine IP/Firewall/NAT-Umgehungsregel einrichten.
Dabei ist es sehr wichtig, dass die Bypass-Regel an erster Stelle aller anderen NAT-Regeln steht.

    /ip firewall nat
    add action=accept chain=srcnat dst-address=192.168.11.0/24 src-address=192.168.13.0/24
<br>
Ein weiteres Problem ist, dass bei aktiviertem IP/Fasttrack das Paket die IPsec-Richtlinien umgeht. Wir müssen also eine Akzeptanzregel vor FastTrack hinzufügen.

    /ip firewall filter
    add chain=forward action=accept place-before=0 src-address=192.168.11.0/24 dst-address=192.168.13.0/24 connection-state=established,related
    add chain=forward action=accept place-before=1 src-address=192.168.13.0/24 dst-address=192.168.11.0/24 connection-state=established,related
<br>
Dies kann jedoch zu einer erheblichen Belastung der CPU des Routers führen, wenn eine größere Anzahl von Tunneln und erheblicher Datenverkehr in jedem Tunnel vorhanden sind.
Um dies entgegen zu wirken kann die Verbindungsverfolgung Umgangen werden.

    /ip firewall raw
    add action=notrack chain=prerouting src-address=192.168.13.0/24 dst-address=192.168.11.0/24
<br>

#### Konfiguration Router Basel - BS-R1
Bei dem Router in Basel müssen die geleichen Einstellungen wie bei Lausanne vorgenommen werden. Dabei muss aber darauf geachtet werden, dass spezifische Einstellungen wie IP oder Public- Private-Keys.

    /ip ipsec profile  
    add dh-group=modp2048 enc-algorithm=aes-128 name=ike1-LS

    /ip ipsec proposal
    add enc-algorithms=aes-128-cbc name=ike1-LS pfs-group=modp2048

    /ip ipsec peer
    add address=203.0.113.70/32 name=ike1-LS profile=ike1-LS

    /ip ipsec identity
    add peer=ike1-LS

    /ip ipsec policy
    add dst-address=192.168.13.0/24 peer=ike1-LS proposal=ike1-LS src-address=192.168.11.0/24 tunnel=yes

    /ip firewall nat
    add action=accept chain=srcnat dst-address=192.168.13.0/24 src-address=192.168.11.0/24

    /ip firewall filter
    add chain=forward action=accept place-before=0 src-address=192.168.11.0/24 dst-address=192.168.13.0/24 connection-state=established,related
    add chain=forward action=accept place-before=1 src-address=192.168.13.0/24 dst-address=192.168.11.0/24 connection-state=established,related

    /ip firewall raw
    add action=notrack chain=prerouting src-address=192.168.11.0/24 dst-address=192.168.13.0/24

### Site to Site WireGuard - Lausanne to Zürich
Anhand der folgenden Anleitung 
https://help.mikrotik.com/docs/display/ROS/WireGuard

#### WireGuard interface configuration:

Im Prinzip müssen beide Routers (LS-R1 und ZH-R1) konfiguriert werden, sodass die Private und Public Keys automatisch generiert werden.

Der gesetzte Listen-Port muss bei beiden der gleiche sein (in unserem Fall "13234")

#### LS-R1

    /interface/wireguard
    add listen-port=13234 name=wireguardZH

    /interface/wireguard print
    name="wireguardZH" mtu=1420 listen-port=13234 private-key="oGDJYeJg+kcUjqZUa0bw3BpWhsvPh2HdT5iGFBS20l4="public-key="lZexpEtJY2Pdb4X0oC7D63iOTMZqziYirHybnePaXkg="

#### ZH-R1

    add listen-port=13234 name=wireguardLS

    /interface/wireguard print
    name="wireguardLS" mtu=1420 listen-port=13234 private-key="sJMJVT6w2YoK3Ruv5Z8HJklst6djLLZnOlnuEBk4DWs="public-key="yWwRYBChRvZOTiBdGKaxaq5+R9eFslvoMIHdDOljGiE="

#### Peer configuration

Die Peer configuration definiert, wer die WireGuard-Schnittstelle nutzen kann und welche Art von Datenverkehr darüber gesendet werden kann.
Um die Gegenstelle zu identifizieren, muss ihr öffentlicher Schlüssel zusammen mit der erstellten WireGuard-Schnittstelle angegeben werden.s

#### LS-R1

    /interface/wireguard/peers
    add allowed-address=192.168.9.0/24 endpoint-address=203.0.113.98 endpoint-port=13234 interface=wireguardZH \
    public-key="yWwRYBChRvZOTiBdGKaxaq5+R9eFslvoMIHdDOljGiE="
    #Public Key von Zürich

#### ZH-R1

    /interface/wireguard/peers
    add allowed-address=192.168.13.0/24 endpoint-address=203.0.113.70 endpoint-port=13234 interface=wireguardLS \
    public-key="lZexpEtJY2Pdb4X0oC7D63iOTMZqziYirHybnePaXkg="
    #Public Key von Lausanne

#### IP and routing configuration

Zum Schluss müssen die IP und Routing Informationen konfiguriert werden, um den Datenverekhr über den Tunnel zu ermöglichen

#### LS-R1

    /ip/address
    add address=192.168.250.1/30 interface=wireguardZH
    /ip/route
    add dst-address=192.168.9.0/24 gateway=wireguardZH

#### ZH-R1

    /ip/address
    add address=192.168.250.1/30 interface=wireguardLS
    /ip/route
    add dst-address=192.168.13.0/24 gateway=wireguardLS

#### Firewall considerations
Bei der Firewall müssen auch noch Einstellungen vorgenommen werden. Standardmässig wird der Tunnel blockiert und somit müssen die Input-Chains von beiden Seiten akzeptiert, um die Kommunikation zu gewährleisten.

#### LS-R1

    /ip/firewall/filter
    add action=accept chain=input dst-port=13234 protocol=udp src-address=203.0.113.98
    add action=accept chain=input dst-port=13234 protocol=udp src-address=192.168.250.2
    add action=accept chain=forward dst-address=192.168.9.0/24 src-address=192.168.13.0/24
    add action=accept chain=forward dst-address=192.168.13.0/24 src-address=192.168.9.0/24

#### ZH-R1

    /ip/firewall/filter
    add action=accept chain=input dst-port=13234 protocol=udp src-address=203.0.113.70
    add action=accept chain=input dst-port=13234 protocol=udp src-address=192.168.250.1
    add action=accept chain=forward dst-address=192.168.13.0/24 src-address=192.168.9.0/24
    add action=accept chain=forward dst-address=192.168.9.0/24 src-address=192.168.13.0/24

### RoadWarrior WireGuard tunnel - Worker1 to Lausanne

#### Router Lausanne
Zuerst muss ein WireGuard Interface konfiguriert und die IP Adresse definiert werden.

    /interface wireguard
    add listen-port=13233 mtu=1420 name=MTW_LS
    /ip address
    add address=192.168.14.1/24 interface=MTW_LS network=192.168.14.0
<br>
Danach müssen die interface wireguard peers gesetzt. Somit wird bei "allowed-address" die erlaubte IP Adresse definiert, welche über den interface (in unserem Fall "MTW_LS) erlaubt wird.

    /interface wireguard peers
    add allowed-address=192.168.14.2/32 interface=MTW_LS public-key=\
    "9nSj/xiApoAJrZX99+EwJuiDH5Xp5WZrD2ceCecGrgc="
<br>
Damit die Verbindung nicht von der Firewall blockiert wird, erstellen wir noch die folgende Regel wleche Daten über das UDP Protkoll auf dem Port 13233 akzepriert.

    /ip firewall filter
    add action=accept chain=input comment="allow WireGuard" dst-port=13233 protocol=udp place-before=1
<br>
Nun erlauben wir den Geräten via RoadWarrior zugriff auf die Dienste des Routers

    /ip firewall filter
    add action=accept chain=input comment="allow WireGuard traffic" src-address=192.168.14.0/24 place-before=1

#### Wiregurad Client Worker1
Das Konfigurationfile des Worker1 ist wie folgt:

![Konfiguration RoadWarrior Worker1](/Bilder/Konfig_RoadWarrior_Worker1.png)

### Debian Sever
#### User erstellen
User für den Share zugriff erstellen:

    sudo useradd worker1
<br>
Passwort für den User feslegen

    sudo passwd worker1 

    tbz1234

#### FileShare Dienst installieren -  Samba
Samba Server installieren

    sudo apt-get install samba
<br>
Erstellter User der Samba DB hinzufügen

    sudo smbpasswd -a worker1

    tbz1234
<br>
User wechslen zu Root User

    sudo -s
<br>
Nun den Ordner für die Freigabe erstellen.

    mkdir /home/worker/shared_folder
<br>
Nun mmuss noch der Besitzer und die Zugriffberechtigung angepasst werden

    chown worker1 shared_folder
    chgrp worker1 shared_folder

Konfigurations-File öffnen

    sudo nano /etc/samba/smb.conf
<br>
Folgende parameter in die Konfigurationsdatei eintragen und gespeichert werden

    [shared_folder]
    path = /home/worker/shared_folder
    readonly = no
    inherit permisson = yes

<br>
zum Abschluss muss der Samba-Service neugestartet werden

    service smbd restart

#### Laufwerk verbinden Worker1
Um das Laufwerk für den Worker1 zu verbinden, muss der Explorer geöffnet werden und danach über Rechtsklick auf "Network" die Optione "Map network device..." ausgewählt werden.
![Konfiguration RoadWarrior Worker1](/Bilder/MapND.png)
<br>
Nun muss der Pfad zum Freigegebnen Ordner angegeben werden, in diesem Fall also

    \\192.168.13.96\shared_folder

Zu beachten ist noch das die zwei Optionen unterhalb, also "Reconnect after sign-in" und "Connect using different credentials" ausgewählt sind.
![Konfiguration RoadWarrior Worker1](/Bilder/MapND_Destination.png)
<br>
Beim Anmeldefenster den vorherigen erstllten User Benutzern. Es ist zu beachten das vor dem User auf den Debian Server mit "192.168.13.96\" verwiesen werden muss.

![Konfiguration RoadWarrior Worker1](/Bilder/MapND_Cred.png)
<br>
Wenn das Verbinden erfolgreich war, öffnet sich dies in einem neuen Fenster.

![Konfiguration RoadWarrior Worker1](/Bilder/MapND_Succees.png)

## Glossar

### OSPF (Open Shortest Path First)
<p>OSPF (Open Shortest Path First) ist das Router-Protokoll, das verwendet wird, um den Weg zu ermitteln, mit dem die Pakete am effizientesten durch die verschiedenen verbundenen Netzwerke transportiert werden können.</p>
<p>Bei Verwendung von OSPF sendet ein Router, sobald er feststellt, dass es eine Änderung in den Routing-Tabellen gegeben hat (weil zum Beispiel das Netzwerk neu konfiguriert wurde), diese Information an alle anderen OSPF-Hosts innerhalb des Netzwerks, so dass alle über identische Routing-Tabellen verfügen.</p>

### iBGP (Internal Border Gateway Protocol)
<p>iBGP wird verwendet, um Informationen für Ihre internen Router bereitzustellen. iBGP erfordert, dass alle Geräte im selben autonomen System eine vollständige Mesh-Nachbarschaft oder entweder einen Routenreflektor oder eine Konföderation für das Präfix-Lernen bilden.</p>
