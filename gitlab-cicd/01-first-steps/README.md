# 01 – First Steps und Runner (GitLab CI/CD)

## Ziel und Voraussetzung

Erklären Sie, wo der Job läuft und welche Dateien er benötigt. Ausgangspunkt ist ein eigenes Übungsrepository mit dem Inhalt von [examples/maven-app](../../examples/maven-app/README.md) direkt im Stamm. Führen Sie zuerst den lokalen Wrapper-Build aus. Prüfen Sie vorab [Runner und Executor](../../docs/runner-und-fehlerdiagnose.md). Die Vorlagen nehmen einen Linux-Container-Executor an. Ergänzen Sie vorhandene Tags nur nach Sichtung der Projekteinstellungen.

## Durchführung

1. Öffnen Sie die vollständige Datei [pipeline.yml](pipeline.yml). Kopieren Sie sie nach `.gitlab-ci.yml` in Ihrem Übungsrepository. Die Vorlagen liegen hier absichtlich außerhalb aktiver Workflowpfade.
2. Ersetzen Sie für diesen Schritt die vorherige Übungsvorlage. Sammeln Sie nicht zehn aktive Workflows; sonst lösen Sie unnötige doppelte Läufe aus.
3. Kopieren Sie die gemeinsame Anwendung und die Vorlage. Lösen Sie einen Lauf aus; finden Sie Runner, Checkout-Revision, Java-Version, Testzahl und Exitcode im Log.
4. Entfernen Sie in einer Übungskopie einen Import aus App.java. Prüfen Sie, dass die Kompilierung den Job rot beendet, und reparieren Sie die Änderung.
5. Stellen Sie einen grünen Stand wieder her und notieren Sie Ihre Erkenntnis.

## Erwarteter Nachweis

Pipeline-Link, Commit und Runner-Umgebung; ein erfolgreicher Lauf mit mindestens einem Test.

## Einordnung und Grenzen

Ein Runner-Scope beschreibt die Zuordnung; der Executor beschreibt die technische Ausführung. Ein Image ersetzt nicht die Runner-Auswahl.

Vergleichen Sie mit [github-cicd, Schritt 01](../../github-cicd/01-first-steps/README.md). Besprechen Sie den zugeordneten Fall aus [Lesson 04](../../lessons/lesson-04/README.md). Der Richtwert beträgt 10–15 Minuten; die gesamte Sammlung ist ein Lernpfad und wird nicht vollständig im 135-Minuten-Block abgearbeitet.

[Offizielle Syntaxreferenz](https://docs.gitlab.com/ci/yaml/)
