# Runner, Executor und Fehlerdiagnose

Öffnen Sie in GitLab die CI/CD-Runner-Einstellungen Ihres Projekts. Prüfen Sie Aktivierung, Zustand, Tags und Berechtigung für ungetaggte Jobs. **Runner-Stand 07.11.2026:** Im Course-Javademo läuft Gruppenrunner #3 mit Tag `edu` und Docker-Executor. Im Study-Bereich läuft Instanzrunner #1 (Default Runner), Kubernetes, Linux/amd64, für Jobs **ohne Tags**. Übernehmen Sie `tags: [edu]` deshalb nicht in Study. Prüfen Sie im eigenen Projekt unter Settings → CI/CD → Runners den tatsächlich verfügbaren Runner. Scope, Executor und Job-Image sind getrennte Eigenschaften.

| Beobachtung | Mögliche Ursache | Nächste Prüfung |
|---|---|---|
| Pipeline fehlt | Trigger/Regel oder ungültige YAML | CI Lint, Ereignis, Branch und include-Pfade |
| pending | Kein passender verfügbarer Runner | Tags, Runner-Zuordnung, Schutzregeln, Kapazität |
| Image ignoriert | Shell-Executor | Job-Log lesen; JDK und Shell auf dem Host prüfen |
| sh mvnw scheitert | Wrapper fehlt oder kein Linux-/POSIX-Pfad | .mvn, Wrapper, Executor und Internetzugang |
| Tests rot | Assertion, Umgebung oder Abhängigkeit | Ersten relevanten Fehler und Testbericht lesen |
| Kein Report | Testphase nicht erreicht oder Pfad falsch | Log und tatsächliche Dateien prüfen |
| Folgejob übersprungen | Abhängigkeit rot | needs/Stages und vorherigen Job lesen |

Die GitLab-Vorlagen verwenden ein Linux-Image mit JDK und erwarten einen Docker- oder Kubernetes-Executor. Bei Shell-Runnern wirkt `image` nicht; stimmen Sie Toolchain und Befehle mit dem lokalen Runner ab. Auf einem Windows-Shell-Runner ist etwa `.\mvnw.cmd` statt `sh mvnw` erforderlich. Der Scope (Instance/Group/Project) sagt darüber nichts aus.

GitHub-hosted `ubuntu-24.04` ist der Vergleichspfad. Selbst betriebene Runner müssen die Anforderungen der verwendeten Actions erfüllen. Prüfen Sie bei Action-Upgrades die offiziellen Repositories. Kein `|| true` und kein `continue-on-error` darf einen verpflichtenden Testfehler verdecken.

[GitLab Executors](https://docs.gitlab.com/runner/executors/) · [Runner configuration](https://docs.gitlab.com/ci/runners/configure_runners/) · [GitHub runners](https://docs.github.com/en/actions/concepts/runners)
