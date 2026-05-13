# karaf-sodeac-feature

### was durch com.icg-software.bsx.jms.connetionfactory.bsx wegfällt

- com.icg-software/com.icg-software.bsx.jms.connetionfactory.bsx/2.0.0-SNAPSHOT
- jms.connetionfactory.bsx in bsx-core = CF-Bundle: https://git.extern1.icg-software.de/bs/bsx-core.git

| Feature                                   | Grund                                                                                       |
|-------------------------------------------|---------------------------------------------------------------------------------------------|
| `pax-jms-config`                          | Liest cfg-Dateien → CF erstellen. CF-Bundle macht das direkt via Blueprint                  |
| `pax-jms-pool`                            | Connection Pooling. CF-Bundle nutzt `JmsPoolXAConnectionFactory` selbst                     |
| `pax-jms-artemis`                         | Artemis-spezifischer pax-jms Provider. CF-Bundle nutzt `ActiveMQXAConnectionFactory` direkt |
| `org.ops4j.connectionfactory-artemis.cfg` | War die Config für pax-jms-config                                                           |

Was bleibt:

- jms — JMS API selbst
- artemis-core-client + artemis-jms-client — die Artemis-Client-Bibliotheken die jms.connetionfactory.bsx intern verwendet