# OPUS4 mit Docker Compose

Es wird ein Cluster aus 3 Docker Containern verwendet:

* Docker Container `opus4-webapp` (enthält PHP und Apache 2 zur Ausführung der OPUS4-Applikation)
* Docker Container `opus4-db`(enthält MySQL DBMS)
* Docker Container `opus4-solr` (enthält Solr Server und JDK)

Die drei Docker-Container sind in ein eigenes Netzwerk `opus4_net` eingesperrt.
