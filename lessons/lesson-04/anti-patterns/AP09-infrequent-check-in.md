# AP09 – Infrequent Check-In

**Gruppenarbeit:** 2–3 Personen · **Vorstellung:** 2–3 Minuten

## 1. Bedeutung und Abgrenzung

Änderungen werden zu selten in den gemeinsamen Entwicklungsstand integriert. Viele lokale Commits oder Pushes auf einen langlebigen Branch können weiterhin mit seltener Team-Integration einhergehen.

## 2. Mögliche Situation

Zwei Personen ändern denselben Vertrag auf getrennten Branches. Beide Branch-Pipelines sind grün. Erst nach mehreren Tagen werden die Änderungen zusammengeführt und ein Integrationstest schlägt fehl.

## 3. Mögliche Anzeichen

Lange getrennte Branches, große Review-Pakete, späte Konflikte und große Zeitabstände zwischen gemeinsamer Integration und Feedback. Die bloße Anzahl von Commits ist kein ausreichendes Maß.

## 4. Ursachen und Prüffragen

Wann begegnen sich die Änderungen tatsächlich? Gibt es kleine integrierbare Schritte? Verhindert ein notwendiges Review kleine Änderungen oder nur eine unklare Arbeitsorganisation? Ein häufiger Pull vom Hauptzweig ist nicht dasselbe wie das Integrieren der eigenen Änderung.

## 5. Arbeitsauftrag und Versuch

Verwenden Sie die Ereignistabelle aus Schritt 06. Zeichnen Sie zwei Branch-Verläufe und markieren Sie lokale Commits, Pushes, Review und Merge getrennt. Legen Sie für dieselbe fachliche Änderung zwei kleinere integrierbare Schritte fest und nennen Sie die jeweils erforderliche Prüfung.

## 6. Gegenmaßnahmen

Integrieren Sie kleine, verständliche Änderungen regelmäßig und überprüfen Sie den gemeinsamen Stand. Begrenzen Sie unfertiges Verhalten bei Bedarf durch geeignete Feature-Schalter. Abstimmung und Review bleiben Teil des Ablaufs.

## 7. Beleg und Kurzvorstellung

Präsentieren Sie die zwei Zeitlinien und den frühesten Punkt, an dem das Team den Vertragsbruch erkennen kann. Verwenden Sie in 2–3 Minuten die Begriffe Commit, Push und Integration korrekt.

## 8. Grenzen und Transfer

Überarbeitung des WS25-Falls. Die frühere pauschale Gleichsetzung von häufigem Committen und CI wird präzisiert. Wiederaufnahme der Git-Übung vom 06.10.; AP08 beschreibt die Reaktion, wenn ein gemeinsamer Stand bereits rot ist.

## Fachliche Quellen

- [Primärquelle 1](https://martinfowler.com/articles/continuousIntegration.html)
- [Primärquelle 2](https://dora.dev/capabilities/continuous-integration/)

Fachlicher Kern aus den bisherigen LV-Folien und verfügbaren WS25-Ausarbeitungen; für WS26 präzisiert. Stand: 26.10.2026.
