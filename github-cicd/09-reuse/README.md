# 09 – Wiederverwendung (GitHub Actions)

## Ziel und Voraussetzung

Vermeiden Sie auseinanderlaufende Kopien gemeinsamer Prüfungen. Ausgangspunkt ist ein eigenes Übungsrepository mit dem Inhalt von [examples/maven-app](../../examples/maven-app/README.md) direkt im Stamm. Führen Sie zuerst den lokalen Wrapper-Build aus.

## Durchführung

1. Öffnen Sie die vollständige Datei [pipeline.yml](pipeline.yml). Kopieren Sie sie nach `.github/workflows/ci.yml` in Ihrem Übungsrepository. Die Vorlagen liegen hier absichtlich außerhalb aktiver Workflowpfade.
2. Ersetzen Sie für diesen Schritt die vorherige Übungsvorlage. Sammeln Sie nicht zehn aktive Workflows; sonst lösen Sie unnötige doppelte Läufe aus.
3. Kopieren Sie zusätzlich die zweite Vorlagendatei an den unten genannten Zielpfad. Lesen Sie Aufruf und Implementierung gemeinsam. Ändern Sie einen verständlichen Jobnamen und beobachten Sie den Folge-Lauf.
4. Entfernen Sie die referenzierte Datei in einer Übungskopie. Prüfen Sie die Konfigurationsfehlermeldung, bevor Sie nach einem Laufzeitproblem suchen.
5. Stellen Sie einen grünen Stand wieder her und notieren Sie Ihre Erkenntnis.

Zusätzlich: `verify-reusable.yml` nach `.github/workflows/verify-reusable.yml` kopieren.

## Erwarteter Nachweis

Aufrufer und wiederverwendbarer Teil mit erklärter Schnittstelle.

## Einordnung und Grenzen

GitHub workflow_call ist ein aufrufbarer Workflow; GitLab include/extends führt Konfiguration zusammen. Das sind ähnliche Ziele mit unterschiedlichen Mechanismen.

Vergleichen Sie mit [gitlab-cicd, Schritt 09](../../gitlab-cicd/09-reuse/README.md). Besprechen Sie den zugeordneten Fall aus [Lesson 04](../../lessons/lesson-04/README.md). Der Richtwert beträgt 10–15 Minuten; die gesamte Sammlung ist ein Lernpfad und wird nicht vollständig im 135-Minuten-Block abgearbeitet.

[Offizielle Syntaxreferenz](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax)
