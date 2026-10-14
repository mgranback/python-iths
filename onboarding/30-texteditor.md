# Texteditor — Visual Studio Code

För att skriva kod behöver du en **kodeditor**. I kursen använder vi **Visual Studio Code**
(VS Code) — gratis, mycket vanligt, och med bra stöd för Python och Jupyter. Du får använda
en annan editor om du redan har en favorit (se sist i dokumentet), men allt kursmaterial och
alla instruktioner utgår från VS Code.

En kodeditor hjälper dig medan du skriver:

- **Syntaxfärgning** — nyckelord, text och funktioner får olika färg.
- **Feldetektering** — felstavade nyckelord och trasig syntax markeras direkt.
- **Komplettering** — förslag medan du skriver.
- **Inbyggt stöd för git**, för att köra tester, och för att köra kod rad för rad (felsökning).

---

## Förkrav

`20-installera-windows.md` **eller** `21-installera-linux-mac.md` — `uv` och Python
installerade.

De grafiska stegen nedan är likadana på Windows, Linux och Mac. Terminalkommandon som
skiljer sig står uppdelade.

---

## 1. Installera Visual Studio Code

Ladda ner från <https://code.visualstudio.com> — knappen känner av ditt operativsystem.

- **Windows:** kör installationsprogrammet. Låt rutan **"Add to PATH"** vara ikryssad (den
  är det som standard). Starta om datorn om installationen ber om det.
- **Mac:** öppna den nedladdade filen och dra **Visual Studio Code** till **Applications**.
- **Linux (Ubuntu):** ladda ner `.deb`-paketet och installera det:

  ```sh
  sudo apt install ./code_*.deb
  ```

  (eller `sudo snap install --classic code`).

Starta VS Code och låt det stå öppet — nästa steg görs inne i programmet.

---

## 2. Installera Git

VS Code använder **Git** för versionshantering (mer om det i lektion 3). Installera det nu:

- **Windows:** ladda ner och kör installationsprogrammet från
  <https://git-scm.com/download/win>. Klicka igenom med förvalda inställningar.
- **Linux (Ubuntu):**

  ```sh
  sudo apt install git
  ```

- **Mac:**

  ```sh
  xcode-select --install
  ```

  (eller ladda ner från <https://git-scm.com>).

---

## 3. Installera extensioner i VS Code

Extensioner lägger till stöd för olika språk och verktyg.

1. Klicka på **Extensions**-ikonen i vänsterkanten (fyra rutor), eller tryck
   **Ctrl + Shift + X** (Mac: **Cmd + Shift + X**).
2. Sök upp och installera, en i taget:
   - **Python** (utgiven av Microsoft)
   - **Jupyter** (utgiven av Microsoft)

**Pylance** (kodanalys) och **Python Debugger** följer med **Python**-extensionen
automatiskt — du behöver inte installera dem separat, men det skadar inte att söka upp dem
och kontrollera att de står som installerade.

---

## 4. Stäng av AI-komplettering till att börja med

När VS Code startas första gången vill det gärna slå på AI-förslag (**Copilot**) som skriver
kod åt dig medan du knappar. Som nybörjare blir det förvirrande — du behöver känna vad du
klarar själv och inte.

- **Logga inte in på Copilot** när VS Code frågar (du kan göra det senare).
- Har förslagen ändå dykt upp: öppna inställningarna med **Ctrl + ,**, sök på
  `inline suggest`, och stäng av **Editor: Inline Suggest: Enabled**.

Vi återkommer till AI-verktyg senare i kursen (`ai-verktyg.md` och lektion 1) och tittar då
på hur man använder dem med omdöme.

---

## Verifiera

Öppna en terminal i VS Code (**Terminal → New Terminal**) och kör:

```sh
code --version
git --version
```

Båda ska skriva ut ett versionsnummer. Gör `code` inte det på Windows: starta om VS Code
(och vid behov datorn) så att PATH läses om.

I **Extensions**-panelen ska **Python** och **Jupyter** ligga under "Installed".

---

## Vanliga fel

| Symptom | Vad du gör |
|---|---|
| **`code: command not found` / okänt kommando** | "Add to PATH" missades vid installationen. Windows: installera om. Mac: i VS Code, `Ctrl + Shift + P → Shell Command: Install 'code' command in PATH`. |
| **`git: command not found`** | Git är inte installerat — gör steg 2. Starta om terminalen efteråt. |
| **Extensionerna syns inte efter installation** | Ladda om fönstret: `Ctrl + Shift + P → Developer: Reload Window`. |
| **Copilot föreslår kod fast du inte vill** | Steg 4 — stäng av `Editor: Inline Suggest: Enabled` och logga ut ur Copilot. |

Windows begränsar som standard sökvägar till 260 tecken, vilket ibland stör Python. Hur du
slår på stöd för långa sökvägar står i `20-installera-windows.md`.

---

## Andra editorer

Inget hindrar dig från att använda en annan editor, men du får själv lösa Python- och
Jupyter-stödet — kursens instruktioner täcker bara VS Code.

- [Sublime Text](https://www.sublimetext.com/)
- [JetBrains PyCharm](https://www.jetbrains.com/pycharm/)
- [Zed](https://zed.dev)
- Terminalbaserade: [Neovim](https://neovim.io/), [Emacs](https://www.gnu.org/software/emacs/),
  [Helix](https://helix-editor.com/) — kräver mer konfiguration för Python.

---

Nästa steg: [40-uv-och-vscode.md](40-uv-och-vscode.md)
