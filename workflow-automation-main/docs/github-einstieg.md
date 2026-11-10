# GitHub Actions schrittweise verstehen

Verwenden Sie die gleiche Maven-Anwendung wie im Testblock. GitHub ist der gemeinsame Einstieg; zu jedem Baustein vergleichen Sie das GitLab-Pendant. Die vollständigen kopierbaren Vorlagen bleiben unter [01](../github-cicd/01-first-steps/pipeline.yml) und [03](../github-cicd/03-testreports/pipeline.yml). Die Ausschnitte unten erklären deren Aufbau; sie sind für sich noch keine vollständigen Workflows.

## 1. Datei und Auslöser

Kopieren Sie `examples/maven-app` einschließlich `.mvn` in den Stamm Ihres eigenen GitHub-Übungsrepositories. Legen Sie `.github/workflows/ci.yml` an.

```yaml
name: Maven exercise
on:
  push:
    branches: [main]
  pull_request:
  workflow_dispatch:
permissions:
  contents: read
```

Ein lokaler Commit startet noch keinen GitHub-Lauf. In dieser Konfiguration startet ein Push nach `main` einen Lauf. Das Öffnen eines Pull Requests sowie dessen Aktualisierung starten ebenfalls Prüfungen. Ein Feature-Branch-Push ohne offenen Pull Request startet hier keinen Lauf. `workflow_dispatch` erlaubt den bewussten manuellen Start, wenn die Workflowdatei auf dem Default-Branch vorliegt. Der manuelle Start ist kein automatisches Deployment.

GitLab: `.gitlab-ci.yml` im Stamm; `workflow: rules` steuert die Pipeline-Erzeugung, Job-`rules` die Teilnahme einzelner Jobs. GitLab 01 lässt zusätzliche Branch-Pushes zu und unterdrückt doppelte Branch-Pipelines bei offenem Merge Request. Gleiche Nummern stehen für gleiche Lernziele, nicht für exakt identisches Triggerverhalten.

## 2. Job und Ausführungsumgebung

```yaml
jobs:
  verify:
    runs-on: ubuntu-24.04
    timeout-minutes: 15
    steps:
```

`verify` ist der Jobname. `runs-on` wählt hier einen GitHub-gehosteten Linux-Runner. Steps laufen innerhalb dieses Jobs standardmäßig nacheinander und teilen seinen Workspace. Jobs besitzen dagegen keinen automatisch gemeinsamen Dateibestand. `permissions` beschränkt das bereitgestellte Repository-Token.

GitLab: Ein Job steht direkt unter seinem Namen, kann einer `stage` zugeordnet sein und verwendet `script`. Runner-Tags wählen geeignete Runner; der konfigurierte Executor entscheidet etwa zwischen Shell und Container. Ein `image` greift bei Docker-/Kubernetes-Executors, macht aber einen Shell-Runner nicht zum Container.

## 3. Quellcode und Java vorbereiten

```yaml
      - uses: actions/checkout@v6
      - uses: actions/setup-java@v6
        with:
          distribution: temurin
          java-version: '17'
```

`uses` ruft eine wiederverwendbare Action auf. `with` liefert deren Eingaben. Checkout stellt die Repository-Dateien bereit; Setup Java wählt das JDK. Der eingecheckte Wrapper wählt Maven. GitLab Runner stellt den Quellcode standardmäßig bereit; die Beispielvorlage wählt das JDK über ein Containerimage. Produktionsprojekte sollten Actions auf geprüfte Commit-SHAs festlegen und Updates planen.

## 4. Den vertrauten Prüfaufruf ausführen

```yaml
      - name: Build and verify
        run: mvn clean verify
```

`run` startet einen Shell-Befehl. Die Datei liegt mit `pom.xml` im Repository-Stamm. Ein Fehlerstatus des Befehls lässt den Step und normalerweise den Job scheitern. Deaktivieren Sie diese Wirkung nicht mit `continue-on-error` oder einem erzwungenen Erfolg. GitLab verwendet denselben Befehl unter `script`.

## 5. Berichte trotz Testfehler behalten

