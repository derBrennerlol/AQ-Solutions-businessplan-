# Zusammenarbeit bei AQ-Businessplan

Diese Seite ist unsere Spielanleitung. Sie ist kurz, damit sie gelesen wird.
Wenn etwas unklar ist: im Team fragen, nicht raten.

## Die 5 Grundregeln

1. **Nie direkt auf `main` arbeiten.** `main` ist der saubere, funktionierende Stand.
2. **Jede Arbeit hat ein Issue.** Was nicht im Board steht, gibt es nicht.
3. **Jede Änderung läuft über einen eigenen Branch und einen Pull Request (PR).**
4. **Jeder PR wird von mindestens einer anderen Person angesehen**, bevor er gemerged wird.
5. **Kleine Schritte.** Lieber oft und klein als selten und riesig.

## Der Ablauf Schritt für Schritt

### Einmalig: Repo klonen

```bash
git clone https://github.com/derBrennerlol/AQ-Solutions-businessplan-.git
cd <REPO>
```

### Für jede Aufgabe

**1. Issue wählen**
Nimm ein Issue aus *Ready*, das dir zugewiesen ist, und setze es im Board auf *In progress*.

**2. Aktuellen Stand holen**
```bash
git switch main
git pull
```

**3. Eigenen Branch anlegen**
```bash
git switch -c feature/kurzer-name
```

**4. Arbeiten und committen**
```bash
git add .
git commit -m "Add Eingabemaske für Startkosten (#12)"
```
Du darfst so oft committen, wie du willst.

**5. Branch auf GitHub hochladen**
```bash
git push -u origin feature/kurzer-name
```
Das betrifft nur deinen Branch. `main` bleibt unberührt.

**6. Pull Request öffnen**
Auf GitHub erscheint ein Button **Compare & pull request**. Dort:
- verständlichen Titel schreiben
- in die Beschreibung `Closes #12` (Nummer deines Issues)
- kurz erklären, was du gemacht hast
- eine Person als **Reviewer** auswählen
- Board-Status auf *Review* setzen

**7. Review**
Die Reviewerin oder der Reviewer schaut den Code bzw. die Datei an, kommentiert und gibt frei (**Approve**) oder bittet um Änderungen.
Änderungen machst du einfach auf demselben Branch und pushst erneut, der PR aktualisiert sich selbst.

**8. Mergen**
Nach der Freigabe auf **Merge pull request** klicken (wer den PR geschrieben hat, darf mergen), danach **Branch löschen**.
Das Issue schließt sich automatisch und springt auf *Done*.

**9. Alle anderen holen sich den neuen Stand**
```bash
git switch main
git pull
```

## Branch-Namen

| Präfix | Wofür | Beispiel |
|--------|-------|----------|
| `feature/` | neue Funktion | `feature/startkosten-maske` |
| `fix/` | Fehler beheben | `fix/rundungsfehler-umsatz` |
| `docs/` | Dokumentation | `docs/projektplan` |
| `chore/` | Aufräumen, Setup | `chore/gitignore` |

Klein schreiben, Wörter mit Bindestrich trennen, kurz und sprechend.

## Commit-Nachrichten

- Kurz, im Imperativ, am besten mit Issue-Nummer: `Add Berechnung Umsatzplan (#14)`
- Ein Commit = ein sinnvoller Schritt
- Keine Nachrichten wie `fix`, `asdf` oder `Änderungen`

## Pull Requests

- **Klein halten:** Ein PR löst ein Issue.
- **Reviewen innerhalb von 1 bis 2 Tagen.** Wer als Reviewer eingetragen ist, kümmert sich.
- **Freundlich bleiben:** Wir kritisieren den Code, nicht die Person.
- Offene Kommentare müssen vor dem Merge geklärt sein.

## Wenn es einen Merge-Konflikt gibt

Das passiert, wenn zwei Leute dieselbe Stelle geändert haben. Kein Drama:

```bash
git switch main
git pull
git switch feature/kurzer-name
git merge main
```

Git markiert die Konfliktstellen in den Dateien. Entscheide, was bleiben soll, speichere, dann:

```bash
git add .
git commit
git push
```

Wenn du nicht weiterkommst: nicht allein kämpfen, Teammitglied rufen.

## Das Project-Board

| Spalte | Bedeutung |
|--------|-----------|
| Backlog | Gesammelt, noch nicht priorisiert |
| Ready | Besprochen, klar beschrieben, bereit |
| In progress | Jemand arbeitet daran |
| Review | PR ist offen, wartet auf Review |
| Done | Erledigt |

- Maximal **2 Issues gleichzeitig** in *In progress* pro Person.
- Wer blockiert ist, schreibt einen Kommentar im Issue.
- Jede Person pflegt ihre eigenen Karten.
- Wöchentliches Treffen: Board gemeinsam durchgehen.

## Dos and Don'ts

**Do**
- Vor dem Arbeiten `git pull` auf `main`
- Kleine, häufige Commits
- Dateien sinnvoll benennen und in den richtigen Ordner legen (`docs/`, `src/`)

**Don't**
- Passwörter, Zugangsdaten oder persönliche Daten committen
- Build-Dateien oder IDE-Ordner committen (steht in der `.gitignore`)
- `git push --force` auf geteilten Branches

## Fragen?

Im Team-Chat melden oder ein Issue mit dem Label `frage` anlegen.
