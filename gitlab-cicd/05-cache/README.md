# 05 – Cache gegenüber Artefakt (GitLab CI/CD)

## Ziel und Voraussetzung

Unterscheiden Sie Beschleunigung und überprüfbares Ergebnis. Ausgangspunkt ist ein eigenes Übungsrepository mit dem Inhalt von [examples/maven-app](../../examples/maven-app/README.md) direkt im Stamm. Führen Sie zuerst den lokalen Wrapper-Build aus. Prüfen Sie vorab [Runner und Executor](../../docs/runner-und-fehlerdiagnose.md). Die Vorlagen nehmen einen Linux-Container-Executor an. Ergänzen Sie vorhandene Tags nur nach Sichtung der Projekteinstellungen.

## Durchführung

1. Öffnen Sie die vollständige Datei [pipeline.yml](pipeline.yml). Kopieren Sie sie nach `.gitlab-ci.yml` in Ihrem Übungsrepository. Die Vorlagen liegen hier absichtlich außerhalb aktiver Workflowpfade.
2. Ersetzen Sie für diesen Schritt die vorherige Übungsvorlage. Sammeln Sie nicht zehn aktive Workflows; sonst lösen Sie unnötige doppelte Läufe aus.
3. Vergleichen Sie zwei Läufe bei unveränderter POM. Notieren Sie Cache-Meldung und Dauer. Ändern Sie danach kontrolliert den Cache-Schlüssel bzw. entfernen Sie den Cache des Übungsprojekts.
4. Auch ohne Treffer muss der Build korrekt bleiben. Prüfen Sie, dass Maven in GitLab tatsächlich nach $CI_PROJECT_DIR/.m2/repository schreibt.
5. Stellen Sie einen grünen Stand wieder her und notieren Sie Ihre Erkenntnis.

## Erwarteter Nachweis

Zwei gemessene Laufzeiten mit Bedingungen; keine erfundene Beschleunigung.

## Einordnung und Grenzen

Cache-Treffer hängen unter anderem von Branch, Schlüssel, Runner und Plattformregeln ab. target ist kein Ersatz für einen expliziten Artefakttransfer.

Vergleichen Sie mit [github-cicd, Schritt 05](../../github-cicd/05-cache/README.md). Besprechen Sie den zugeordneten Fall aus [Lesson 04](../../lessons/lesson-04/README.md). Der Richtwert beträgt 10–15 Minuten; die gesamte Sammlung ist ein Lernpfad und wird nicht vollständig im 135-Minuten-Block abgearbeitet.

[Offizielle Syntaxreferenz](https://docs.gitlab.com/ci/yaml/)
