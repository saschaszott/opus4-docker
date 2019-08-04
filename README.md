# OPUS4 mit Docker Compose

## Vorbereitung

Neues Verzeichnis auf dem Docker Host anlegen, z.B. mittels `mkdir opusdev`. In diesem Verzeichnis werden dann zwei Git-Repositories ausgecheckt:

```
cd opusdev
git clone https://github.com/OPUS4/application.git
git clone https://github.com/OPUS4/opus4-search.git
```

Will man nicht auf dem `master`-Branch arbeiten (insbesondere bei der OPUS4-Applikation wird man vermutlich auf einem Release- oder Feature-Branch wechseln wollen, um ein Feature zu testen oder neu zu entwickeln), so kann man mit `git checkout $BRANCHNAME` den Branch wechseln.

Beispiel:
```
cd application
# aktuellen Branch anzeigen
git branch

# Branch wechseln, z.B. in 4.6.4-Release-Branch
git checkout 4.6.4

# Branch wechseln, z.B. in OPUSVIER-9876 Feature-Branch
git checkout OPUSVIER-9876
```

## Allgemeine Hinweise zum Aufbau des Docker Compose-Files

Es wird ein Cluster aus 3 Docker Containern verwendet:

* Docker Container `opus4-webapp` (enthält PHP und Apache 2 zur Ausführung der OPUS4-Applikation)
* Docker Container `opus4-db`(enthält MySQL DBMS)
* Docker Container `opus4-solr` (enthält Solr Server und JDK)

Die drei Docker-Container sind in ein eigenes Netzwerk `opus4_net` eingesperrt.

## Bauen und Starten der Container

```
# im Verzeichnis opusdev
git clone https://github.com/saschaszott/opus4-docker.git
ln -s opus4-docker/docker-compose.yml
```
Nun können die 3 Container mittels `docker-compose up -d --no-recreate` gebaut und gestartet werden. Das Flag `-d` führt die Container im Hintergrund aus. Die Option `--no-recreate` baut die Docker Container nicht neu, wenn sie bereits existieren (Identifikation anhand der Containernamen).

## Zugriff auf die Dienste

Durch die definierten *Port Bindings* sind folgende Zugriff vom Docker Host aus möglich:

* Über https://localhost/opus4 kann man auf die OPUS4-Webapp zugreifen (Standard-Port 80).

* Der MySQL-Server kann unter `localhost:3306` erreicht werden, z.B. mit der MySQL Workbench.

* Die Solr-Admin-UI kann unter http://localhost:8983/solr/ aufgerufen werden.

## Referenzen

Docker Compose Dokumentation: https://docs.docker.com/compose/reference/overview/
