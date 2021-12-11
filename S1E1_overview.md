---
title: "Überblick - ROKS rocks!"
tags:
  - ROKS
  - Red Hat
  - OpenShift
  - ARO
  - ROSA
  - AWS
  - Azure
  - Microsoft
  - IBM
  - IBM Cloud
  - Architektur
  - Architecture
  - Satellite
  - Cloud Satellite
  - IBM Cloud Satellite
---

# Überblick

Über die Vorteile von OpenShift gegenüber anderen Kuebernetes-Distributionen wurden schon diverse Blogs geschrieben und Diskussionen geführt (z.B. [Red Hat OpenShift und Kubernetes im Vergleich](https://www.redhat.com/de/topics/containers/red-hat-openshift-kubernetes)). Deshalb hier wirklich nur ein kurzer Abriss über die Vorteile von OpenShift aus meiner Sicht.
- OpenShift ist Kubernetes (genaugenommen eine Distribution von Kubernetes)
- OpenShift ist Open-Source (IBM und Red Hat sind neben Google Hauptcontributors im Kubernetes Kontext)
- OpenShift ist mehr als Kubernetes. OpenShift ist eine Anwendungsplattform (d.h. wichtige Werkzeuge für Entwickler und den Betrieb/Administratoren sind vor-integriert und weitere Werkzeuge einfach integrierbar, es wird auf Sicherheits- und Unternehmensbelange besonderer Wert gelegt, Updates und Migrationspfade werden getestet und bereitgestellt, etc.)
- OpenShift gibt es mit Support, d.h. man ist bei Problemem nicht auf sich gestellt (für Unternehmen oft sehr wichtig, sog. Subscriptions im Red Hat Jargon)
- OpenShift gibt es überall (im eigenen Rechenzentrum, bei Cloud-Anbietern, etc.) selbst-gemanagedt oder auch voll-gemanagedt (z.B. ROKS auf IBM Cloud Satellite), d.h. Investitionsschutz und Portabilität werden grossgeschrieben

Was genau ist jetzt ROKS?
ROKS ist ein ge-managedter Red Hat OpenShift Service auf der IBM Cloud, d.h.
- ROKS ist OpenShift
- Die Installation erfolgt automatisiert auf Knopfdruck (oder durch Automation, z.B. via CLI oder Terraform)
- Updates erfolgen auf Knopfdruck (oder durch Automation, z.B. via CLI oder Terraform)
- Bei Problemen gibt es Support (Ticket aufmachen oder auch architekturelle Fragen stellen)
- SRE Unterstützung (Site Reliability Engineering, d.h. viele Probleme werden schon adressiert, bevor der Kunde sie feststellt)
- Hochverfügbarkeit, Security/Härtung und Compliance by default (d.h. diese wichtigen Aspekte sind bereits adressiert)
- Integration mit weiteren Plattform-Services (Logging, Monitoring, Verschlüsselung, Secrets Management, Identity and Access Management, Storage, Netzwerk, Container Registry mit Schwachstellenchecks)
- Vereinfachte Installation weiterer IBM Software-Pakete (z.B. IBM Cloud Paks können auf Knopfdruck aus dem IBM Cloud Portal auf ROKS installiert werden)

Mittels IBM Cloud Satellite kann ROKS aber auch anderswo sehr einfach als gemanagedter Service bereitgestellt werden (z.B. im eigenen Rechenzentrum, bei anderen Cloud-Providern oder auch an sog. Edge-Lokationen (z.B. einer Aussenstelle, einer Fabrikhalle, etc.). Als Grundlage werden lediglich Linux Server und eine ausgehende Internet-Verbindung benötigt.

Zusammenfassung: ROKS ist ein ge-managedter OpenShift-Service von IBM. ROKS kann in der IBM Cloud als Service bezogen werden. ROKS kann über den verteilten Cloud-Dienst IBM Cloud Satellite aber auch in anderen Clouds, dem eigenen Rechenzentrum oder sog. Edges bereitgestellt werden (alles was dazu benötigt wird sind Linux Hosts und eine ausgehende Internet-Verbindung).

[Inhaltsverzeichnis](./README.md) 
