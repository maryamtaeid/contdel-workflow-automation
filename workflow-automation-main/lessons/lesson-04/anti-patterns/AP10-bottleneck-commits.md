# AP10 – Bottleneck Commits

**Gruppenarbeit:** 2–3 Personen · **Vorstellung:** 2–3 Minuten

## 1. Bedeutung und Abgrenzung

Viele zurückgehaltene Änderungen treffen gebündelt auf die gemeinsame Integrations- und Feedbackstrecke. In den bisherigen LV-Unterlagen steht besonders die späte Abgabe ohne Zeit zur Reaktion im Vordergrund; der Begriff wird hier in diesem Sinn verwendet.

## 2. Mögliche Situation

Mehrere Personen integrieren kurz vor Ende des Arbeitstages größere Pakete. Die Pipeline wartet oder meldet einen Fehler, während die für die Änderung zuständige Person nicht mehr erreichbar ist. Eine andere Person muss Kontext rekonstruieren.

## 3. Mögliche Anzeichen

Zeitlich gebündelte Integrationen, Warteschlangen, große Änderungen und fehlende Zuständigkeit nach dem Push. Ein einzelner langsamer Runner ist ein anderer Befund; unterscheiden Sie Lastspitze, Jobdauer und organisatorische Übergabe.

## 4. Ursachen und Prüffragen

Warum werden Änderungen aufgeschoben? Wann ist Feedback verfügbar? Ist jemand für die Reparatur zuständig? Welche notwendige Freigabe ist tatsächlich ein Engpass, und welche Verzögerung entsteht durch zu große Änderungspakete?

## 5. Arbeitsauftrag und Versuch

Vergleichen Sie zwei konstruierte Abläufe: drei kleine überprüfte Integrationen mit Reaktionszeit gegenüber einer späten Sammelintegration. Markieren Sie Review, Runner-Wartezeit, Ausführung und Reparatur getrennt. Verwenden Sie keine erfundenen gemessenen Minutenwerte.

## 6. Gegenmaßnahmen

Verteilen Sie kleine integrierbare Schritte, verfolgen Sie den zugehörigen Lauf und klären Sie eine Übergabe. Beschleunigen Sie die Pipeline erst nach einer Messung ihrer tatsächlichen Engstelle. Ein bloß größerer Runner löst die fehlende Zuständigkeit nicht.

## 7. Beleg und Kurzvorstellung

Zeigen Sie den Ablauf und eine konkrete organisatorische bzw. technische Verbesserung. Erklären Sie in 2–3 Minuten, wie jemand nach Ihrer Integration einen Fehler erkennen und bearbeiten kann.

## 8. Grenzen und Transfer

Überarbeitung des WS25-Falls. Rückbezug AP06 Slow Machine und AP05 Bloated Build vom 20.10.: Ressourcen- und Arbeitsumfangsprobleme werden hier nur bei entsprechendem Beleg hinzugezogen. AP09 betrifft primär die Integrationsfrequenz.

## Fachliche Quellen

- [Primärquelle 1](https://dora.dev/capabilities/continuous-integration/)
- [Primärquelle 2](https://docs.gitlab.com/ci/runners/configure_runners/)

Fachlicher Kern aus den bisherigen LV-Folien und verfügbaren WS25-Ausarbeitungen; für WS26 präzisiert. Stand: 26.10.2026.
