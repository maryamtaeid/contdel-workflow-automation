# Workflow Automation – GitHub und GitLab im Vergleich

## Ausführbare Java-Demos auf beiden Plattformen

[GitHub Actions – Java CI Demo](https://github.com/michaelulm/contdel-ws26-java-demo) · [GitLab CI/CD – Java CI Demo](https://gitlab.itplus.fh-joanneum.at/study/msd/msd24w/courses/contdel/java-ci-demo-ws26). Beide READMEs haben dieselbe Kapitelstruktur: Anwendung, lokaler Build, Berichte, Pipeline, Rot/Grün, Vergleich und Fehlerdiagnose. Beginnen Sie lokal mit `mvn clean verify`.

| Begriff | GitHub-Demo | GitLab-Demo |
|---|---|---|
| Plattform / Ausführung | GitHub Actions organisiert Workflows; Runner führen Jobs aus | GitLab CI/CD organisiert Pipelines; GitLab Runner führen Jobs aus |
| Konfiguration | .github/workflows/ci.yml; Jobs mit Steps | .gitlab-ci.yml; Jobs mit script und Stages |
| Umgebung | runs-on: ubuntu-24.04; Java über setup-java | Instanzrunner #1, ohne Tags, Kubernetes-Executor und JDK-17-Image |
| Ereignisse | main-Push, PR, manueller Start | Branch-Push, MR, manueller Start; keine doppelte Push-Pipeline bei offenem MR |
| Testberichte | XML-Artefakt und eigene Laufzusammenfassung | reports:junit mit nativer Tests-Ansicht |
| Artefaktübergabe | upload/download-artifact und needs | artifacts und needs mit artifacts: true |

Ein GitLab Runner ist das Gegenstück zum GitHub-Runner, nicht zur gesamten Plattform GitHub Actions. Beide Demos prüfen denselben Java-Code und übergeben das JAR ohne Neubuild. Prüfen Sie Zugriff und Runner in Ihrem eigenen Übungsprojekt.


Die bisherigen Einzelübungen bleiben als Lernpfad erkennbar. Unter **github-cicd** und **gitlab-cicd** finden Sie nun dieselben Nummern und Lernziele. Die aktuellen Beispiele verwenden dieselbe Maven-Anwendung und denselben Buildbefehl.

**Unterrichtsreihenfolge:** Zuerst GitHub Actions [schrittweise aufbauen](docs/github-einstieg.md), anschließend jeweils das GitLab-Pendant zuordnen.

## Vorbereitung

1. Übernehmen Sie den Inhalt von [examples/maven-app](examples/maven-app/README.md) einschließlich `.mvn` in ein eigenes Übungsrepository. Verwenden Sie alternativ Ihren grünen Java-Stand aus Test Automation mit identischen Bericht- und JAR-Pfaden.
2. Bauen Sie lokal mit JDK 17 und `mvn clean verify` (Maven 3.10.0; Wrapper alternativ). Halten Sie Testzahl und JAR fest.
3. Prüfen Sie GitHub-Actions-Zugriff sowie GitLab-Runner und Executor. [Runner-Diagnose](docs/runner-und-fehlerdiagnose.md) erklärt die Voraussetzungen. Für dieses Study-Demo ist Instanzrunner #1 für Jobs ohne Tags verfügbar; generische Vorlagen benötigen eine passende Runner-Zuordnung.
4. Kopieren Sie **eine** Pipelinevorlage an ihren aktiven Zielpfad. Führen Sie die nächsten Schritte als nachvollziehbare Änderungen derselben Pipeline aus.

## Paralleler Lernpfad

| Nr. | Thema | GitHub | GitLab |
|---|---|---|---|
| 01 | First Steps und Runner | [Übung](github-cicd/01-first-steps/README.md) | [Übung](gitlab-cicd/01-first-steps/README.md) |
| 02 | Tests und Artefakte | [Übung](github-cicd/02-testrun-artifacts/README.md) | [Übung](gitlab-cicd/02-testrun-artifacts/README.md) |
| 03 | JUnit-Berichte bei Fehlern | [Übung](github-cicd/03-testreports/README.md) | [Übung](gitlab-cicd/03-testreports/README.md) |
| 04 | Variablen und Secrets | [Übung](github-cicd/04-secrets/README.md) | [Übung](gitlab-cicd/04-secrets/README.md) |
| 05 | Cache gegenüber Artefakt | [Übung](github-cicd/05-cache/README.md) | [Übung](gitlab-cicd/05-cache/README.md) |
| 06 | Trigger und Branch-Regeln | [Übung](github-cicd/06-triggers-and-rules/README.md) | [Übung](gitlab-cicd/06-triggers-and-rules/README.md) |
| 07 | Job-Abhängigkeiten und Artefaktübergabe | [Übung](github-cicd/07-jobs-and-dependencies/README.md) | [Übung](gitlab-cicd/07-jobs-and-dependencies/README.md) |
| 08 | Matrix und gezielte Parallelisierung | [Übung](github-cicd/08-matrix/README.md) | [Übung](gitlab-cicd/08-matrix/README.md) |
| 09 | Wiederverwendung | [Übung](github-cicd/09-reuse/README.md) | [Übung](gitlab-cicd/09-reuse/README.md) |
| 10 | Vollständige Pipeline und Plattformvergleich | [Übung](github-cicd/10-complete-pipeline/README.md) | [Übung](gitlab-cicd/10-complete-pipeline/README.md) |

Die Lücke 06–09 behandelt damit die Steuerung der Pipeline, bevor 10 die Teile zusammenführt. Die früheren GitLab-First-Steps liegen unter `gitlab-cicd/01-first-steps`. Alte Einstiegspfade verweisen auf die neuen Anleitungen.

## Unterricht am 10.11.2026, 11:30–13:45

Beginnen Sie mit [Lesson 04](lessons/lesson-04/README.md). Pflichtkern sind 01–03, 06/07 und der Vergleich in 10. 04/05 werden demonstriert, 08/09 sind vorbereitete Vertiefungen. Diese Auswahl vermeidet zehn Pflichtübungen pro Plattform in einer einzigen Einheit.

GitHub hat Workflows mit Jobs und Steps; es gibt dort kein eigenes Stage-Schlüsselwort wie in GitLab. GitLab ordnet Jobs Stages zu und kann mit `needs` explizite Abhängigkeiten ausdrücken. Runner-Scope, Executor und Image sind unterschiedliche Entscheidungen. Die [Vergleichstabelle](docs/plattformvergleich.md) hält diese Begriffe auseinander.

## Beispiele und Archiv

`examples/maven-app` ist der aktuelle gemeinsame Stand. `examples/ws25` bewahrt historische Varianten und ist kein WS26-Einstieg. Die kleinen Ausgangsbeispiele bleiben bewusst ohne zusätzliche Containerabstraktion auf dem lokalen Rechner: Der folgende Containerblock behandelt diese Grenze.

CI-Ausgaben werden als zeitlich begrenzte Artefakte gespeichert. `target`, `.m2`, Logs und Berichte gehören nicht in Git. Action-Majors und Image-Patchstände sind der Prüfstand; produktive Projekte sollten zusätzlich unveränderliche Action-SHAs bzw. Image-Digests und eine Update-Regel verwenden.

[GitHub Actions](https://docs.github.com/en/actions) · [GitLab CI/CD](https://docs.gitlab.com/ci/) · [Maven Lifecycle](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)

**Runner-Stand 07.11.2026:** Im Course-Javademo läuft Gruppenrunner #3 mit Tag `edu` und Docker-Executor. Im Study-Bereich läuft Instanzrunner #1 (Default Runner), Kubernetes, Linux/amd64, für Jobs **ohne Tags**. Übernehmen Sie `tags: [edu]` deshalb nicht in Study. Prüfen Sie im eigenen Projekt unter Settings → CI/CD → Runners den tatsächlich verfügbaren Runner. Scope, Executor und Job-Image sind getrennte Eigenschaften.
