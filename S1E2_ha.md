# Hochverfügbarkeit

Mit ROKS kann ein OpenShift-Cluster sehr einfach über die drei Rechenzentren (sog. Verfügbarkeitszonen/Availability Zones/AZ) einer sog. Multi-Zone-Region (MZR) in der IBM Cloud, z.B. in Frankfurt, verteilt werden.

Die OpenShift Master werden dabei IMMER hochverfügbar bereitgestellt, d.h. ich bekomme bei ROKS immer drei Master, die in einer MZR über alle drei AZs verteilt sind, auch wenn ich nur einen Worker bestelle. 
Bei den Workern bestimme ich als Kunde über die Verteilung und kann mich entscheiden meine Worker über 1, 2 oder 3 Zonen innerhalb einer Region zu verteilen.
Eine regions-übergreifende Verteilung ist nicht möglich, könnte aber durch zwei getrennte Cluster und einen davor geschaltenen globalen Loadbalancer realisiert werden (z.B. Cloud Internet Services in der IBM Cloud).
ROKS unterscheidet nicht zwischen Worker- und Infrastruktur-Knoten, es gibt nur Worker-Knoten. 

Die Master laufen dabei in einem IBM Service Account, während die Worker in einem Kunden Cloud Account laufen (entweder auf der sog. Classic oder der Virtual Private Cloud (VPC) Infrastruktur).
Die Kommunikation von den Mastern (die kunden- und cluster-dediziert aufgebaut sind) mit den Workern, zwischen den beiden Accounts, erfolgt über eine automatisch aufgesetzte VPN-Verbindung.

Inerhalb eines ROKS-Clusters können verschiedene Worker Pools gebildet werden. Beim Anlegen wird der sog. "default" Worker Pool erzeugt. 
Danach können weitere Worker Pools erzeugt werden, z.B. zonenspezifisch (d.h. 1 Worker Pool pro Zone). Mit zonenspezifischen Worker Pools kann Workload relativ einfach in andere Zonen verschoben werden (z.B. für geplante Wartungen).
Jeder Worker Pool kann über bis zu drei Zonen aufgespannt werden und besteht aus einer homogenen Knotengrösse (z.B. 4vCPU/16GB RAM). Die Anzahl der Knoten kann im Nachgang erweitert werden (auch automatisch über den sog. Cluster-Autoscaler).
Wenn ein Worker Pool mehrere Zonen umfasst, dann ist die Knotenanzahl nur symmetrisch erweiterbar, d.h. in jeder Zone sind immer gleich viele Knoten in Bezug auf den Worker Pool.

Anbei mal ein Beispiel:
- default Workerpool über 3 Zonen mit 2 Knoten: 2 Knoten AZ1, 2 Knoten AZ2, 2 Knoten AZ3
- AZ1 Workerpool in AZ1 mit 1 Knoten: 1 Knoten AZ1
- AZ2 Workerpool in AZ2 mit 4 Knoten: 4 Knoten AZ2
- AZ3 Workerpool in AZ3 mit 2 Knoten: 2 Knoten AZ2
Jeder Workerpool kann dabei eine andere Knotengröße haben (verschiedene CPU/RAM Konfigurationen).
Wenn nun eine Wartung in AZ1 geplant ist kann der AZ1 Workerpool komplett heruntergefahren werden, die Workload wird dann auf die anderen Worker verteilt. In diesem Fall wären aber durch den default Workerpool immer noch Knoten in AZ1, die man nicht ohne Weiteres entfernen kann, da ein Workerpool quasi nur als Ganzes fungiert.

Weitere Hochverfügbarkeitsaspekte bzgl. Storage und Netzwerk (insbesondere auch Loadbalancing/Routing) schauen wir uns im Detail in den entsprechenden dedidzierten Blogeinträgen dazu an.


