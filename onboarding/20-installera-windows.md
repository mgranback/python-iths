# Installera uv och Python — Windows

Kursen stödjer **Windows 11**. Äldre Windows-versioner testas inte och kan strula.

Du installerar **uv** — kursens verktyg för Python-versioner, miljöer och paket (se
`10-verktyg.md`) — och låter sedan uv installera **Python** åt dig. Inget av det kräver
administratörsrättigheter; allt hamnar i din användarmapp.

---

## 1. Öppna PowerShell

Tryck på **Start**, skriv `PowerShell`, tryck **Enter**. Ett blått/svart terminalfönster
öppnas. Du behöver **inte** "Kör som administratör".

Alla kommandon nedan skrivs (eller klistras) in i det här fönstret, ett i taget, följt av
**Enter**.

---

## 2. Installera uv

Klistra in hela raden och tryck Enter:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Raden hämtar uv:s officiella installationsskript och kör det. Det laddar ner uv, lägger det
i `%USERPROFILE%\.local\bin` och lägger till den mappen i din PATH. Det tar någon minut.

Officiell sida med alternativ: <https://docs.astral.sh/uv/getting-started/installation/>

---

## 3. Starta om PowerShell och verifiera

**Stäng PowerShell-fönstret och öppna ett nytt** (PATH-ändringen slår igenom först då).
Kör sedan:

```powershell
uv self version
```

Skrivs en rad som `uv 0.12.x (… windows-msvc)` ut har det lyckats (versionsnumret är ett
annat när du läser det här). Får du i stället "not recognized" — se **Vanliga fel** nedan.

---

## 4. Installera Python

```powershell
uv python install 3.13
```

Kursmaterialet kräver **Python 3.13 eller senare**. Kontrollera:

```powershell
uv python list
```

En rad med `cpython-3.13...` ska stå med i listan. Du kan ha flera Python-versioner
installerade samtidigt — uv håller reda på vilken varje projekt använder.

Du behöver **inte** köra `python` direkt någonstans i kursen — det sköts via `uv run` (mer
i `40-uv-och-vscode.md`).

---

## 5. Slå på stöd för långa sökvägar (rekommenderas)

Windows begränsar som standard sökvägar till 260 tecken, vilket ibland stör Python och uv.
Öppna PowerShell **som administratör** (högerklicka på Start → **Terminal (Admin)**) och kör:

```powershell
New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1 -PropertyType DWORD -Force
```

Starta om datorn efteråt. Microsofts dokumentation:
<https://learn.microsoft.com/en-us/windows/win32/fileio/maximum-file-path-limitation>

---

## Vanliga fel

| Symptom | Vad du gör |
|---|---|
| **`uv : The term 'uv' is not recognized`** efter omstart | PATH har inte uppdaterats. Öppna ett helt nytt PowerShell-fönster. Kvarstår det: lägg till `%USERPROFILE%\.local\bin` i PATH via **System properties → Environment Variables → Path → New**, logga ut och in. |
| **`running scripts is disabled on this system`** | Kör installationsraden exakt som i steg 2 — den innehåller `-ExecutionPolicy ByPass` just för detta. |
| **Nedladdningen hänger eller ger SSL-fel** (t.ex. på skolnätet) | Prova ett annat nät (mobil hotspot). Bakom proxy: sätt `$env:HTTPS_PROXY` innan du kör raden. |
| **`uv python install` misslyckas med nätverksfel** | Samma som ovan — kör om på ett öppnare nät. |
| **Antivirus blockerar `uv.exe`** | Tillåt filen i `%USERPROFILE%\.local\bin` i antivirusprogrammet, installera om. |

---

Nästa steg: [30-texteditor.md](onboarding/30-texteditor.md)
