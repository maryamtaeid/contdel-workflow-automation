# Plattformvergleich

| Konzept | GitHub Actions | GitLab CI/CD |
|---|---|---|
| Einstieg | .github/workflows/ci.yml | .gitlab-ci.yml |
| Ereignis | on | workflow:rules und job rules |
| Review | pull_request | merge_request_event |
| Ablauf | Jobs, Steps, needs | Jobs, stages, needs, script |
| Ausführung | runs-on wählt Runner | Runner-Tags; image gilt bei unterstütztem Executor |
| JUnit | Hier XML als Upload-Artefakt | reports:junit integriert Ergebnisse |
| Cache | setup-java: cache=maven | cache und tatsächliches Maven-Repository |
| Artefaktübergabe | upload/download-artifact | artifacts + needs:artifacts |
| Matrix | strategy:matrix | parallel:matrix |
| Wiederverwendung | workflow_call | include und extends |
| Manuell | workflow_dispatch | Pipeline in der UI bzw. when:manual für Jobs |
| Laufbegrenzung | timeout-minutes, concurrency | timeout, interruptible; Auto-Cancel ist separat zu konfigurieren |

Vergleichen Sie denselben Commit, dieselbe Testmenge, dasselbe Compilerziel und dieselbe Artefaktaussage. Verschiedene Runner können unterschiedliche Laufzeiten zeigen; ein einzelner Lauf belegt keine generelle Überlegenheit einer Plattform.
