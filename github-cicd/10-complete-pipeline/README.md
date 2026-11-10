# 10 – Vollständige Pipeline und Plattformvergleich (GitHub Actions)

## Ziel und Voraussetzung

Vergleichen Sie äquivalente Abläufe auf GitHub und GitLab. Ausgangspunkt ist ein eigenes Übungsrepository mit dem Inhalt von [examples/maven-app](../../examples/maven-app/README.md) direkt im Stamm. Führen Sie zuerst den lokalen Wrapper-Build aus.

## Durchführung

1. Öffnen Sie die vollständige Datei [pipeline.yml](pipeline.yml). Kopieren Sie sie nach `.github/workflows/ci.yml` in Ihrem Übungsrepository. Die Vorlagen liegen hier absichtlich außerhalb aktiver Workflowpfade.
2. Ersetzen Sie für diesen Schritt die vorherige Übungsvorlage. Sammeln Sie nicht zehn aktive Workflows; sonst lösen Sie unnötige doppelte Läufe aus.
3. Nutzen Sie denselben grünen Anwendungsstand. Aktivieren Sie die vollständige Vorlage auf beiden Plattformen und vergleichen Sie verify, Berichte, Cache, Artefakt und package.
4. Führen Sie auf einem Arbeitsbranch einen absichtlichen Testfehler aus und reparieren Sie ihn. Zeigen Sie auf beiden Plattformen den fehlgeschlagenen Lauf und das blockierte Folgejob-Verhalten.
5. Stellen Sie einen grünen Stand wieder her und notieren Sie Ihre Erkenntnis.

## Erwarteter Nachweis

Vergleichstabelle und Pipeline-Links; Quelle, JAR und Prüfsumme sind zuordenbar.

## Einordnung und Grenzen

Der Jobname package bezeichnet hier die Freigabe/Prüfung des bereits im verify-Job erzeugten JARs. Er führt keinen zweiten Build und kein Produktionsdeployment aus.

Vergleichen Sie mit [gitlab-cicd, Schritt 10](../../gitlab-cicd/10-complete-pipeline/README.md). Besprechen Sie den zugeordneten Fall aus [Lesson 04](../../lessons/lesson-04/README.md). Der Richtwert beträgt 10–15 Minuten; die gesamte Sammlung ist ein Lernpfad und wird nicht vollständig im 135-Minuten-Block abgearbeitet.

[Offizielle Syntaxreferenz](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax)
