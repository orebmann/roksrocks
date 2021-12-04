# Network

Zugriff auf API über Public oder Private Service Endpoint.

Zugriff auf Applikationen erfolgt über Ingress und/oder Loadbalancer. Auch der Ingress haengt am Ende des Tages hinter einem Loadbalancer.
Ein Loadbalancer kann entweder public oder private aufgesetzt werden (in einem Cluster kann es auch public und private Loadbalancer für unterschiedliche Applikationen geben).

Bei Loadbalancern gibt es NLB und ALB (ALB wird per default angelegt).

