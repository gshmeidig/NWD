# HF – NWD GNS3 Labor: VPN Technologien

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

## Glossar

### OSPF (Open Shortest Path First)
<p>OSPF (Open Shortest Path First) ist das Router-Protokoll, das verwendet wird, um den Weg zu ermitteln, mit dem die Pakete am effizientesten durch die verschiedenen verbundenen Netzwerke transportiert werden können.</p>
<p>Bei Verwendung von OSPF sendet ein Router, sobald er feststellt, dass es eine Änderung in den Routing-Tabellen gegeben hat (weil zum Beispiel das Netzwerk neu konfiguriert wurde), diese Information an alle anderen OSPF-Hosts innerhalb des Netzwerks, so dass alle über identische Routing-Tabellen verfügen.</p>

### iBGP (Internal Border Gateway Protocol)
<p>iBGP wird verwendet, um Informationen für Ihre internen Router bereitzustellen. iBGP erfordert, dass alle Geräte im selben autonomen System eine vollständige Mesh-Nachbarschaft oder entweder einen Routenreflektor oder eine Konföderation für das Präfix-Lernen bilden.</p>