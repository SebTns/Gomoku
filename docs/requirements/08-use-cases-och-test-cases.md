[← Tillbaka till README](../../README.md)

# 8. Use Cases och Test Cases

Den här filen är kartan mellan användningsfall, krav och testfall. Den innehåller inga nya krav —
allt som står här finns någon annanstans, och syftet är att göra kopplingen synlig.

Testspråket är **Given / When / Then** genomgående. Valet är gjort för att formen tvingar fram ett
observerbart utfall: ett kriterium som inte går att avsluta med ett *Then* beskriver inte ett
testbart krav, och då är det inte ett krav.

---

## 8.1 Kedjan

```
Aktör  →  Use Case  →  Krav (FR/NFR)  →  Acceptanskriterium  →  Testfall
```

Varje led svarar på en egen fråga:

| Led | Frågan det besvarar | Var det står |
|-----|--------------------|--------------|
| Aktör | Vem förväntar sig ett resultat? | `01-inledning.md` 1.4, `07` 7.1 |
| Use Case | Vad vill aktören uppnå? | `use-cases/` |
| Krav | Vad ska systemet göra för att det ska ske? | `02`, `03`, `04` |
| Acceptanskriterium | Hur ser man skillnaden mellan rätt och fel? | `Acceptance-Criterias/` |
| Testfall | Hur körs kontrollen? | `tests/` — sammanfattning i [`tests/tester.md`](../../tests/tester.md) |

## 8.2 Hur use case-delarna översätts till testdelar

Kartan mellan de två formaten:

| I användningsfallet | I testfallet |
|--------------------|--------------|
| Förutsättningar | **Given** — testets förutsättningar |
| Huvudflöde | **When** + **Then** — förväntat beteende |
| Alternativa flöden | Negativa testfall, ett per AF |
| Postconditions | **Then** — assertions |
| Särskilda krav (NFR) | Mätbara **Then**-rader med gränsvärden |

Ett alternativflöde utan eget kriterium är en lucka: avvikelsen är beskriven men aldrig
kontrollerad.

---

## 8.3 Täckning per användningsfall

40 användningsfall, samtliga med acceptanskriterier. 41 testfiler och 254 testfall i `tests/`
(inklusive AC-NFR-13, som gäller systemet som helhet).

| UC-ID | Namn | Primär aktör | Acceptanskriterier | Antal |
|-------|------|--------------|--------------------|-------|
| UC-01 | Starta nytt parti | Spelare | AC-01-01 – AC-01-05 | 5 |
| UC-02 | Gör ett drag | Spelare | AC-02-01 – AC-02-09 (+ AC-02-06b) | 10 |
| UC-03 | Bjud in en vän | Spelare (inbjudare) | AC-03-01 – AC-03-06 | 6 |
| UC-04 | Välja färg | Spelare | AC-04-01 – AC-04-04 | 4 |
| UC-05 | Spela mot datorn | Spelare | AC-05-01 – AC-05-07 | 7 |
| UC-06 | Starta spelet | Spelare | AC-06-01 – AC-06-06 | 6 |
| UC-07 | Välj ditt synliga spelarnamn | Spelare | AC-07-01 – AC-07-05 | 5 |
| UC-08 | Välj svårighetsgrad | Spelare | AC-08-01 – AC-08-06 | 6 |
| UC-09 | Motståndare gör drag | Motståndaren (datorn eller online-motståndaren) | AC-09-01 – AC-09-06 | 6 |
| UC-10 | Spela mot vän | Spelare | AC-10-01 – AC-10-07 | 7 |
| UC-11 | Ge upp | Spelare | AC-11-01 – AC-11-03 | 3 |
| UC-12 | Avsluta ett parti | Spelare | AC-12-01 – AC-12-04 | 4 |
| UC-13 | Starta ett nytt parti | Spelare | AC-13-01 – AC-13-06 | 6 |
| UC-14 | Oavgjort | Spelare, Motståndare | AC-14-01 – AC-14-03 | 3 |
| UC-15 | Förlust | Spelare | AC-15-01 – AC-15-03 | 3 |
| UC-16 | Vinst | Spelare | AC-16-01 – AC-16-03 | 3 |
| UC-17 | Spelhistorik | Spelare | AC-17-01 – AC-17-06 | 6 |
| UC-18 | Spela multiplayer lokalt | Spelare | AC-18-01 – AC-18-07 | 7 |
| UC-19 | Ångra ett drag | Spelare | AC-19-01 – AC-19-07 | 7 |
| UC-20 | Visa spelregler | Spelare | AC-20-01 – AC-20-07 | 7 |
| UC-21 | Skapa ett konto | Spelare | AC-21-01 – AC-21-07 | 7 |
| UC-22 | Logga in | Spelare | AC-22-01 – AC-22-06 | 6 |
| UC-23 | Radera ett konto | Spelare | AC-23-01 – AC-23-07 | 7 |
| UC-24 | Lägg till inloggningsmetod | Spelare | AC-24-01 – AC-24-08 | 8 |
| UC-25 | Välj inloggningsmetod | Spelare | AC-25-01 – AC-25-05 | 5 |
| UC-26 | Spara parti | Spelare | AC-26-01 – AC-26-08 | 8 |
| UC-27 | Starta sparat parti | Spelare | AC-27-01 – AC-27-06 | 6 |
| UC-28 | Rapportera ett tekniskt problem | Spelare | AC-28-01 – AC-28-07 | 7 |
| UC-29 | Tillfälligt blockera en spelare | Administratör | AC-29-01 – AC-29-08 | 8 |
| UC-30 | Ändra kontoinställningar | Spelare | AC-30-01 – AC-30-06 | 6 |
| UC-31 | Byta lösenord | Spelare | AC-31-01 – AC-31-07 | 7 |
| UC-32 | Återställ spelet | Spelare | AC-32-01 – AC-32-06 | 6 |
| UC-NFR-01 | Ge samtycke till cookie | Gästanvändare | AC-NFR-01-01 – AC-NFR-01-07 | 7 |
| UC-NFR-02 | Begära tillgång till personuppgifter | Registrerad spelare | AC-NFR-02-01 – AC-NFR-02-06 | 6 |
| UC-NFR-03 | Informeras om delning med tredje part | Spelare | AC-NFR-03-01 – AC-NFR-03-05 | 5 |
| UC-NFR-04 | Begär radering av data (rätt till radering) | Registrerad spelare | AC-NFR-04-01 – AC-NFR-04-09 | 9 |
| UC-NFR-05 | Ta bort konto | Registrerad spelare | AC-NFR-05-01 – AC-NFR-05-06 | 6 |
| UC-NFR-06 | Systemets responstid efter spelarens handling | Spelare | AC-NFR-06-01 – AC-NFR-06-08 | 8 |
| UC-NFR-07 | Spelaren får återkoppling efter handling | Spelare | AC-NFR-07-01 – AC-NFR-07-08 | 8 |
| UC-NFR-08 | Dataskyddsombudet granskar en raderingsbegäran | Dataskyddsombud (DPO) | AC-NFR-08-01 – AC-NFR-08-05 | 5 |

