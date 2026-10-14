# Verktyg och mjukvara i kursen

Det här är översikten över vad du installerar och varför. **Steg-för-steg-instruktioner**
finns i de numrerade dokumenten `20`–`60` — läs det här först så vet du vart det bär.

---

## Operativsystem

Kursmaterialet testas på:

- **Windows 11.** Allt är skrivet för Windows 11. Äldre versioner kan fungera men
  rekommenderas inte.
- **Linux: Ubuntu 22.04 LTS eller senare LTS** (24.04 är vanligast idag). Andra
  distributioner fungerar oftast men testas inte.
- **Mac:** de macOS-versioner som fortfarande får säkerhetsuppdateringar från Apple.

---

## Det du installerar före lektion 1

### uv — verktyget allt annat går genom

**`uv`** är en projekt- och pakethanterare för Python som dessutom kan installera Python
självt. I kursen använder vi uv för att installera Python, köra program och lägga till
tredjepartsmoduler.

En pakethanterare hanterar i första hand tredjepartsbibliotek — t.ex. `pytest`, ett verktyg
för att köra tester. Python har en inbyggd pakethanterare, `pip`, men den blir krånglig när
man jobbar med flera projekt samtidigt. Med uv kan olika projekt i olika mappar använda
olika Python-versioner och olika bibliotek utan att krocka.

→ `20-installera-windows.md` / `21-installera-linux-mac.md`

### Python 3.13 eller senare

Allt kursmaterial är skrivet för att fungera från och med **Python 3.13**. Nyare versioner
går bra. Du installerar inte Python själv — uv gör det åt dig.

→ `20-installera-windows.md` / `21-installera-linux-mac.md`

### Visual Studio Code

Kodeditorn vi använder, med extensionerna **Python** och **Jupyter**. Du får använda en
annan editor om du har en favorit, men instruktionerna utgår från VS Code.

→ `30-texteditor.md`

### Jupyter

Interaktiv Python-miljö där kod, text och grafer bor i samma dokument (filändelse
`.ipynb`). Används **löpande under kursen**: övningar, föreläsningsexempel och
kom-igång-guiden till inlämningsuppgiften är notebooks.

Du ska ha **JupyterLab** igång lokalt före lektion 1. Det startas med
`uv run --with jupyter jupyter lab` (samma kommando som kursens `just lab`), och samma
notebooks kan även öppnas via **Jupyter-extensionen i VS Code**. Att bara "prova" på
<https://jupyter.org/try-jupyter/lab/> räcker inte — kursens övningar körs lokalt.

→ `50-jupyter.md`

---

## Övriga verktyg

- **Marp** — läraren använder det för att skapa presentationsmaterialet. Du behöver **inte**
  installera det. <https://marp.app>
- **Git** — versionshantering. Installeras i `30-texteditor.md`; vi använder det på riktigt
  först i lektion 3.

---

Nästa steg: [20-installera-windows.md](20-installera-windows.md) eller [21-installera-linux-mac.md](21-installera-linux-mac.md)
