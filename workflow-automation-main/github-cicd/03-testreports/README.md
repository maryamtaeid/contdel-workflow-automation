# 03 – JUnit-Berichte bei Fehlern (GitHub Actions)

## Ziel und Voraussetzung

Lesen Sie Fehlerberichte auch bei einem fehlgeschlagenen Test. Ausgangspunkt ist ein eigenes Übungsrepository mit dem Inhalt von [examples/maven-app](../../examples/maven-app/README.md) direkt im Stamm. Führen Sie zuerst den lokalen Wrapper-Build aus.

## Durchführung

1. Öffnen Sie die vollständige Datei [pipeline.yml](pipeline.yml). Kopieren Sie sie nach `.github/workflows/ci.yml` in Ihrem Übungsrepository. Die Vorlagen liegen hier absichtlich außerhalb aktiver Workflowpfade.
2. Ersetzen Sie für diesen Schritt die vorherige Übungsvorlage. Sammeln Sie nicht zehn aktive Workflows; sonst lösen Sie unnötige doppelte Läufe aus.
3. Ändern Sie die Greeting-Erwartung im Test. Lassen Sie die Pipeline rot werden und öffnen Sie den Surefire-Bericht. Der Report-Upload darf den Fehlerstatus nicht neutralisieren.
4. Prüfen Sie, ob Failsafe überhaupt erreicht wurde. Fehlende spätere Berichte sind kein grüner Integrationsnachweis.
5. Stellen Sie einen grünen Stand wieder her und notieren Sie Ihre Erkenntnis.

## Erwarteter Nachweis

Fehlgeschlagener Testname, erwarteter/erhaltener Wert und reparierter Lauf.

## Einordnung und Grenzen

GitLab interpretiert reports:junit in der Oberfläche; GitHub stellt hier ein XML-Artefakt bereit. Das ist kein identischer Report-Publisher.

Vergleichen Sie mit [gitlab-cicd, Schritt 03](../../gitlab-cicd/03-testreports/README.md). Besprechen Sie den zugeordneten Fall aus [Lesson 04](../../lessons/lesson-04/README.md). Der Richtwert beträgt 10–15 Minuten; die gesamte Sammlung ist ein Lernpfad und wird nicht vollständig im 135-Minuten-Block abgearbeitet.

[Offizielle Syntaxreferenz](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax)

[Bausteine, Ereignis-Timeline und GitLab-Vergleich](../../docs/github-einstieg.md) begleiten den gemeinsamen Unterricht.
