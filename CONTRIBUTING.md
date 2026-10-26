# Zusammenarbeit bei AQ-Businessplan

Diese Seite ist unsere Spielanleitung für die Arbeit mit **Eclipse** und **GitHub**.
Sie ist kurz, damit sie gelesen wird. Wenn etwas unklar ist: im Team fragen, nicht raten.

## Die 5 Grundregeln

1. **Nie direkt auf `main` arbeiten.** `main` ist der saubere, funktionierende Stand.
2. **Jede Arbeit hat ein Issue.** Was nicht im Board steht, gibt es nicht.
3. **Jede Änderung läuft über einen eigenen Branch und einen Pull Request (PR).**
4. **Jeder PR wird von mindestens einer anderen Person angesehen**, bevor er gemerged wird.
5. **Kleine Schritte.** Lieber oft und klein als selten und riesig.

## Einmalige Einrichtung

### 1. GitHub-Token erstellen

Eclipse akzeptiert beim Hochladen nicht dein normales GitHub-Passwort, sondern ein **Personal Access Token**.

1. GitHub öffnen → Profilbild → **Settings** → **Developer settings**
2. **Personal access tokens → Tokens (classic) → Generate new token (classic)**
3. Name z. B. `eclipse`, Haken bei **repo** setzen, **Generate token**
4. Token sofort kopieren und sicher speichern, es wird nur einmal angezeigt

### 2. Name und E-Mail in Eclipse setzen

**Eclipse → Settings** (Windows/Linux: Window → Preferences) → **Team → Git → Configuration → Add Entry…**

- `user.name` = dein Name
- `user.email` = die E-Mail-Adresse deines GitHub-Kontos

### 3. Repo klonen

1. **Window → Show View → Other… → Git → Git Repositories**
2. In der Ansicht auf **Clone a Git repository** klicken
3. **URI** einfügen (auf GitHub: grüner Button **Code**, HTTPS-Adresse kopieren)
4. Benutzername = dein GitHub-Name, Passwort = dein **Token**, Haken bei **Store in Secure Store**
5. Branch `main` auswählen, **Finish**

### 4. Als Projekt in Eclipse öffnen

1. In **Git Repositories** das Repo aufklappen
2. Rechtsklick auf **Working Tree → Import Projects…**
3. Den Repo-Ordner markieren, **Finish**

Jetzt erscheint das Projekt im **Package Explorer**, und im Menü **Team** (Rechtsklick aufs Projekt) stehen alle Git-Befehle.

Sobald im Repo ein Maven-Projekt liegt, wird es stattdessen über **File → Import → Maven → Existing Maven Projects** geöffnet. Das sagen wir euch dann.

## Der Ablauf für jede Aufgabe

### Schritt 1: Issue wählen
Nimm ein Issue aus **Ready**, das dir zugewiesen ist, und setze es im Board auf **In progress**.

### Schritt 2: Aktuellen Stand holen
1. Rechtsklick aufs Projekt → **Team → Switch To → main**
2. Rechtsklick aufs Projekt → **Team → Pull**

Das machst du **jedes Mal**, bevor du etwas Neues anfängst.

### Schritt 3: Eigenen Branch anlegen
1. Rechtsklick aufs Projekt → **Team → Switch To → New Branch…**
2. **Branch name** eintragen, z. B. `feature/startkosten-maske`
3. **Checkout new branch** angehakt lassen, **Finish**

Kontrolle: Hinter dem Projektnamen im Package Explorer steht jetzt in eckigen Klammern dein Branch, z. B. `[feature/startkosten-maske]`.

### Schritt 4: Arbeiten und committen
1. Ändere oder erstelle deine Dateien
2. **Window → Show View → Other… → Git → Git Staging** öffnen
3. Geänderte Dateien aus **Unstaged Changes** nach **Staged Changes** ziehen (oder auf das Plus-Symbol klicken)
4. Unten eine **Commit message** schreiben, z. B. `Add Eingabemaske für Startkosten (#12)`
5. **Commit** klicken

Du darfst so oft committen, wie du willst.

