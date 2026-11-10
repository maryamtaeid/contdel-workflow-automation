# 06 – Trigger und Branch-Regeln (GitLab CI/CD)

## Ziel und Voraussetzung

Wählen Sie Trigger für frühzeitiges Integrationsfeedback. Ausgangspunkt ist ein eigenes Übungsrepository mit dem Inhalt von [examples/maven-app](../../examples/maven-app/README.md) direkt im Stamm. Führen Sie zuerst den lokalen Wrapper-Build aus. Prüfen Sie vorab [Runner und Executor](../../docs/runner-und-fehlerdiagnose.md). Die Vorlagen nehmen einen Linux-Container-Executor an. Ergänzen Sie vorhandene Tags nur nach Sichtung der Projekteinstellungen. Bei Schritt 06 legen Sie den Schedule in der Oberfläche an.

## Durchführung

1. Öffnen Sie die vollständige Datei [pipeline.yml](pipeline.yml). Kopieren Sie sie nach `.gitlab-ci.yml` in Ihrem Übungsrepository. Die Vorlagen liegen hier absichtlich außerhalb aktiver Workflowpfade.
2. Ersetzen Sie für diesen Schritt die vorherige Übungsvorlage. Sammeln Sie nicht zehn aktive Workflows; sonst lösen Sie unnötige doppelte Läufe aus.
3. Erstellen Sie einen Arbeitsbranch und einen Pull/Merge Request. Vergleichen Sie Branch-Push, Review-Ereignis und main. Planen Sie einen ergänzenden Wochenlauf.
4. Prüfen Sie, ob derselbe Commit doppelt läuft. Die GitLab-Regeln unterdrücken den Branch-Push, wenn bereits ein Merge Request offen ist.
5. Stellen Sie einen grünen Stand wieder her und notieren Sie Ihre Erkenntnis.

## Erwarteter Nachweis

Tabelle Ereignis → erwarteter Lauf → beobachteter Lauf.

## Einordnung und Grenzen

GitHub schedule liegt in der YAML; GitLab-Schedules werden im Projekt angelegt. Zeitpläne ersetzen kein Feedback zu Änderungen. Verwechseln Sie Commit und Integration nicht.

Vergleichen Sie mit [github-cicd, Schritt 06](../../github-cicd/06-triggers-and-rules/README.md). Besprechen Sie den zugeordneten Fall aus [Lesson 04](../../lessons/lesson-04/README.md). Der Richtwert beträgt 10–15 Minuten; die gesamte Sammlung ist ein Lernpfad und wird nicht vollständig im 135-Minuten-Block abgearbeitet.

[Offizielle Syntaxreferenz](https://docs.gitlab.com/ci/yaml/)
