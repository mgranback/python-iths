# Jupyter / JupyterLab — installera och använda

En **Jupyter Notebook** (filändelse `.ipynb`) är ett dokument där du blandar körbar
Python-kod, text, bilder och grafer i samma fönster. Du kör koden en bit i taget och ser
svaret direkt under.

Du använder Jupyter **löpande under kursen**, inte bara i slutet:

- Många övningar delas ut som notebooks med inbyggd självrättning.
- Föreläsningsexemplen (live coding) är notebooks som du kan öppna och köra själv.
- Kom-igång-guiden till inlämningsuppgiften (`projekt/getting-started.ipynb`) är en notebook.

Därför ska du få igång Jupyter redan nu, före lektion 1. Vi kör **JupyterLab i
webbläsaren** (Väg A nedan) — se till att den fungerar. Att i stället öppna notebooks i
VS Code går bra (Väg B), men du ska ha JupyterLab på plats.

---

## Förkrav

Gör klart i tur och ordning först:

1. `20-installera-windows.md` **eller** `21-installera-linux-mac.md` — `uv` och Python 3.13.
2. `30-texteditor.md` — Visual Studio Code. (Jupyter-extensionen används i Väg B nedan.)
3. `40-uv-och-vscode.md` — skapa ett projekt med `uv init --no-package --python 3.13` och
   kör `uv run main.py` en gång så att `.venv`-mappen skapas.

Öppna terminalen så här när stegen nedan säger "i terminalen":

- **Windows:** VS Code → **Terminal → New Terminal** (en PowerShell öppnas nere i fönstret).
- **Linux / Mac:** VS Code → **Terminal → New Terminal**, eller ett vanligt terminalfönster.

Kommandona är **exakt likadana** på Windows och Linux/Mac. Där något skiljer sig står det ut.

---

## Väg A — JupyterLab i webbläsaren (så här gör vi på kursen)

JupyterLab startar du från terminalen; det öppnas i webbläsaren. Samma kommando som
kursens `just lab`.

### 1. Kontrollera att projektet finns

I terminalen, gå till din projektmapp (den du skapade i `40-uv-och-vscode.md`) och lista
innehållet:

```sh
# Windows (PowerShell)
cd C:\Kod\Pythonkurs
dir

# Linux / Mac
cd ~/kod/pythonkurs
ls -a
```

Du ska se `pyproject.toml`, `main.py` och en mapp som heter `.venv`. Saknas `.venv`, kör
`uv run main.py` en gång så skapas den.

### 2. Lägg de notebooks du ska jobba med i mappen

JupyterLab visar filerna i mappen du startar det från. Utdelade övnings-`.ipynb`-filer:
dra in dem i projektmappen först.

### 3. Starta JupyterLab

I terminalen, i projektmappen:

```sh
uv run --with jupyter jupyter lab
```

- `uv run --with jupyter` lånar in Jupyter för just den här körningen. Vill du installera
  det permanent i projektet: `uv add jupyter` (sedan räcker `uv run jupyter lab`).
- Webbläsaren öppnas på en adress som `http://localhost:8888/lab`. Gör den inte det,
  kopiera raden som börjar med `http://localhost:8888/lab?token=…` från terminalen och
  klistra in i webbläsaren.

### 4. Öppna eller skapa en notebook

- Till vänster ser du filerna. **Dubbelklicka på en `.ipynb`** för att öppna den.
- Ny notebook: **File → New → Notebook**. Döp om via högerklick på fliken.

### 5. Välj kärna (kernel)

När notebooken öppnas frågar JupyterLab efter kärna. Välj **Python 3 (ipykernel)** — det
är projektets `.venv`, eftersom du startade via `uv run`. Byt senare via menyn uppe till
höger eller **Kernel → Change Kernel…**.

### 6. Kör din första cell

Klicka i cellen, skriv:

```python
print("Hello from Jupyter")
1 + 1
```

Tryck **Shift + Enter**. Under cellen dyker utskriften `Hello from Jupyter` upp, och därefter
`2` (svaret på sista raden visas automatiskt). En ny cell skapas nedanför.

### 7. Stäng av när du är klar

Notebooken slutar fungera när servern stängs av. **Ctrl + C** (två gånger) i terminalen,
eller **File → Shut Down** i JupyterLab.

Behöver en notebook ett paket den inte har (`ModuleNotFoundError`): stäng av servern och
starta om med paketet inlånat, t.ex. `uv run --with jupyter --with pyyaml jupyter lab`
(eller `uv add <paket>` permanent).

Klart. Jupyter fungerar.

---

## Väg B — Jupyter i VS Code

Vill du ha notebooken i editorn bredvid resten av koden går det via extensionen **Jupyter**
(installeras i `30-texteditor.md`).

### 1. Installera Jupyter i projektet

I terminalen, i projektmappen:

```sh
uv add jupyter
```

`uv` laddar ner Jupyter och skriver in det i `pyproject.toml`. Det tar en stund första
gången. Kommandot ska sluta utan röd text.