### Schritt 5: Branch auf GitHub hochladen
1. In **Git Staging** auf **Commit and Push…** klicken (oder nach dem Commit: Rechtsklick aufs Projekt → **Team → Push Branch '…'**)
2. Im Dialog prüfen:
   - **Remote:** `origin`
   - **Remote branch name:** derselbe Name wie dein Branch (nicht `origin`!)
3. **Finish**. Beim ersten Mal kommt das Anmeldefenster: Benutzername und **Token** eintragen, **nicht wegklicken**

Das betrifft nur deinen Branch. `main` bleibt unberührt.

### Schritt 6: Pull Request auf GitHub öffnen
1. Auf GitHub erscheint oben in der Repo der gelbe Hinweis **Compare & pull request**. Klick darauf
2. **Titel** verständlich schreiben
3. In die Beschreibung `Closes #12` (Nummer deines Issues) und eine kurze Erklärung, was du gemacht hast
4. Rechts bei **Reviewers** eine Person auswählen
5. **Create pull request**
6. Im Board den Status auf **Review** setzen (falls das nicht automatisch passiert)

### Schritt 7: Review
Die Reviewerin oder der Reviewer öffnet den PR auf GitHub, schaut sich unter **Files changed** die Änderungen an und:
- schreibt Kommentare (am besten direkt an die betroffene Zeile), oder
- gibt frei über **Review changes → Approve → Submit review**

Wenn Änderungen nötig sind: einfach auf **demselben Branch** weiterarbeiten, committen und pushen. Der PR aktualisiert sich von selbst.

### Schritt 8: Mergen
Nach der Freigabe auf GitHub **Merge pull request → Confirm merge**, danach **Delete branch**.
Das Issue schließt sich automatisch und springt im Board auf **Done**.

### Schritt 9: Neuen Stand holen
Alle machen wieder:
**Team → Switch To → main**, dann **Team → Pull**.

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

## Wenn es einen Konflikt gibt

Das passiert, wenn zwei Leute dieselbe Stelle geändert haben. Kein Drama.

1. Auf deinem Branch: Rechtsklick aufs Projekt → **Team → Merge…**
2. Im Dialog **Local → main** auswählen, **Merge**
3. Meldet Eclipse Konflikte, tauchen die betroffenen Dateien mit einem **roten Konflikt-Symbol** auf
4. Rechtsklick auf die Datei → **Team → Merge Tool** und entscheiden, welche Änderungen bleiben
5. Datei speichern, dann Rechtsklick → **Team → Add to Index**
6. In **Git Staging** committen und pushen

Wenn du nicht weiterkommst: nicht allein kämpfen, Teammitglied rufen.

## Typische Stolperfallen

| Problem | Lösung |
|---------|--------|
| Anmeldefenster beim Push weggeklickt | Commit ist nur lokal. Nochmal pushen (**Team → Push Branch**) und diesmal Benutzername und Token eintragen |
| Auf GitHub gibt es einen Branch namens `origin` | Beim Push im Feld **Remote branch name** stand `origin`. Mit richtigem Namen neu pushen und den falschen Branch auf GitHub löschen |
| Ich habe auf `main` committet | Nicht pushen. Im Team melden, wir verschieben den Commit auf einen eigenen Branch |
| Team-Menü zeigt nur „Share Project“ | Das Projekt ist nicht mit dem Repo verbunden. Über **Git Repositories → Import Projects…** neu importieren |
| Ich weiß nicht, auf welchem Branch ich bin | Package Explorer: Name in eckigen Klammern hinter dem Projekt |

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
- Vor dem Arbeiten auf `main` einen **Pull** machen
- Kleine, häufige Commits
- Dateien in die richtigen Ordner legen (`docs/`, `src/`)

**Don't**
- Passwörter, Tokens oder persönliche Daten committen
- Build-Dateien oder IDE-Ordner committen (steht in der `.gitignore`)
- Auf `main` arbeiten oder dorthin pushen

## Für Fortgeschrittene: dasselbe im Terminal

```bash
git switch main && git pull
git switch -c feature/kurzer-name
git add . && git commit -m "Add Beschreibung (#12)"
git push -u origin feature/kurzer-name
```

Danach weiter mit dem Pull Request auf GitHub wie oben.

## Fragen?

Im Team-Chat melden oder ein Issue mit dem Label `frage` anlegen.