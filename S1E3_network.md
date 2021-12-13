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

Zugriff auf API über Public oder Private Service Endpoint.

Zugriff auf Applikationen erfolgt über Ingress und/oder Loadbalancer. Auch der Ingress haengt am Ende des Tages hinter einem Loadbalancer.
Ein Loadbalancer kann entweder public oder private aufgesetzt werden (in einem Cluster kann es auch public und private Loadbalancer für unterschiedliche Applikationen geben).

Bei Loadbalancern gibt es NLB und ALB (ALB wird per default angelegt).

**Zusammenfassung:** Anwendungen sollten, wo möglich die hochverfügbaren PaaS Services aus der Cloud verwenden (z.B. Datenbanken, Logging). Persistenter Speicher für zustandsbehaftete Workload kann in ROKS auf verschiedenste Arten und Weisen zonal oder multi-zonal bereitgestellt werden. Sollte Hochverfügbarkeit benötigt werden sollte ein zonenübergreifender Storage verwendet werden. Für FTP-style (put, get) workload kann hier Cloud Object Storage (S3) verwendet werden, für Workload die häufige Dateiänderungen erfodert sollte ein software-definierter Storage zum Einsatz kommen (z.B. mit ODF)

[Inhaltsverzeichnis](./README.md) 