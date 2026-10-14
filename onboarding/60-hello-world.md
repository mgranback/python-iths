# Ditt första program — Hello world

Nu skriver och kör du ett Python-program. Målet är litet med flit: när det här fungerar vet
du att verktygen sitter ihop, och det är allt du behöver ha klart före lektion 1.

---

## Förkrav

Gör klart `40-uv-och-vscode.md` först. Då har du:

- en projektmapp (`C:\Kod\Pythonkurs` på Windows, `~/kod/pythonkurs` på Linux/Mac) med en
  `pyproject.toml` och en `.venv`-mapp,
- mappen öppnad i VS Code (**File → Open Folder…**),
- rätt Python vald: nere till höger i VS Code ska det stå `.venv` eller `Python 3.13.x`.

Alla kommandon nedan är **likadana på Windows och Linux/Mac**.

---

## 1. Skapa filen

I VS Code, med projektmappen öppen:

1. Håll muspekaren över filträdet till vänster → klicka på ikonen **New File…**
   (eller **File → New File**).
2. Döp filen till `hello.py` och tryck Enter.
3. Filen öppnas i editorn till höger.

Ändelsen `.py` betyder att filen innehåller Python-kod.

---

## 2. Skriv koden

Skriv exakt den här raden i `hello.py`:

```python
print("Hello world!")
```

`print(...)` skriver ut det som står inom parentesen. Texten måste stå inom
citationstecken.

**Spara filen:** `Ctrl + S` (Mac: `Cmd + S`). En osparad fil har en fylld prick i
flikens namn.

---

## 3. Kör programmet

Du kan köra på två sätt. Använd gärna båda en gång så du sett dem.

### Väg A — Run-knappen i VS Code

Klicka på **▷-knappen** uppe till höger i editorn (”Run Python File”).

En terminal öppnas nertill och kör filen åt dig. Kommandot VS Code skriver ser lite olika ut
beroende på inställning, men resultatet blir detsamma som i Väg B.

### Väg B — från terminalen

1. Öppna terminalen i VS Code: **Terminal → New Terminal**.
2. Kontrollera att du står i projektmappen — prompten ska sluta med `pythonkurs`. Gör den
   inte det:

   ```sh
   # Windows (PowerShell)
   cd C:\Kod\Pythonkurs

   # Linux / Mac
   cd ~/kod/pythonkurs
   ```

3. Kör filen:

   ```sh
   uv run hello.py
   ```

`uv run` kör `hello.py` med projektets Python och dess miljö. Första gången kan den ta en
kort stund; sedan går det snabbt.

---

## 4. Vad du ska se

```
Hello world!
```

Ser du den raden är du klar. **Grattis — allt som behövs för dag 1 är på plats.**

---

## 5. Prova att ändra något

Byt ut raden mot det här, spara, och kör igen:

```python
namn = "Johan"
print("Hello", namn)
```

Utskrift:

```
Hello Johan
```

Byt `"Johan"` mot ditt eget namn och kör en gång till. Du kommer lära dig vad `namn = ...`
och `print(a, b)` gör på lektion 1 — här räcker det att se att en ändring i filen syns i
utskriften.

---

## Vanliga fel

| Symptom | Vad det betyder | Vad du gör |
|---|---|---|
| `uv: command not found` / `uv känns inte igen` | uv finns inte i PATH | Starta om terminalen och VS Code. Hjälper inte det: gå tillbaka till `20-`/`21-installera-*.md`. |
| `error: Failed to spawn: hello.py` / `No such file or directory` | Du står i fel mapp, eller filen heter något annat | `dir` (Windows) / `ls` (Linux/Mac) ska visa `hello.py`. `cd` till rätt mapp, kontrollera stavningen. |
| `SyntaxError` | Skrivfel i koden | Jämför tecken för tecken med rutan i steg 2. Vanligast: saknat citationstecken eller saknad parentes. |
| `NameError: name 'Hello' is not defined` | Text utan citationstecken | Texten ska stå inom `"..."`: `print("Hello world!")`. |
| Inget händer när du sparar och kör i VS Code | Fel fil kördes, eller filen var osparad | Spara (`Ctrl + S`), klicka i `hello.py` så den är den aktiva fliken, kör igen. |
| Run-knappen använder fel Python | Ingen tolk vald | Klicka på Python-versionen nere till höger → välj den i projektets `.venv`. Se `40-uv-och-vscode.md` steg 5. |

---

## Klart — vad händer nu

- [ai-verktyg.md](ai-verktyg.md) — hur vi förhåller oss till AI-verktyg i kursen. Läs den innan lektion 1.
- Vill du komma vidare kan du börja med övningarna till lektion 1.
