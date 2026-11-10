# Arbeitsauftrag Workflow Automation – 10.11.2026

10.11.2026 · Online-Auftakt 11:30 · gemeinsames Wiedersehen um **12:30 und 13:15** im selben Besprechungsraum.

## Ziel und Ausgangsstand

Sie übertragen einen lokal grünen Java-Build in CI, erklären einen roten/grünen Lauf und verfolgen dasselbe JAR in einen zweiten Job. **GitHub zuerst**, anschließend das gleichartige GitLab-Pendant. Konto und Übungsrepository richten Sie vor dem Auftakt ein. Ein erster grüner Pipeline-Lauf entsteht im Einstieg; danach bearbeiten Sie den Auftrag eigenständig mit festen gemeinsamen Checkpoints.

Verwenden Sie eine eigene Übungskopie des grünen Java-Projekts aus Testing. Im Repository-Stamm müssen `pom.xml`, `mvnw`, `mvnw.cmd`, `.mvn/wrapper/`, `src/` und `.gitignore` liegen. Kopieren Sie keine `.git`- oder `target`-Ordner. Alternativ starten Sie von der [GitHub-Javademo](https://github.com/michaelulm/contdel-ws26-java-demo) auf `main`. Der vorbereitete rote Lehrer-PR bleibt unverändert.

Klonen Sie zusätzlich das [Workflow-Repository](https://gitlab.itplus.fh-joanneum.at/study/msd/msd24w/courses/contdel/workflow-automation). Seine Ordner `github-cicd/` und `gitlab-cicd/` enthalten gleich nummerierte Vorlagen; diese sind Lernmaterial und werden nicht alle gleichzeitig aktiviert.

## Vorbereitung gemeinsam mit dem Lehrenden

1. Legen Sie ein eigenes leeres GitHub-Repository an. Falls Ihre Java-Kopie noch kein Repository ist: `git init -b main`. Prüfen Sie vor jeder Remote-Änderung `git remote -v`.
2. Legen Sie `.github/workflows/ci.yml` an und übernehmen Sie den vollständigen Inhalt von `github-cicd/01-first-steps/pipeline.yml`.
3. Führen Sie lokal `mvn clean verify` aus. Stellen Sie den grünen Stand sicher.
4. Fügen Sie die eigene GitHub-URL als `origin` hinzu, falls noch keine Remote gesetzt ist. Prüfen Sie die URL; pushen Sie nicht in das Kursrepository.
5. Versionieren Sie die benannten Quellen und die Workflow-Datei. Pushen Sie `main`; öffnen Sie **Actions → Lauf → Job → Schritte**. Bestätigen Sie Commit, Trigger, Runner und Testausführung.

```powershell
git add pom.xml mvnw mvnw.cmd .mvn src .gitignore .github/workflows/ci.yml
git diff --cached --stat
git commit -m "ci: add Java verification workflow"
git push -u origin main
```

Wenn `origin` noch fehlt, verwenden Sie davor `git remote add origin IHRE_GITHUB_CLONE_URL` und ersetzen den Platzhalter durch die Clone-URL Ihres eigenen Repositories. Ein vorhandenes `origin` wird nicht blind überschrieben.

Nutzen Sie die beiden eigenen Arbeitsphasen für die folgenden Schritte. Zum ersten Checkpoint zeigen Sie den Ausgangslauf und einen nachvollziehbaren Fehler; bis zur Abschlussrunde stellen Sie den grünen Stand und Ihre Nachweise fertig. Bearbeiten Sie zuerst den Kern, danach Vertiefungen. Je Moodle-Gruppe sind fünf Minuten Vorstellung und anschließend insgesamt fünf Minuten Puffer vorgesehen.

## 1. Ausgangslauf erklären

Öffnen Sie die aktive Konfiguration und ordnen Sie die Abschnitte zu: `on` = Auslöser, `jobs` = Arbeitspakete, `runs-on` = Runner, `steps` = Reihenfolge, `uses` = wiederverwendete Action, `run` = Shellbefehl. Zeigen Sie Checkout, Java-Setup und Maven-Aufruf im Log.

Übernehmen Sie nun `github-cicd/03-testreports/pipeline.yml` vollständig in dieselbe `ci.yml`. Lesen Sie dessen Trigger, bevor Sie den nächsten Schritt ausführen.

## 2. Fehler im Pull Request beobachten und reparieren

```powershell
git switch -c exercise/workflow-red-green
git add .github/workflows/ci.yml
git commit -m "ci: publish Java test reports"
```

Ändern Sie in `src/main/java/at/fhj/msd/CalculatorImpl.java` ausschließlich `multiply` von `a * b` auf `a + b`. Prüfen Sie lokal mit `clean verify` und lesen Sie den Exitcode. Der absichtlich rote Commit ist nur für dieses Fehlerexperiment vorgesehen:

```powershell
git add src/main/java/at/fhj/msd/CalculatorImpl.java
git commit -m "test: demonstrate multiplication regression"
git push -u origin exercise/workflow-red-green
```

Öffnen Sie auf GitHub einen Pull Request nach `main`. Im zugehörigen Actions-Lauf lesen Sie eine fehlgeschlagene Assertion und laden den vorhandenen JUnit-Bericht herunter. **Erwartung:** roter Prüfjob; das fachlich falsche Ergebnis wird nicht durch angepasste Erwartungen akzeptiert.

Reparieren Sie dieselbe Methode zu `a * b`, prüfen Sie lokal den grünen Build und committen/pushen Sie diese eine Datei auf denselben Branch. Der bestehende PR erhält den neuen Lauf. Halten Sie beide Commit- und Run-Links fest. Ein grüner Lauf mergt den PR nicht automatisch.

## 3. Dasselbe Artefakt weitergeben

Ersetzen Sie die aktive Konfiguration durch `github-cicd/07-jobs-and-dependencies/pipeline.yml`, committen Sie nur diese Datei und pushen Sie denselben Branch. Lesen Sie Produzent, `needs` und Upload/Download des Artefakts.

Zeigen Sie im grünen Lauf: Maven erstellt das JAR einmal; der Folgejob übernimmt JAR und Prüfsumme und prüft genau diese Dateien. Der Jobname `package` dieser Vorlage meint den **Konsumenten**, nicht die Maven-Phase `package`.

Wiederholen Sie den gezielten Multiplikationsfehler auf diesem Branch, pushen Sie ihn und zeigen Sie den nicht ausgeführten Folgejob. Reparieren Sie anschließend wieder und pushen Sie den grünen Stand. Bei langen Warteschlangen analysieren Sie einen vorbereiteten Referenzlauf und kennzeichnen diesen Nachweis ausdrücklich als Analyse statt eigener Ausführung.

## 4. Anti-Pattern und Ergebnis

Bearbeiten Sie den zugeteilten Fall aus `lessons/lesson-04/anti-patterns/` im Workflow-Repository: Team Fast Feedback AP09/AP11, Team Flow Builders AP10/AP01 (Revisiting vom 20.10.), Team Signal Finders AP12/AP13. Verbinden Sie Situation, Anzeichen, Prüfung, Gegenmaßnahme und Grenze mit einem eigenen Pipeline-Beleg. Wiederkehrende Fälle werden als Revisiting kenntlich gemacht. Stellen Sie den Fall in 5 Minuten in eigenen Worten vor.

Füllen Sie `lessons/lesson-04/ERGEBNIS.md` aus: Repository, Commit, Auslöser, Runner, roter/grüner Lauf, Testzahl, Bericht, JAR, Prüfsumme und Sperre des Folgejobs. Erklären Sie zusätzlich, weshalb Cache und Artefakt unterschiedliche Aufgaben erfüllen.

## 5. GitLab gemeinsam vergleichen, bis 15.11. vervollständigen

Öffnen Sie die [GitLab-Javademo](https://gitlab.itplus.fh-joanneum.at/study/msd/msd24w/courses/contdel/java-ci-demo-ws26). Sie ist ein vorbereitetes, eigenständiges Beispiel desselben Java-Quellstands. Die vollständige `.gitlab-ci.yml` liegt im Stamm. Arbeiten Sie für eigene Fehlerexperimente in einem eigenen GitLab-Übungsprojekt.

| GitHub | GitLab | Ihre Erklärung |
|---|---|---|
| `.github/workflows/ci.yml` | `.gitlab-ci.yml` | Wo wird die Konfiguration erkannt? |
| `on` | `workflow: rules` | Welcher Push/PR/MR erzeugt einen Lauf? |
| `runs-on` | Runner-Zuordnung (Course: `edu`, Study: ohne Tags) und `image` | Wer führt aus, in welcher Umgebung? |
| `steps` mit `uses`/`run` | `script` | Wo stehen Build und Test? |
| Upload/Download + `needs` | `artifacts` + `needs` | Wie gelangt dasselbe JAR zum Folgejob? |
| Pull Request / Actions | Merge Request / Build → Pipelines | Wo liegen Checks, Logs und Berichte? |

**Runner-Stand 07.11.2026:** Im Course-Javademo läuft Gruppenrunner #3 mit Tag `edu` und Docker-Executor. Im Study-Bereich läuft Instanzrunner #1 (Default Runner), Kubernetes, Linux/amd64, für Jobs **ohne Tags**. Übernehmen Sie `tags: [edu]` deshalb nicht in Study. Prüfen Sie im eigenen Projekt unter Settings → CI/CD → Runners den tatsächlich verfügbaren Runner. Scope, Executor und Job-Image sind getrennte Eigenschaften.

1. Übernehmen Sie die Java-Quelldateien und die vollständige `.gitlab-ci.yml` der Demo in Ihr eigenes GitLab-Projekt. Pushen Sie den grünen Stand.
2. Öffnen Sie **Build → Pipelines**. Zeigen Sie `verify`, die JUnit-Testansicht, Coverage als herunterladbares HTML und `artifact-check`. Der zweite Job hat keinen Checkout und führt keinen Maven-Build aus.
3. Legen Sie einen Feature-Branch an, erzeugen Sie denselben Fehler und öffnen Sie einen MR. Prüfen Sie Rot, reparieren Sie die Ursache, prüfen Sie Grün. Lassen Sie `main` unverändert, bis eine bewusste Freigabe erfolgt.
4. Vergleichen Sie die Trigger: Die GitLab-Demo erlaubt Branch-Push, MR und manuellen Web-Start. Bei offenem MR unterdrückt sie die zusätzliche Branch-Push-Pipeline. Ein Tag oder Zeitplan löst dort keinen Lauf aus.
5. Übertragen Sie das Prinzip anschließend gemäß [Release Board, Lesson 04](https://gitlab.itplus.fh-joanneum.at/study/msd/msd24w/courses/contdel/delivery-pipeline-example/-/blob/main/docs/lessons/04_2026-11-10.md). Das Node-Artefakt ersetzt das JAR; der Konsument baut weiterhin nicht neu.

## Fertig, wenn überprüft

Sie können Konfiguration → Ereignis → Runner → Testfehler → Reparatur → Artefaktübergabe am eigenen Beispiel erklären. Die zweite Plattform und der Release-Board-Transfer dürfen in der Nachbereitung bis 15.11. fertiggestellt werden. Fehlende Plattformläufe bleiben explizit offen; ein lokaler Build ersetzt sie nicht. Generierte Dateien, Zugangsdaten und Runner-Tokens gehören nicht ins Repository.

[GitHub-Einstieg](https://gitlab.itplus.fh-joanneum.at/study/msd/msd24w/courses/contdel/workflow-automation/-/blob/main/docs/github-einstieg.md) · [GitLab YAML](https://docs.gitlab.com/ci/yaml/) · [Runner-Konfiguration](https://docs.gitlab.com/ci/runners/configure_runners/)
