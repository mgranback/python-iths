# Koppla ihop uv och VS Code — skapa ett projekt

Nu knyter du ihop det du installerat: du skapar ett **uv-projekt** och ställer in VS Code så
att Run, felsökning och terminalen använder samma Python och samma paket som uv.

Vi jobbar projektbaserat hela kursen — bl.a. är varje del av inlämningsuppgiften ett eget
uv-projekt.

---

## Förkrav

- `20-installera-windows.md` **eller** `21-installera-linux-mac.md` — `uv` och Python 3.13
  installerade (`uv self version` skriver ut en versionsrad).
- `30-texteditor.md` — Visual Studio Code med extensionerna **Python** och **Jupyter**.

Alla kommandon nedan är **likadana på Windows och Linux/Mac**. Där något skiljer sig står
det ut.

---

## Vad ett projekt är

Ett *projekt* är en mapp med en `pyproject.toml` som listar vilken Python-version och vilka
paket som ska användas. uv läser den filen och bygger en egen, isolerad miljö (`.venv`) för
just den mappen. Två projekt kan använda olika Python-versioner och olika paket utan att
krocka.

---

## 1. Skapa projektmappen

Öppna en terminal (**PowerShell** på Windows, valfri terminal på Linux/Mac) och skapa en
mapp för kursen. Lägg den någonstans du lätt hittar tillbaka till.

```sh
# Windows (PowerShell)
mkdir C:\Kod\Pythonkurs
cd C:\Kod\Pythonkurs

# Linux / Mac
mkdir -p ~/kod/pythonkurs
cd ~/kod/pythonkurs
```

Prompten i terminalen ska nu sluta med `Pythonkurs` respektive `pythonkurs`. Här sparar du
all kod under kursen — skapa gärna undermappar för övningar och inlämningar senare.

---

## 2. Skapa projektet

I mappen, kör:

```sh
uv init --no-package --python 3.13
```

- `--no-package` ger ett enkelt projekt där du lägger `.py`-filer direkt i mappen. Utan
  flaggan bygger uv i stället ett paket med en `src/`-mapp — det behöver vi inte i kursen.
- `--python 3.13` sätter lägstanivån. Nyare Python går bra.

uv skapar bl.a.:

| Fil | Vad |
|---|---|
| `pyproject.toml` | projektets definition — Python-version och paket |
| `main.py` | en liten exempelfil att börja i |
| `.python-version` | vilken Python-version mappen använder |
| `README.md`, `.gitignore` | tomma mallar; uv sätter också upp git här (mer om git i lektion 3) |

---

## 3. Kör en gång så att miljön skapas

```sh
uv run main.py
```

Första gången gör `uv run` tre saker: laddar hem Python om det behövs, skapar miljön
`.venv` i mappen, och kör sedan filen. Du ska se `Hello from pythonkurs!`.

> **Viktigt:** `.venv`-mappen skapas först vid `uv run`, `uv sync` eller `uv add` — **inte**
> redan vid `uv init`. VS Code behöver att `.venv` finns för nästa steg.

---

## 4. Öppna mappen i VS Code

**File → Open Folder…** → välj din projektmapp (`C:\Kod\Pythonkurs` / `~/kod/pythonkurs`).

Filträdet till vänster ska visa `main.py`, `pyproject.toml` med flera.

Godkänner VS Code frågar om du "litar på författarna till filerna i den här mappen" — svara
ja (det är din egen mapp).

---

## 5. Välj rätt Python (interpreter)

VS Code måste peka på Pythonen i projektets `.venv`, annars hittar den inte dina paket.

1. Öppna `main.py` i editorn.
2. Klicka på Python-versionen **nere till höger** i statusraden (eller
   **Ctrl + Shift + P → Python: Select Interpreter**).
3. Välj den som ligger i projektets `.venv`:
   - **Windows:** `.venv\Scripts\python.exe`
   - **Linux / Mac:** `./.venv/bin/python`

   Den är oftast redan förvald och märkt **Recommended**.

Syns ingen `.venv` i listan: kör steg 3 (`uv run main.py`) i terminalen, klicka sedan
**Refresh** i listan — eller kör **Ctrl + Shift + P → Developer: Reload Window**.

---

## 6. Kör kod från VS Code

- **Run-knappen:** ▷ uppe till höger när en `.py`-fil är öppen. En terminal öppnas nertill
  och kör filen.
- **Integrerad terminal:** **Terminal → New Terminal**. Kör kod med `uv run din_fil.py`
  eller starta en Python-tolk med `uv run python`.

Både Run/Debug och terminalen använder nu projektets `.venv`.

---

## 7. Lägg till och ta bort paket

Behöver du ett tredjepartspaket, t.ex. testverktyget `pytest`:

```sh
uv add pytest
```

- `uv remove pytest` tar bort det igen.
- `uv tree` visar installerade paket och deras beroenden.
- `pyproject.toml` och `uv.lock` uppdateras automatiskt varje gång.

Kör alltid programmet med `uv run` — då ser uv till att miljön stämmer med `pyproject.toml`
innan koden startar.

---

## Verifiera att allt sitter ihop

I den integrerade terminalen i VS Code:

```sh
uv run python -c "import sys; print(sys.executable)"
```

Sökvägen som skrivs ut ska innehålla din projektmapp och `.venv`. Gör den det använder
VS Code och uv samma miljö — klart.

---

## Vanliga fel

| Symptom | Vad du gör |
|---|---|
| **Select Interpreter visar ingen `.venv`** | Kör `uv run main.py` i terminalen, tryck **Refresh**, annars `Developer: Reload Window`. |
| **`ModuleNotFoundError` fast du kört `uv add`** | Du körde filen med "vanlig" Python. Kör med `uv run din_fil.py`, och kontrollera vald interpreter (steg 5). |
| **`uv: command not found` i VS Code-terminalen** | Starta om VS Code helt efter uv-installationen så att PATH läses om. |
| **Terminalen står i fel mapp** | `cd` till projektmappen. Prompten ska sluta med `Pythonkurs` / `pythonkurs`. |
| **uv skapade en `src/`-mapp** | Du glömde `--no-package`. Enklast: radera mappinnehållet och kör `uv init --no-package --python 3.13` igen. |

---

## Två specialfall

**Bara en mapp med lösa script, utan projektfil.** Kör `uv venv` för att skapa `.venv`, välj
den i VS Code som ovan. `uv run din_fil.py` fungerar också direkt i en mapp utan
`pyproject.toml`.

**Ett projekt som redan har en `pyproject.toml`** (t.ex. deluppgifterna i
inlämningsuppgiften). Kör då **inte** `uv init` — kör `uv sync` i mappen för att skapa
`.venv` och installera de paket som redan står i `pyproject.toml`. `uv run ...` gör samma
sak automatiskt.

---

Nästa steg: [50-jupyter.md](50-jupyter.md)
