# Installera uv och Python — Linux och Mac

- **Linux:** kursen stödjer **Ubuntu 22.04 LTS eller senare LTS** (24.04 är vanligast idag).
  Andra distributioner fungerar oftast men testas inte.
- **Mac:** de macOS-versioner som fortfarande får säkerhetsuppdateringar från Apple.

Du installerar **uv** — kursens verktyg för Python-versioner, miljöer och paket (se
`10-verktyg.md`) — och låter sedan uv installera **Python** åt dig. Inget av det kräver
`sudo`; allt hamnar i din hemkatalog under `~/.local`.

---

## 1. Öppna en terminal

- **Ubuntu:** tryck **Ctrl + Alt + T**, eller sök efter "Terminal" i aktivitetsöversikten.
- **Mac:** tryck **Cmd + Blanksteg**, skriv `Terminal`, tryck **Enter**.

Alla kommandon nedan skrivs in i terminalen, ett i taget, följt av **Enter**.

---

## 2. Installera uv

```sh
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Raden hämtar uv:s officiella installationsskript och kör det: uv laddas ner till
`~/.local/bin` och en rad som lägger till mappen i PATH skrivs in i din `~/.bashrc` /
`~/.zshrc`.

Saknas `curl` (kan hända på en avskalad Ubuntu eller i WSL), installera det först med
`sudo apt install curl` — eller använd `wget`:

```sh
wget -qO- https://astral.sh/uv/install.sh | sh
```

Officiell sida med alternativ: <https://docs.astral.sh/uv/getting-started/installation/>

---

## 3. Ladda om PATH och verifiera

Öppna ett **nytt terminalfönster** (eller kör `source ~/.bashrc` respektive
`source ~/.zshrc`). Kör sedan:

```sh
uv self version
```

Skrivs en rad som `uv 0.12.x (… linux-gnu)` eller `(… apple-darwin)` ut har det lyckats
(versionsnumret är ett annat när du läser det här). Får du `command not found` — se
**Vanliga fel** nedan.

---

## 4. Installera Python

```sh
uv python install 3.13
```

Kursmaterialet kräver **Python 3.13 eller senare**. Kontrollera:

```sh
uv python list
```

En rad med `cpython-3.13...` ska stå med i listan. Du kan ha flera Python-versioner
installerade samtidigt — uv håller reda på vilken varje projekt använder.

Rör **inte** systemets egen `python3` — i kursen kör du allt via `uv run` (mer i
`40-uv-och-vscode.md`).

---

## Vanliga fel

| Symptom | Vad du gör |
|---|---|
| **`uv: command not found`** i ett nytt fönster | PATH-raden hamnade i fel fil. Kör `echo $SHELL` — står det `zsh`, lägg till `export PATH="$HOME/.local/bin:$PATH"` i `~/.zshrc`; för `bash` i `~/.bashrc`. Öppna nytt fönster. |
| **`curl: command not found`** | `sudo apt install curl`, eller använd `wget`-raden i steg 2. |
| **Installationsskriptet klagar på saknad `unzip`/`tar`** | `sudo apt install unzip tar`, kör om steg 2. |
| **`uv python install` ger nätverksfel** | Prova ett öppnare nät. Bakom proxy: `export HTTPS_PROXY=...` innan du kör kommandot. |
| **Mac: "cannot be opened because the developer cannot be verified"** | Gäller sällan CLI-verktyg. Uppstår det: **System Settings → Privacy & Security → Open Anyway**. |

---

Nästa steg: [30-texteditor.md](30-texteditor.md)
