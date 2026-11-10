# AP12 – Impeding action with minimal feedback

**Gruppenarbeit:** 2–3 Personen · **Vorstellung:** 2–3 Minuten

## 1. Bedeutung und Abgrenzung

Eine Rückmeldung zeigt zwar einen Status, liefert aber zu wenig Kontext für eine Handlung. Entscheidend sind verständliche Ursache, betroffener Stand und nächster Zugriff auf die Belege, nicht möglichst große Logmengen.

## 2. Mögliche Situation

Eine Gruppe sieht nur „Build failed“. Der Testname und der JUnit-Bericht fehlen, die Änderung ist nicht verlinkt. Die Fehlersuche beginnt bei null, obwohl die Pipeline die relevanten Details erzeugt hatte.

## 3. Mögliche Anzeichen

Generische Meldung, kein Commit-/Joblink, fehlende Berichte, abgeschnittene Assertion oder keine erkennbare Zuständigkeit. Prüfen Sie auch, ob der Bericht wegen einer nie erreichten Testphase fehlt.

## 4. Ursachen und Prüffragen

Welche Information benötigt die Person für die nächste Handlung? Ist der Fehler reproduzierbar? Zeigt die Oberfläche einen Testfehler oder einen Setup-Fehler? Sind die Daten zugänglich, ohne Geheimnisse oder unnötige Inhalte weiterzugeben?

## 5. Arbeitsauftrag und Versuch

Verwenden Sie den roten Lauf aus Schritt 03. Schreiben Sie zuerst eine unzureichende Einzeilenmeldung und danach eine verbesserte Meldung mit Commit, Job/Test, erwarteter/erhaltener Antwort und Reportlink. Senden Sie die Meldung nicht an echte Kanäle; dokumentieren Sie sie im Ergebnisbogen.

## 6. Gegenmaßnahmen

Erhalten Sie Reports auch bei Testfehlern, verwenden Sie sprechende Testnamen und verlinken Sie die relevante Stelle. Geben Sie einen konkreten nächsten Schritt und die zuständige Rolle an. Begrenzen Sie sensible oder unbrauchbare Ausgaben.

## 7. Beleg und Kurzvorstellung

Zeigen Sie die beiden Meldungen und erklären Sie die erste sinnvolle Reaktion. Die 2–3-minütige Vorstellung soll den zusätzlichen Handlungsspielraum deutlich machen, ohne einfach das gesamte Log vorzulesen.

## 8. Grenzen und Transfer

Fortsetzung der bisherigen Anti-Pattern-Folien. AP13 behandelt die umgekehrte Überlastung durch zu viele Meldungen. AP07 erinnert daran, dass ein verständlicher grüner Bericht trotzdem nur seinen tatsächlichen Testumfang belegt.

## Fachliche Quellen

- [Primärquelle 1](https://docs.gitlab.com/ci/testing/unit_test_reports/)
- [Primärquelle 2](https://docs.github.com/en/actions/how-tos/monitor-workflows/use-workflow-run-logs)

Fachlicher Kern aus den bisherigen LV-Folien und verfügbaren WS25-Ausarbeitungen; für WS26 präzisiert. Stand: 26.10.2026.
