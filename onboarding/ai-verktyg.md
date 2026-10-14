# AI-verktyg i kursen

Kursplanen 2026 har **användning av relevanta AI-verktyg med fokus på kritiskt tänkande**
som ett eget utbildningsmoment. Med AI-verktyg menar vi chattbotar (ChatGPT, Claude,
Gemini …) och kodassistenter i editorn (GitHub Copilot m.fl.).

Det här dokumentet är kursens hållning. Läs det före lektion 1 — vi bygger vidare på det
under kursens gång.

---

## Kort version

- **Du får använda AI-verktyg.** Det hör till yrket idag.
- **Du ansvarar för all kod du lämnar in** — även det en AI föreslagit. Kan du inte förklara
  vad en rad gör, ska den inte vara med.
- **Stäng av AI-komplettering i editorn nu i början** (se sista avsnittet). Slå på den igen
  när du står stadigare.
- **På veckoprov och tentor är AI-verktyg inte tillåtna** om inget annat sägs.

---

## Vad AI-verktyg är bra på

Med rimliga, avgränsade frågor är de till stor hjälp:

- **Förklara ett felmeddelande.** Klistra in felet och de raderna det pekar på, fråga vad
  det betyder.
- **Förklara kod du inte förstår** — en rad, en funktion, ett begrepp.
- **Slå upp syntax:** "hur läser jag rad för rad ur en textfil i Python 3.13?"
- **Skriva rutinkod du redan kan** — t.ex. en testfunktion till en funktion du skrivit själv.
- **Bolla upplägg:** "jag ska räkna förekomster av varje IP i en loggfil — vilka sätt finns?"
- **Föreslå namn, struktur och kommentarer.**

---

## Vad du ska vara vaksam på

- **Självsäkert fel.** Ett AI-verktyg låter lika övertygande när det har fel. Kör koden. Läs
  dokumentationen. Kontrollera.
- **Föråldrat.** Förslag drar ofta åt gammal stil: Python 2, `%`-formatering i stället för
  f-strängar, `os.path` i stället för `pathlib`, moduler som inte finns kvar.
- **För mycket kod.** Verktyget löser gärna hela uppgiften på en gång. Då lär du dig inget,
  och du sitter med kod du inte kan felsöka.
- **Påhittade API:er.** Funktioner och parametrar som låter rimliga men inte existerar.
- **Säkerhet och sekretess.** Klistra **aldrig** in riktiga loggar, nycklar, lösenord,
  personuppgifter eller kunddata i ett AI-verktyg. Hitta på exempeldata i stället.

---

## Ett exempel

> **Du:** "Hur kollar jag om en fil finns i Python?"
>
> **AI:** "Använd `os.path.isfile(path)` — eller den nyare `os.exists(path)`."

`os.path.isfile` finns och fungerar. `os.exists` finns **inte** (det heter
`os.path.exists`, och `pathlib` har `Path(path).exists()`). Kör du bara vidare får du
`AttributeError: module 'os' has no attribute 'exists'` — och sitter med ett fel du inte
förstår för att koden inte var din.

Rätt reaktion: testa i en REPL (`uv run python`), eller slå upp `os` respektive `pathlib` i
[Pythons dokumentation](https://docs.python.org/3/).

---

## Så använder du AI-verktyg och lär dig något

1. **Försök själv först.** Skriv åtminstone ett utkast, eller skriv ner exakt var du fastnat.
2. **Fråga smått.** Be om en förklaring eller ett tips — inte hela lösningen.
3. **Skriv av för hand, förstå, kör.** Kopiera inte rakt in. Skriv koden själv rad för rad
   och kör den. Oklart? Fråga vidare tills du fattar.
4. **Verifiera mot en källa.** Pythons dokumentation, `help(...)` i REPL, eller att koden
   bevisligen gör rätt på din indata.
5. **Reflektera.** Vad lärde du dig? Vad gör du annorlunda nästa gång?

---

## Checklista innan ett AI-svar går in i din kod

- [ ] Jag kan förklara varje rad med egna ord.
- [ ] Jag har kört koden och sett att den gör rätt — även på ett kantfall.
- [ ] Inga påhittade funktioner: det jag använder finns i dokumentationen.
- [ ] Stilen matchar kursen (f-strängar, `pathlib`, Python 3.13+).
- [ ] Jag har inte klistrat in känslig data för att få fram svaret.

Kan du inte bocka alla rutorna — använd inte koden ännu.

---

## Bra fråga kontra dålig fråga

| Mindre bra | Bättre |
|---|---|
| "Lös uppgift 2 åt mig." | "Vad betyder felet `KeyError: 'time'` på rad 12?" |
| "Skriv en loggparser i Python." | "Jag har en lista med rader. Hur delar jag varje rad på första kolon-tecknet?" |
| "Varför funkar inte min kod?" (utan kod) | "Här är funktionen och felet jag får. Vad är fel?" |

---

## På veckoprov och tentor

AI-verktyg (chattbotar, kodassistenter, AI-komplettering) är **inte tillåtna** under
examinerande prov om inget annat uttryckligen sägs. Se `../prov/instruktioner.md`.

---

## I inlämningsuppgiften

Du får använda AI-verktyg, men:

- Koden ska vara din — du ska kunna förklara varje del vid en muntlig avstämning.
- Skriv en mening i din README (eller överst i filen) om AI-verktyg använts och till vad.
- Lösningar som uppenbart är AI-genererade och som du inte kan förklara godkänns inte.

---

## Stäng av AI-komplettering nu i början

Kodassistenter som föreslår hela rader medan du skriver gör att du missar att lära dig
grunderna. Stäng av det tills vidare:

- **Logga inte in på Copilot** när VS Code frågar.
- Har förslagen redan dykt upp: **Ctrl + ,** → sök `inline suggest` → stäng av
  **Editor: Inline Suggest: Enabled**.

Detaljer i `30-texteditor.md`, steg 4.

---

## Vi återkommer

Ämnet tas upp igen i lektion 1 och i kursavslutningen — bl.a. hur du bedömer ett AI-svar
och hur du använder verktygen i ett riktigt utvecklingsarbete.
