# Gemeinsame Maven-Anwendung

Kopieren Sie den **Inhalt dieses Ordners** in das Wurzelverzeichnis Ihres eigenen Übungsrepositories. Damit liegen `pom.xml`, `mvnw`, `.mvn` und `src` direkt im Repository-Stamm. Alle Pipelinevorlagen beziehen sich auf diese Struktur. Versteckte Wrapper-Dateien und die `.gitignore` müssen mitkopiert werden.

Die Anwendung ist der aktuelle Java-Pfad aus Test Automation: Greeting, Calculator, OrderService, Mock- und Integrationstests. JDK 17 ist der Ausgangspunkt. Prüfen Sie lokal `mvn clean verify` mit Maven 3.10.0. Erwartet werden 11 Unit-/parameterisierte Ausführungen und 1 Integrationstest. Start: `java -jar target/contdel-app-1.0-SNAPSHOT.jar`.

`verify` erreicht die Unit- und Integrationstestphase und erzeugt das JAR. `test` allein erreicht die Failsafe-Integrationstests nicht. Ein zusätzliches `test` nach `verify` würde Tests wiederholen. Die Pipeline übergibt das bereits geprüfte JAR an den Folgejob; sie baut es dort nicht neu.

Ein `target`-Ordner ist lokales Build-Ergebnis. Übertragen Sie für einen separaten Job gezielt JAR und zugehörige Prüfsumme als CI-Artefakt, nicht über einen Cache. Keine öffentlichen Paketveröffentlichungen oder Deployments sind Teil dieses Beispiels.

Dieser bisherige Einstieg bleibt als eigenständig kopierbare Variante erhalten. Die gemeinsame Quelle und der Lernpfad liegen unter `examples/maven-app` sowie `gitlab-cicd/10-complete-pipeline`; die hier enthaltene `.gitlab-ci.yml` entspricht Schritt 10.
