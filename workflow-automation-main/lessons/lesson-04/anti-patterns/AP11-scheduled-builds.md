# AP11 – Scheduled Builds

**Gruppenarbeit:** 2–3 Personen · **Vorstellung:** 2–3 Minuten

## 1. Bedeutung und Abgrenzung

Integrationsfeedback erfolgt ausschließlich zeitgesteuert und damit verspätet. Ein ergänzender Nightly-Lauf für aufwendige oder periodische Prüfungen ist sinnvoll und wird nicht pauschal als Fehler eingeordnet.

## 2. Mögliche Situation

Ein Team integriert mehrere Änderungen tagsüber, prüft den gemeinsamen Stand jedoch erst nachts. Am Morgen sind mehrere Änderungen mögliche Ursachen des Fehlers. Die verantwortlichen Personen erhalten die Rückmeldung verspätet.

## 3. Mögliche Anzeichen

Kein Push-/Review-Trigger, lange Rückmeldeintervalle und viele Änderungen zwischen dem letzten grünen und ersten roten Lauf. Ein vorhandener Schedule allein beweist dieses Anti-Pattern nicht.

## 4. Ursachen und Prüffragen

Welche Prüfung muss zeitnah zu einer Änderung laufen? Welche ist bewusst periodisch? Erhält ein Review einen aussagekräftigen Status? Erzeugt die aktuelle Konfiguration doppelte Läufe oder lässt sie wichtige Branches ungeprüft?

## 5. Arbeitsauftrag und Versuch

Lesen Sie Schritt 06 auf beiden Plattformen. Erstellen Sie eine Ereignistabelle für Branch-Push, Pull/Merge Request, main und Wochenlauf. Zeigen Sie, welche Zeilen ohne Push-/Review-Trigger fehlen würden. Einen produktiven Zeitplan müssen Sie dafür nicht verändern.

## 6. Gegenmaßnahmen

Nutzen Sie schnelle Prüfungen bei relevanten Änderungen und ergänzende zeitgesteuerte Prüfungen für ihren eigenen Zweck. Begrenzen Sie Doppelstarts über nachvollziehbare Regeln, ohne Integrationsfeedback versehentlich auszuschalten.

## 7. Beleg und Kurzvorstellung

Präsentieren Sie die Tabelle und einen sinnvoll ergänzenden Schedule. Erklären Sie in 2–3 Minuten den Unterschied zwischen einer späten einzigen Prüfung und einer zusätzlichen periodischen Prüfung.

## 8. Grenzen und Transfer

Überarbeitung des WS25-Falls mit ausdrücklicher Abgrenzung. GitHub deklariert den Schedule in der YAML auf dem Default-Branch; GitLab verwaltet ihn in den Projekteinstellungen. Instanzgrenzen und Zeitzone sind beim echten Termin zu prüfen.

## Fachliche Quellen

- [Primärquelle 1](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows)
- [Primärquelle 2](https://docs.gitlab.com/ci/pipelines/schedules/)

Fachlicher Kern aus den bisherigen LV-Folien und verfügbaren WS25-Ausarbeitungen; für WS26 präzisiert. Stand: 26.10.2026.