### 2. Öppna projektmappen i VS Code

**File → Open Folder…** → välj din projektmapp. VS Code ska visa filerna till vänster.

### 3. Skapa eller öppna en notebook

- Högerklicka i filträdet → **New File…** → döp till `prov.ipynb`.
- Eller dra in en utdelad `.ipynb` i projektmappen och dubbelklicka på den.

### 4. Välj kärna (kernel)

Uppe till höger i notebooken står det **Select Kernel** (eller ett Python-versionsnummer).
Klicka där:

1. Välj **Python Environments…**
2. Välj den som ligger i ditt projekt och har `.venv` i sökvägen, t.ex.
   `.venv (Python 3.13.x)` eller `./.venv/bin/python`.

Ber VS Code att få installera **ipykernel** — säg **ja**.

Syns ingen `.venv` i listan: kör `uv add jupyter` i projektmappen, sedan
**Ctrl + Shift + P → Developer: Reload Window**.

### 5. Kör en cell

Klicka i cellen, skriv `print("Hello from Jupyter")` och tryck **Shift + Enter**.

---

## Så använder du en notebook

**Två sorters celler:**

| Cell | Vad | Hur du byter |
|---|---|---|
| **Code** | Python som körs | tryck `Y` när cellen är markerad (inte i redigeringsläge) |
| **Markdown** | text, rubriker, tabeller — körs till formaterad text | tryck `M` |

**Köra celler:**

- **Shift + Enter** — kör cellen och hoppa till nästa.
- **Ctrl + Enter** — kör cellen och stanna kvar.
- Kör **uppifrån och ner**. En cell långt ner kan bero på en variabel som skapas högre upp.
- Använd **inte** "Run All" på övnings- och guide-notebooks — vissa celler är gjorda att
  fela med flit för att visa hur ett felmeddelande ser ut. Kör en cell i taget.

**Kärnan (kernel)** är Python-processen som kör din kod. Den kommer ihåg alla variabler du
skapat under sessionen. Om något beter sig konstigt — en variabel "hänger kvar" eller koden
tar aldrig slut:

- **Restart** (knappen med den runda pilen) startar om kärnan och glömmer allt. Kör sedan
  cellerna från början igen.
- **Interrupt** (stopp-knappen) avbryter en cell som fastnat i en oändlig loop.

**Rensa output före inlämning.** Ska du lämna in en notebook: kör **Edit → Clear Outputs of
All Cells** (JupyterLab), eller **Ctrl + Shift + P → Jupyter: Clear All Outputs** (VS Code),
och spara. Facit och kursmaterial checkas in utan output.

---

## Snabbreferens — tangentbord

Markera en cell (klicka i vänstermarginalen, cellen får blå kant) och tryck:

| Tangent | Gör |
|---|---|
| `Enter` | börja redigera cellen |
| `Esc` | sluta redigera |
| `A` / `B` | ny cell **A**bove / **B**elow |
| `D` `D` (två gånger) | ta bort cellen |
| `M` / `Y` | gör cellen till Markdown / Code |
| `Shift + Enter` | kör cellen |
| `Z` | ångra senaste cell-ändring |

---

## Vanliga fel

| Symptom | Vad du gör |
|---|---|
| **`jupyter: command not found` (Väg A)** | Du glömde `--with jupyter`. Kör hela raden: `uv run --with jupyter jupyter lab`. |
| **Webbläsaren öppnas inte / "This site can't be reached"** | Servern är inte igång, eller du stängde terminalen. Kör `uv run --with jupyter jupyter lab` igen och klistra in `http://localhost:8888/lab?token=…`-raden. |
| **`ModuleNotFoundError: No module named 'X'`** | Paketet saknas i miljön. Väg A: starta om med `--with X`. Väg B: `uv add X`, starta sedan om kärnan (Restart). |
| **Cellen får `[*]` och blir aldrig klar** | Koden kör fortfarande (eller har fastnat). Tryck Interrupt, annars Restart. |
| **Select Kernel visar ingen `.venv` (Väg B)** | Kör `uv add jupyter` i projektmappen, sedan `Developer: Reload Window` i VS Code. |
| **VS Code frågar om `ipykernel` gång på gång (Väg B)** | Säg ja och vänta tills installationen är klar; välj sedan kärnan igen. |
| **Allt är rött efter "Run All"** | Kör en cell i taget uppifrån i stället — vissa celler ska fela med flit. |

---

## Prova helt utan installation

Vill du bara känna på gränssnittet kör JupyterLab i webbläsaren utan att installera något:
<https://jupyter.org/try-jupyter/lab/>. Bra för att testa — men kursens övningar kör du
lokalt enligt Väg A eller B ovan.

## Mer information

- JupyterLab: <https://jupyterlab.readthedocs.io/en/stable/user/interface.html>
- Jupyter i VS Code: <https://code.visualstudio.com/docs/datascience/jupyter-notebooks>

Nästa steg: [60-hello-world.md](60-hello-world.md)
