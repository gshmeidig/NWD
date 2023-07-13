# HF – NWD GNS3 Labor: VPN Technologien
![GNS3 Labor - VPN](.\Bilder/GNS3LaborVPN.png)
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

/system identity 
set name=LS-R1

/ip address 
add address=203.0.113.70/30 interface=ether1 network=203.0.113.69

/ip route 
add dst-address=0.0.0.0/0 gateway=203.0.113.69

/ip dns
set allow-remote-requests=yes servers=8.8.8.8

/ip address 
add address=192.168.13.1/24 interface=ether2 network=192.168.13.0

/ip pool
add name=dhcp_pool1 ranges=192.168.13.50-192.168.13.100

/ip dhcp-server network
add address=192.168.13.0/24 dns-server=192.168.13.1 gateway=192.168.13.1

/ip dhcp-server/
add address-pool=dhcp_pool1 interface=ether2 name=dhcp1

/ip firewall nat
add action=masquerade chain=srcnat out-interface=ether1

###########################Site to Site IPsec tunnel (LS to BS)

add chain=forward action=accept place-before=0 src-address=192.168.11.0/24 dst-address=192.168.13.0/24 connection-state=established,related
add chain=forward action=accept place-before=1 src-address=192.168.13.0/24 dst-address=192.168.11.0/24 connection-state=established,related

add action=notrack chain=prerouting src-address=192.168.13.0/24 dst-address=192.168.11.0/24
add action=notrack chain=prerouting src-address=192.168.11.0/24 dst-address=192.168.13.0/24


###########################Site to Site WireGuard tunnel (LS to ZH)

#### interface configuration:

##LS-R1
/interface/wireguard
add listen-port=13234 name=wireguardZH

/interface/wireguard print
 1  R name="wireguardZH" mtu=1420 listen-port=13234 private-key="oGDJYeJg+kcUjqZUa0bw3BpWhsvPh2HdT5iGFBS20l4="
      public-key="lZexpEtJY2Pdb4X0oC7D63iOTMZqziYirHybnePaXkg="


##ZH-R1
add listen-port=13234 name=wireguardLS

/interface/wireguard print
 1  R name="wireguardLS" mtu=1420 listen-port=13234 private-key="sJMJVT6w2YoK3Ruv5Z8HJklst6djLLZnOlnuEBk4DWs="
      public-key="yWwRYBChRvZOTiBdGKaxaq5+R9eFslvoMIHdDOljGiE="

####Peer configuration

##LS-R1
/interface/wireguard/peers
add allowed-address=192.168.9.0/24 endpoint-address=203.0.113.98 endpoint-port=13234 interface=wireguardZH \
public-key="yWwRYBChRvZOTiBdGKaxaq5+R9eFslvoMIHdDOljGiE="
#Public Key von Zürich

##ZH-R1-R1
/interface/wireguard/peers
add allowed-address=192.168.13.0/24 endpoint-address=203.0.113.70 endpoint-port=13234 interface=wireguardLS \
public-key="lZexpEtJY2Pdb4X0oC7D63iOTMZqziYirHybnePaXkg="
#Public Key von Lausanne

####IP and routing configuration

##LS-R1
/ip/address
add address=192.168.250.1/30 interface=wireguardZH
/ip/route
add dst-address=192.168.9.0/24 gateway=wireguardZH

##ZH-R1
/ip/address
add address=192.168.250.1/30 interface=wireguardLS
/ip/route
add dst-address=192.168.13.0/24 gateway=wireguardLS

####Firewall considerations

##LS-R1
/ip/firewall/filter
add action=accept chain=input dst-port=13234 protocol=udp src-address=203.0.113.98
add action=accept chain=input dst-port=13234 protocol=udp src-address=192.168.250.2
add action=accept chain=forward dst-address=192.168.9.0/24 src-address=192.168.13.0/24
add action=accept chain=forward dst-address=192.168.13.0/24 src-address=192.168.9.0/24


##ZH-R1
/ip/firewall/filter
add action=accept chain=input dst-port=13234 protocol=udp src-address=203.0.113.70
add action=accept chain=input dst-port=13234 protocol=udp src-address=192.168.250.1
add action=accept chain=forward dst-address=192.168.13.0/24 src-address=192.168.9.0/24
add action=accept chain=forward dst-address=192.168.9.0/24 src-address=192.168.13.0/24



## Glossar

### OSPF (Open Shortest Path First)
<p>OSPF (Open Shortest Path First) ist das Router-Protokoll, das verwendet wird, um den Weg zu ermitteln, mit dem die Pakete am effizientesten durch die verschiedenen verbundenen Netzwerke transportiert werden können.</p>
<p>Bei Verwendung von OSPF sendet ein Router, sobald er feststellt, dass es eine Änderung in den Routing-Tabellen gegeben hat (weil zum Beispiel das Netzwerk neu konfiguriert wurde), diese Information an alle anderen OSPF-Hosts innerhalb des Netzwerks, so dass alle über identische Routing-Tabellen verfügen.</p>

### iBGP (Internal Border Gateway Protocol)
<p>iBGP wird verwendet, um Informationen für Ihre internen Router bereitzustellen. iBGP erfordert, dass alle Geräte im selben autonomen System eine vollständige Mesh-Nachbarschaft oder entweder einen Routenreflektor oder eine Konföderation für das Präfix-Lernen bilden.</p>

<p>