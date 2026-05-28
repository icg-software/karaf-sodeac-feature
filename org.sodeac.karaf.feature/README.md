# karaf-sodeac-feature

## Installation in Karaf 4.4.10

```bash
# open karaf console
karaf
```

```bash
feature:repo-add mvn:org.sodeac/org.sodeac.karaf.feature/2.0.0-SNAPSHOT/xml/features

#installs all at once
feature:install sodeac-standalone
```

### all other features

```bash

# 1) bsx-mail-service (outlook)
feature:repo-add mvn:com.icg-software.bsx/graph.sdk.feature/2.0.0-SNAPSHOT/xml/features

#installs all at once
feature:install bsx-mailservice


# 2) all bs-db (should be after bsx-mail-service, otherwise there might be failure in com.icg-software.bsx.datasource.icgbs.localhost!)
# connect datasource: localhost or stage (only one is allowed to be active!)
bundle:install -s mvn:com.icg-software.bsx/com.icg-software.bsx.datasource.icgbs.localhost/2.0.0-SNAPSHOT
#bundle:install -s mvn:com.icg-software.bsx/com.icg-software.bsx.datasource.icgbs.sspbs.stage/2.0.0-SNAPSHOT

# includes bs-db
feature:repo-add mvn:com.icg-software/com.icg-software.integration.easy.feature/2.0.0-SNAPSHOT/xml/features
feature:install bsx-easy-db

```

### Ersatz für pax-jms durch com.icg-software.bsx.jms.connetionfactory.bsx

Das CF-Bundle (`com.icg-software.bsx.jms.connetionfactory.bsx`, [bsx-core](https://git.extern1.icg-software.de/bs/bsx-core.git)) übernimmt die JMS Connection Factory direkt via Blueprint und ersetzt damit die pax-jms-Features (`pax-jms-config`, `pax-jms-pool`, `pax-jms-artemis`), deren Konfigurationsdateien sowie die Artemis-XML-Deployments.

Übrig bleiben nur noch die JMS-API und die Artemis-Client-Bibliotheken.
