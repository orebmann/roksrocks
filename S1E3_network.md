---
title: "Netzwerk - ROKS rocks!"
tags:
  - ROKS
  - Red Hat
  - OpenShift
  - IBM
  - IBM Cloud
  - Architektur
  - Architecture
  - Satellite
  - Cloud Satellite
  - Netzwerk
  - Network
  - Loadbalancer
  - Lastverteilung
  - Availabilty Zone
  - Hochverfügbarkeit
  - IBM Cloud Satellite
---

# Netzwerk

Generell kann ROKS mit privatem oder öffentlichem (public) Zugang, oder einer Mischung aus beidem ausgerollt werden. 
Dabei ist bzgl. Zugang zwischen zwei Ebenen zu unterscheiden:
- API Zugriff (sog. Public oder Private Endpoints/Endpunkte)
- Applikationszugriff (wird über Loadbalancer bereitgestellt)

Prinzipiell bedeutet privater Zugriff, dass ein Zugriff aus dem Internet nicht möglich ist, d.h. um auf das Cluster zugreifen zu können, muss man entweder im 
gleichen Netzwerk sein (z.B. durch Aufsetzen eines Jump-Servers oder Bastion-Nodes) oder über eine private Zugangstechnologie (z.B. VPN oder Direktverbindung/Direct Link) verfügen.

Dies erhöht den Administrationsaufwand und die Sicherheit gleichermassen. Für die allermeisten Cluster (Spielcluster und PoCs ausgenommen) ist es m.E. deshalb sinnvoll
den Zugriff zunächst auf private Endpunkte und private Loadbalancer zu begrenzen und bei Bedarf um public/öffentliche Loadbalancer, für die Applikationsteile, die ins Internet exponiert werden müssen, zu erweitern.

Diese Empfehlungen beziehen sich explizit auf "Zugang", d.h. eingehenden Datenverkehr (oft auch als Inbound Traffic bezeichnet). 
Ausgehende Requests ins Internet (z.B. zum Pullen eines Container-Images, sog. Outbound Traffic) können separat davon betrachtet werden und z.B. in einer Virtual Private Cloud (VPC)-Umgebung separat davon über ein Public Gateway ermöglicht werden.


Zugriff auf Applikationen erfolgt über Ingress und/oder Loadbalancer. Auch der Ingress haengt am Ende des Tages hinter einem Loadbalancer.
Ein Loadbalancer kann entweder public oder private aufgesetzt werden (in einem Cluster kann es auch public und private Loadbalancer für unterschiedliche Applikationen geben).

Bei Loadbalancern gibt es NLB und ALB (ALB wird per default angelegt).

**Zusammenfassung:** Anwendungen sollten, wo möglich die hochverfügbaren PaaS Services aus der Cloud verwenden (z.B. Datenbanken, Logging). Persistenter Speicher für zustandsbehaftete Workload kann in ROKS auf verschiedenste Arten und Weisen zonal oder multi-zonal bereitgestellt werden. Sollte Hochverfügbarkeit benötigt werden sollte ein zonenübergreifender Storage verwendet werden. Für FTP-style (put, get) workload kann hier Cloud Object Storage (S3) verwendet werden, für Workload die häufige Dateiänderungen erfodert sollte ein software-definierter Storage zum Einsatz kommen (z.B. mit ODF)

[Inhaltsverzeichnis](./README.md) 