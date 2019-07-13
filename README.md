# OPUS4 mit Docker Compose

Es wird ein Cluster aus 3 Containern verwendet:

* webapp (enthält PHP und Apache 2 zur Ausführung der OPUS4-Applikation)
* db (enthält MySQL DBMS)
* solr (enthält Solr Server und JDK)

Die 3 Container sind in ein eigenes Netzwerk `opus4_net` eingesperrt. 