```yaml
      - name: Preserve test reports
        if: always()
        uses: actions/upload-artifact@v7
        with:
          name: junit
          path: |
            target/surefire-reports/TEST-*.xml
            target/failsafe-reports/TEST-*.xml
          if-no-files-found: error
          retention-days: 7
```

`always()` lässt diesen Berichtsschritt auch nach einem fehlgeschlagenen Testschritt zu. Es erzeugt jedoch keine Berichte, wenn die entsprechende Phase nie lief. Der rote Job bleibt rot. Auf GitHub öffnen Sie **Actions → Workflow-Lauf → Job/Steps**, und laden unter den Run-Artefakten `junit` herunter. Der Upload allein erzeugt keine native JUnit-Testübersicht. GitLab stellt mit `artifacts: reports: junit` eine solche Auswertung bereit; `artifacts: when: always` erhält zusätzlich konfigurierte Dateiartefakte bei Fehlern.

Die Vorlagen 03 und 10 speichern außerdem einen erzeugten JaCoCo-Bericht als Artefakt. Bei einem frühen Unit-Testfehler fehlt er, weil `verify` noch nicht erreicht wurde. Nach einer Coverage-Regelverletzung liegt er dagegen vor. Ein Coverage-Report und ein JUnit-Testreport erfüllen verschiedene Zwecke.

## 6. Events auf einer Zeitlinie vorhersagen

| Handlung | GitHub-Vorlage 01/06 | GitLab-Vorlage 01/06 |
|---|---|---|
| Nur lokal committen | kein Ereignis auf GitHub | kein Ereignis auf GitLab |
| Feature-Branch pushen, noch kein Review | kein Lauf in dieser Konfiguration | Branch-Pipeline |
| Pull/Merge Request öffnen | `pull_request` | `merge_request_event` |
| Weiteren Commit in offenen Review pushen | `pull_request` mit `synchronize` | Merge-Request-Pipeline; zusätzliche Push-Pipeline unterdrückt |
| Nach `main` mergen | `push` auf `main` | Branch-/Push-Pipeline auf `main` |
| Bewusst manuell starten | `workflow_dispatch` | Pipeline in der Oberfläche starten, sofern Regeln zulassen |
| Wöchentlicher Zusatzlauf | In 06: YAML-`schedule`, Cron in UTC | In 06: Zeitplan in GitLab anlegen; konfigurierte Zeitzone beachten |

Ein Schedule ergänzt unmittelbares Feedback. Er ersetzt es nicht. GitHub-Schedules laufen auf dem Default-Branch und können sich verzögern. Die Beispiele führen bei diesen Ereignissen Prüfungen aus; ein Deployment müsste gesondert definiert werden. Branch-Schutz kann erforderliche Checks festlegen und ist eine separate Repository-Einstellung.

## Vergleich und Quellen

GitHub bietet für den Einstieg gut kombinierbare Actions und gehostete Runner. Dafür müssen Actions, Berechtigungen und Abhängigkeiten bewusst gewählt werden; JUnit-Uploads werden in diesen Vorlagen nur als Dateien aufbewahrt. GitLab verbindet in den Beispielen Stages, Runner-Konfiguration und native Testreport-Anzeige. Dafür müssen Runner, Executor, Tags und Instanzeinstellungen zusammenpassen. Beide bieten gehostete bzw. selbst verwaltete Ausführungsmöglichkeiten; Kosten und verfügbare Minuten hängen vom Konto bzw. von der Instanz ab.

- [GitHub: Bestandteile und Ablaufdiagramm](https://docs.github.com/en/actions/get-started/understand-github-actions)
- [GitHub: Workflow-Syntax](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax)
- [GitHub: Events](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows)
- [GitHub: Artefakte](https://docs.github.com/en/actions/tutorials/store-and-share-data)
- [GitLab: Pipeline-Architekturen und Diagramme](https://docs.gitlab.com/ci/pipelines/pipeline_architectures/)
- [GitLab: Workflow-Regeln](https://docs.gitlab.com/ci/yaml/workflow/)
- [GitLab: JUnit-Berichte](https://docs.gitlab.com/ci/testing/unit_test_reports/)
