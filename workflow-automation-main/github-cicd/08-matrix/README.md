# 08 – Matrix und gezielte Parallelisierung (GitHub Actions)

## Ziel und Voraussetzung

Prüfen Sie denselben Quellstand mit zwei Laufzeiten. Ausgangspunkt ist ein eigenes Übungsrepository mit dem Inhalt von [examples/maven-app](../../examples/maven-app/README.md) direkt im Stamm. Führen Sie zuerst den lokalen Wrapper-Build aus.

## Durchführung

1. Öffnen Sie die vollständige Datei [pipeline.yml](pipeline.yml). Kopieren Sie sie nach `.github/workflows/ci.yml` in Ihrem Übungsrepository. Die Vorlagen liegen hier absichtlich außerhalb aktiver Workflowpfade.
2. Ersetzen Sie für diesen Schritt die vorherige Übungsvorlage. Sammeln Sie nicht zehn aktive Workflows; sonst lösen Sie unnötige doppelte Läufe aus.
3. Verwenden Sie Java 17 und 21. Das Kompilierungsziel bleibt 17. Lesen Sie je Matrixzweig die Laufzeit und Testzahl.
4. Vergleichen Sie die getrennten Reports. Bei GitHub verhindern eindeutige Artefaktnamen Namenskollisionen; fail-fast: false lässt beide Ergebnisse sichtbar werden.
5. Stellen Sie einen grünen Stand wieder her und notieren Sie Ihre Erkenntnis.

## Erwarteter Nachweis

Zwei Testergebnisse für denselben Commit, mit klarer Runtime-Zuordnung.

## Einordnung und Grenzen

Eine Matrix multipliziert Rechenzeit und Wartungsaufwand. Zwei JDKs beweisen keine Unterstützung aller Betriebssysteme und Architekturen.

Vergleichen Sie mit [gitlab-cicd, Schritt 08](../../gitlab-cicd/08-matrix/README.md). Besprechen Sie den zugeordneten Fall aus [Lesson 04](../../lessons/lesson-04/README.md). Der Richtwert beträgt 10–15 Minuten; die gesamte Sammlung ist ein Lernpfad und wird nicht vollständig im 135-Minuten-Block abgearbeitet.

[Offizielle Syntaxreferenz](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax)
