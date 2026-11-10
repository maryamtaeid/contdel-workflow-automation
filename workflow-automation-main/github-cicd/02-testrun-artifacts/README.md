# 02 – Tests und Artefakte (GitHub Actions)

## Ziel und Voraussetzung

Unterscheiden Sie ein Build-Ergebnis von einer Quelldatei. Ausgangspunkt ist ein eigenes Übungsrepository mit dem Inhalt von [examples/maven-app](../../examples/maven-app/README.md) direkt im Stamm. Führen Sie zuerst den lokalen Wrapper-Build aus.

## Durchführung

1. Öffnen Sie die vollständige Datei [pipeline.yml](pipeline.yml). Kopieren Sie sie nach `.github/workflows/ci.yml` in Ihrem Übungsrepository. Die Vorlagen liegen hier absichtlich außerhalb aktiver Workflowpfade.
2. Ersetzen Sie für diesen Schritt die vorherige Übungsvorlage. Sammeln Sie nicht zehn aktive Workflows; sonst lösen Sie unnötige doppelte Läufe aus.
3. Bauen Sie die Anwendung, laden Sie das JAR aus dem Lauf herunter und starten Sie es außerhalb des Checkouts mit Java 17.
4. Ändern Sie den Artefaktpfad absichtlich auf einen nicht vorhandenen Pfad. Lesen Sie Warnung bzw. Fehler und vergleichen Sie dies mit einem wirklichen Testfehler.
5. Stellen Sie einen grünen Stand wieder her und notieren Sie Ihre Erkenntnis.

## Erwarteter Nachweis

JAR-Name, Herkunfts-Commit und Ausgabe des getrennten Starts.

## Einordnung und Grenzen

Ein erfolgreicher Upload beweist keine fachliche Richtigkeit. Fehlende GitLab-Artefakte können nur eine Warnung erzeugen; erforderliche Dateien müssen zusätzlich im Skript geprüft werden.

Vergleichen Sie mit [gitlab-cicd, Schritt 02](../../gitlab-cicd/02-testrun-artifacts/README.md). Besprechen Sie den zugeordneten Fall aus [Lesson 04](../../lessons/lesson-04/README.md). Der Richtwert beträgt 10–15 Minuten; die gesamte Sammlung ist ein Lernpfad und wird nicht vollständig im 135-Minuten-Block abgearbeitet.

[Offizielle Syntaxreferenz](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax)