---

## 8.4 Var täckningen saknades

Fram till v.37 hade elva användningsfall krav men inga acceptanskriterier: UC-26, UC-27, UC-30,
UC-31, UC-32 och UC-NFR-01, -02, -03, -05, -06, -07. Kraven var skrivna men aldrig översatta till
något observerbart. De har nu fått testfall i `tests/`.

Arbetet visade fyra ställen där use case och krav säger olika saker (sparplatser i UC-26,
avslutat parti i UC-26 AF-03, e-poststeget i UC-NFR-05 och antal mätningar för NFR-02). De står
listade i [`tests/tester.md`](../../tests/tester.md) under *Öppna frågor*. Det är just den sortens
lucka som bara syns när någon försöker skriva ett *Then*.

## 8.5 Krav som inte går att verifiera fullt ut

Tre kategorier återkommer i acceptanskriterierna och är värda att samla på ett ställe.

**Negativa påståenden.** NFR-12.4 säger att raderade personuppgifter inte ska kunna återskapas.
Ett test kan visa att uppgifterna *går* att återskapa från en viss sökväg — aldrig att det är
omöjligt från varje tänkbar. AC-NFR-04-05 räknar därför upp fem namngivna sökvägar i stället för
att gömma frågan bakom ordet "inte kan". Samma sak gäller NFR-07.6 i AC-21-05 och NFR-07.2 i
AC-10-06.

**Tidsskalor bortom en testsvit.** NFR-05.2 kräver 12 månaders lagring, NFR-12.2 och SR-03.2
30 dagar. Ingen pipeline väntar ut dem. NFR-05.7 och NFR-12.7 finns just därför: de kräver att
tillståndet går att avläsa med simulerad tid. Det verifierar logiken, inte att produktionsjobbet
faktiskt kör i tid — och den skillnaden är medveten.

**Krav om människor.** NFR-06.6 säger att en ny spelare ska klara ett parti inom 2 minuter utan
hjälp. Det är testbart, men bara genom observerad användbarhetstest med personer som inte sett
systemet. Ett krav som aldrig körs i CI kontrolleras i praktiken en gång och glöms sedan.

**Krav som gäller tvärs över allt.** NFR-13 (språk) hör inte till något enskilt användningsfall.
Det är inte otestbart, men det syns inte i täckningstabellen ovan, eftersom den är sorterad på
use case. AC-NFR-13 är därför skrivet mot systemet som helhet. Samma sak gäller NFR-01
(kompatibilitet) och NFR-06 (tillgänglighet), som i dag saknar egna acceptanskriterier.

## 8.6 Kriterier som medvetet står ofärdiga

Fyra acceptanskriterier saknar kravreferens och väntar på ett gruppbeslut. De står kvar i sina
filer för att luckan ska synas i täckningen i stället för att försvinna.

| Kriterium | Frågan som måste besvaras |
|-----------|---------------------------|
| AC-19-07 | Ska flera drag kunna ångras i följd? |
| AC-21-07 | Ska e-postadressen verifieras innan kontot aktiveras? Beslutet avgör om FR-30.2 fungerar. |
| AC-24-08 | Ska en inloggningsmetod kunna tas bort, och måste minst en finnas kvar? |
| UC-NFR-08 | Ska dataskyddsombudet se personuppgifterna eller bara datakategorierna? |

---

## 8.7 Diagram

Aktivitetsdiagram för testaktiviteterna ligger i `../diagrams/uml/`:

| Diagram | Realiserar |
|---------|-----------|
| `UC-02-aktivitetsdiagram-gor-ett-drag.md` | UC-02 med samtliga sex alternativflöden |
| `UC-02-sekvensdiagram-gor-ett-drag.md` | UC-02 och UC-09, med tidskraven på pilarna |
| `Tillstandsdiagram-partiets-livscykel.md` | Partiets status genom UC-01, UC-11, UC-12, UC-14 – UC-16 |
| `Tillstandsdiagram-turordning.md` | Turordningen, med avvisade drag som självövergångar |
| `Bjuda_in_en_van.md` | UC-03 |
