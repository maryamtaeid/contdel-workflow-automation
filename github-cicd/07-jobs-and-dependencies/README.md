# 07 – Job-Abhängigkeiten und Artefaktübergabe (GitHub Actions)

## Ziel und Voraussetzung

Übergeben Sie genau das geprüfte Artefakt zwischen isolierten Jobs. Ausgangspunkt ist ein eigenes Übungsrepository mit dem Inhalt von [examples/maven-app](../../examples/maven-app/README.md) direkt im Stamm. Führen Sie zuerst den lokalen Wrapper-Build aus.

## Durchführung

1. Öffnen Sie die vollständige Datei [pipeline.yml](pipeline.yml). Kopieren Sie sie nach `.github/workflows/ci.yml` in Ihrem Übungsrepository. Die Vorlagen liegen hier absichtlich außerhalb aktiver Workflowpfade.
2. Ersetzen Sie für diesen Schritt die vorherige Übungsvorlage. Sammeln Sie nicht zehn aktive Workflows; sonst lösen Sie unnötige doppelte Läufe aus.
3. Lesen Sie verify → package. Der erste Job prüft und baut das JAR, der zweite lädt dasselbe JAR und seine Prüfsumme, kontrolliert den Hash und startet es.
4. Lassen Sie einen Test scheitern: package muss ausbleiben. Entfernen Sie anschließend in einer Übungskopie die Übergabe und erklären Sie den fehlenden Dateizugriff.
5. Stellen Sie einen grünen Stand wieder her und notieren Sie Ihre Erkenntnis.

## Erwarteter Nachweis

Jobgraph, Prüfsumme und erfolgreicher Start ohne erneuten Maven-Build im package-Job.

## Einordnung und Grenzen

GitHub-Jobs laufen ohne needs parallel. GitLab-Stages ordnen Jobs, needs kann den starren Stage-Ablauf gezielt verkürzen. Ein neuer Job besitzt nicht automatisch den vorherigen Workspace.

Vergleichen Sie mit [gitlab-cicd, Schritt 07](../../gitlab-cicd/07-jobs-and-dependencies/README.md). Besprechen Sie den zugeordneten Fall aus [Lesson 04](../../lessons/lesson-04/README.md). Der Richtwert beträgt 10–15 Minuten; die gesamte Sammlung ist ein Lernpfad und wird nicht vollständig im 135-Minuten-Block abgearbeitet.

[Offizielle Syntaxreferenz](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax)
