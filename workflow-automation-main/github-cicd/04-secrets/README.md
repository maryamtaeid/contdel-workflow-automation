# 04 – Variablen und Secrets (GitHub Actions)

## Ziel und Voraussetzung

Trennen Sie gewöhnliche Konfiguration und einen geheimen Wert. Ausgangspunkt ist ein eigenes Übungsrepository mit dem Inhalt von [examples/maven-app](../../examples/maven-app/README.md) direkt im Stamm. Führen Sie zuerst den lokalen Wrapper-Build aus. Bei Schritt 04 legen Sie LAB_TOKEN als Secret an und wählen „Run workflow“.

## Durchführung

1. Öffnen Sie die vollständige Datei [pipeline.yml](pipeline.yml). Kopieren Sie sie nach `.github/workflows/ci.yml` in Ihrem Übungsrepository. Die Vorlagen liegen hier absichtlich außerhalb aktiver Workflowpfade.
2. Ersetzen Sie für diesen Schritt die vorherige Übungsvorlage. Sammeln Sie nicht zehn aktive Workflows; sonst lösen Sie unnötige doppelte Läufe aus.
3. Hinterlegen Sie ausschließlich einen erfundenen Übungswert als LAB_TOKEN in den CI-Einstellungen. Starten Sie den manuellen Workflow. Die Vorlage prüft nur die Anwesenheit und gibt niemals den Wert aus.
4. Entfernen Sie den Übungswert und starten Sie erneut. Der Job muss mit der Meldung LAB_TOKEN is missing fehlschlagen.
5. Stellen Sie einen grünen Stand wieder her und notieren Sie Ihre Erkenntnis.

## Erwarteter Nachweis

Log ohne Geheimnis sowie Erklärung der Zugriffsgrenze.

## Einordnung und Grenzen

Maskierung ist keine Garantie gegen Offenlegung. Fork-PRs erhalten gewöhnlich keine Repository-Secrets. Geschützte GitLab-Variablen sind nur für entsprechend geschützte Kontexte verfügbar; verwenden Sie keine echten Zugangsdaten.

Vergleichen Sie mit [gitlab-cicd, Schritt 04](../../gitlab-cicd/04-secrets/README.md). Besprechen Sie den zugeordneten Fall aus [Lesson 04](../../lessons/lesson-04/README.md). Der Richtwert beträgt 10–15 Minuten; die gesamte Sammlung ist ein Lernpfad und wird nicht vollständig im 135-Minuten-Block abgearbeitet.

[Offizielle Syntaxreferenz](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax)
