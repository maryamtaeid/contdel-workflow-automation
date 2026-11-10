# AP13 – Spam Feedback

**Gruppenarbeit:** 2–3 Personen · **Vorstellung:** 2–3 Minuten

## 1. Bedeutung und Abgrenzung

Ungezielte, wiederholte Meldungen verdrängen die Information, auf die jemand reagieren sollte. Das Problem ist fehlende Auswahl und Zuständigkeit, nicht eine feste erlaubte Nachrichtenanzahl.

## 2. Mögliche Situation

Jeder Job sendet jede erfolgreiche Statusänderung in denselben Kanal. Bei einem realen Fehler gehen Testname und Handlungsbedarf zwischen vielen gleichen Erfolgsmeldungen unter.

## 3. Mögliche Anzeichen

Doppelte Push-/Review-Läufe, mehrere Meldungen für denselben Fehler, breite Verteiler und stummgeschaltete Kanäle. Ein umfangreicher Bericht zur gezielten Analyse ist nicht automatisch Spam.

## 4. Ursachen und Prüffragen

Welche Zustandsänderung ist handlungsrelevant? Wer soll reagieren? Kann eine Zusammenfassung auf Detailberichte verweisen? Sind mehrere Benachrichtigungsquellen parallel aktiviert?

## 5. Arbeitsauftrag und Versuch

Nutzen Sie die Vorlagen 06 und 10. Zeichnen Sie für denselben Commit die möglichen Läufe und markieren Sie Duplikate. Entwerfen Sie eine kleine Benachrichtigungsregel für ersten Fehler, anhaltenden Fehler und Wiederherstellung. Versenden Sie keine echten Benachrichtigungen.

## 6. Gegenmaßnahmen

Vermeiden Sie unnötige Doppelstarts, bündeln Sie zusammengehörige Meldungen und richten Sie Empfänger nach Verantwortung aus. Detailberichte bleiben abrufbar. Eine ausschließlich stumme Pipeline löst das Problem nicht.

## 7. Beleg und Kurzvorstellung

Zeigen Sie Ihre Ereignis-/Empfängertabelle und eine aussagekräftige Fehlermeldung. Erläutern Sie in 2–3 Minuten, was bewusst zusammengefasst wird und welches Signal erhalten bleibt.

## 8. Grenzen und Transfer

Fortsetzung der bisherigen Folien. AP12 liefert die notwendige Informationsqualität. Rückbezug AP05 Bloated Build: unnötig mehrfach ausgeführte Arbeit kann zusätzliche Meldungen erzeugen; die beiden Probleme sind getrennt zu prüfen.

## Fachliche Quellen

- [Primärquelle 1](https://docs.gitlab.com/ci/jobs/job_rules/#avoid-duplicate-pipelines)
- [Primärquelle 2](https://docs.github.com/en/actions/how-tos/write-workflows/choose-when-workflows-run/control-workflow-concurrency)

Fachlicher Kern aus den bisherigen LV-Folien und verfügbaren WS25-Ausarbeitungen; für WS26 präzisiert. Stand: 26.10.2026.
