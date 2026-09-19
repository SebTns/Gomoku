[← Tillbaka till README](../README.md)

# Tester

Alla testfall i projektet, skrivna i **Given / When / Then** (BDT — Behaviour-Driven Testing).
Varje testfall pekar på de krav (FR/NFR/SR) det verifierar, och varje alternativt flöde i ett
användningsfall har minst ett eget testfall.

**Omfattning:** 41 testfiler, 254 testfall. 30 filer (181 testfall) är kopierade
från `docs/requirements/Acceptance-Criterias/`. 11 filer (73 testfall) är nyskrivna för de
användningsfall som tidigare saknade test.

---

## Så läses ett testfall

```
### AC-11-02: Spelaren avbryter uppgivandet     ← ID: AC-<use case>-<löpnummer>
**Relaterade krav:** FR-09.2, FR-09.6           ← vilka krav testet verifierar
**Given** att ett parti pågår                   ← förutsättningar (från UC:s förutsättningar)
**When** spelaren väljer "Cancel"               ← handlingen (från huvud-/alternativflödet)
**Then** ska uppgivandet inte genomföras        ← förväntat, observerbart resultat
**And** partiet ska fortsätta.                  ← ytterligare resultat som ska kontrolleras
```

Kedjan: **Aktör → Use Case → Krav → Testfall**. Kartan mellan use case-delar och testdelar
finns i [`08-use-cases-och-test-cases.md`](../docs/requirements/08-use-cases-och-test-cases.md).

| I användningsfallet | I testfallet |
|--------------------|--------------|
| Förutsättningar | **Given** |
| Huvudflöde | **When** + **Then** |
| Alternativa flöden | Negativa testfall, ett per AF |
| Postconditions | **Then** / **And** |
| Särskilda krav (NFR) | Mätbara **Then**-rader med gränsvärden |

---

## Översikt

| UC | Namn | Fil | Testfall | Antal | Status |
|----|------|-----|----------|-------|--------|
| UC-01 | Starta nytt parti | [AC-01-Starta-nytt-parti](AC-01-Starta-nytt-parti.md) | AC-01-01 – AC-01-05 | 5 | kopierad |
| UC-02 | Gör ett drag | [AC-02-1-Placera.en.sten.på.ledig.punkt](AC-02-1-Placera.en.sten.på.ledig.punkt.md) | AC-02-01 – AC-02-09 | 10 | kopierad |
| UC-03 | Bjuda in en vän | [AC-03-bjuda-in-en-van](AC-03-bjuda-in-en-van.md) | AC-03-01 – AC-03-06 | 6 | kopierad |
| UC-04 | Välja färg | [AC-04-valja-farg](AC-04-valja-farg.md) | AC-04-01 – AC-04-04 | 4 | kopierad |
| UC-05 | Spela mot datorn | [AC-05-Spela-mot-datorn](AC-05-Spela-mot-datorn.md) | AC-05-01 – AC-05-07 | 7 | kopierad |
| UC-06 | Starta spelet | [AC-06-Starta-spelet](AC-06-Starta-spelet.md) | AC-06-01 – AC-06-06 | 6 | kopierad |
| UC-07 | Välj ditt synliga spelarnamn | [AC-07-valj-ditt-synliga-spelar-namn](AC-07-valj-ditt-synliga-spelar-namn.md) | AC-07-01 – AC-07-05 | 5 | kopierad |
| UC-08 | Välj svårighetsgrad | [AC-08-valj-svarighetsgrad](AC-08-valj-svarighetsgrad.md) | AC-08-01 – AC-08-06 | 6 | kopierad |
| UC-09 | Motståndare gör drag | [AC-09-motstandare-gor-drag](AC-09-motstandare-gor-drag.md) | AC-09-01 – AC-09-06 | 6 | kopierad |
| UC-10 | Spela mot vän | [AC-10-spela-mot-van](AC-10-spela-mot-van.md) | AC-10-01 – AC-10-07 | 7 | kopierad |
| UC-11 | Ge upp | [AC-11-Ge-upp](AC-11-Ge-upp.md) | AC-11-01 – AC-11-03 | 3 | kopierad |
| UC-12 | Avsluta ett parti | [AC-12-Avsluta-ett-parti](AC-12-Avsluta-ett-parti.md) | AC-12-01 – AC-12-04 | 4 | kopierad |
| UC-13 | Starta ett nytt parti | [AC-13-Starta-ett-nytt-parti](AC-13-Starta-ett-nytt-parti.md) | AC-13-01 – AC-13-06 | 6 | kopierad |
| UC-14 | Oavgjort | [AC-14-Oavgjort](AC-14-Oavgjort.md) | AC-14-01 – AC-14-03 | 3 | kopierad |
| UC-15 | Förlust | [AC-15-forlust](AC-15-forlust.md) | AC-15-01 – AC-15-03 | 3 | kopierad |
| UC-16 | Vinst | [AC-16-Vin](AC-16-Vin.md) | AC-16-01 – AC-16-03 | 3 | kopierad |
| UC-17 | Spelhistorik | [AC-17-Spelhistorik](AC-17-Spelhistorik.md) | AC-17-01 – AC-17-06 | 6 | kopierad |
| UC-18 | Spela multiplayer lokalt | [AC-18-spela-multiplayer-lokalt](AC-18-spela-multiplayer-lokalt.md) | AC-18-01 – AC-18-07 | 7 | kopierad |
| UC-19 | Ångra ett drag | [AC-19-angra-ett-drag](AC-19-angra-ett-drag.md) | AC-19-01 – AC-19-07 | 7 | kopierad |
| UC-20 | Visa spelregler | [AC-20-visa-spelregler](AC-20-visa-spelregler.md) | AC-20-01 – AC-20-07 | 7 | kopierad |
| UC-21 | Skapa ett konto | [AC-21-skapa-ett-konto](AC-21-skapa-ett-konto.md) | AC-21-01 – AC-21-07 | 7 | kopierad |
| UC-22 | Logga in | [AC-22-logga-in](AC-22-logga-in.md) | AC-22-01 – AC-22-06 | 6 | kopierad |
| UC-23 | Radera ett konto | [AC-23-radera-ett-konto](AC-23-radera-ett-konto.md) | AC-23-01 – AC-23-07 | 7 | kopierad |
| UC-24 | Lägg till inloggningsmetod | [AC-24-lagg-till-inloggningsmetod](AC-24-lagg-till-inloggningsmetod.md) | AC-24-01 – AC-24-08 | 8 | kopierad |
| UC-25 | Välj inloggningsmetod | [AC-25-Inloggnings-Alternativ](AC-25-Inloggnings-Alternativ.md) | AC-25-01 – AC-25-05 | 5 | kopierad |
| UC-26 | Spara parti | [AC-26-Spara-parti](AC-26-Spara-parti.md) | AC-26-01 – AC-26-08 | 8 | **ny** |
| UC-27 | Starta sparat parti | [AC-27-Starta-sparat-parti](AC-27-Starta-sparat-parti.md) | AC-27-01 – AC-27-06 | 6 | **ny** |
| UC-28 | Rapportera ett tekniskt problem | [AC-28-Rapportera-ett-tekniskt-problem](AC-28-Rapportera-ett-tekniskt-problem.md) | AC-28-01 – AC-28-07 | 7 | kopierad |
| UC-29 | Tillfälligt blockera en spelare | [AC-29-Tillfalligt-blockera-en-spelare](AC-29-Tillfalligt-blockera-en-spelare.md) | AC-29-01 – AC-29-08 | 8 | kopierad |
| UC-30 | Ändra kontoinställningar | [AC-30-Andra-kontoinstallningar](AC-30-Andra-kontoinstallningar.md) | AC-30-01 – AC-30-06 | 6 | **ny** |
| UC-31 | Byta lösenord | [AC-31-Byta-losenord](AC-31-Byta-losenord.md) | AC-31-01 – AC-31-07 | 7 | **ny** |
| UC-32 | Återställ spelet | [AC-32-Aterstall-spelet](AC-32-Aterstall-spelet.md) | AC-32-01 – AC-32-06 | 6 | **ny** |
| UC-NFR-01 | Ge samtycke till cookie | [AC-NFR-01-Ge-samtycke-till-cookie](AC-NFR-01-Ge-samtycke-till-cookie.md) | AC-NFR-01-01 – AC-NFR-01-07 | 7 | **ny** |
| UC-NFR-02 | Begära tillgång till personuppgifter | [AC-NFR-02-Begara-tillgang-till-personuppgifter](AC-NFR-02-Begara-tillgang-till-personuppgifter.md) | AC-NFR-02-01 – AC-NFR-02-06 | 6 | **ny** |
| UC-NFR-03 | Informeras om delning med tredje part | [AC-NFR-03-Informeras-om-delning-med-tredje-part](AC-NFR-03-Informeras-om-delning-med-tredje-part.md) | AC-NFR-03-01 – AC-NFR-03-05 | 5 | **ny** |
| UC-NFR-04 | Begär radering av data | [AC-NFR-04-Begar-radering-av-data](AC-NFR-04-Begar-radering-av-data.md) | AC-NFR-04-01 – AC-NFR-04-09 | 9 | kopierad |
| UC-NFR-05 | Ta bort konto (GDPR-självbetjäning) | [AC-NFR-05-Ta-bort-konto](AC-NFR-05-Ta-bort-konto.md) | AC-NFR-05-01 – AC-NFR-05-06 | 6 | **ny** |
| UC-NFR-06 | Systemets responstid efter spelarens handling | [AC-NFR-06-Responstid](AC-NFR-06-Responstid.md) | AC-NFR-06-01 – AC-NFR-06-08 | 8 | **ny** |
| UC-NFR-07 | Spelaren får återkoppling efter handling | [AC-NFR-07-Aterkoppling](AC-NFR-07-Aterkoppling.md) | AC-NFR-07-01 – AC-NFR-07-08 | 8 | **ny** |
| UC-NFR-08 | Dataskyddsombudet granskar en raderingsbegäran | [AC-NFR-08-DPO-granskar-en-raderingsbegaran](AC-NFR-08-DPO-granskar-en-raderingsbegaran.md) | AC-NFR-08-01 – AC-NFR-08-05 | 5 | kopierad |
| NFR-13 | Språk i gränssnittet | [AC-NFR-13-sprak-i-granssnittet](AC-NFR-13-sprak-i-granssnittet.md) | AC-NFR-13-01 – AC-NFR-13-08 | 8 | kopierad |
| | **Totalt** | | | **254** | |

---

## Öppna frågor som testen har hittat

När de nya testen skrevs visade sig några användningsfall och krav säga olika saker. Testen
följer kraven tills gruppen har bestämt sig:

| Test | Motsägelse | Att besluta |
|------|-----------|-------------|
| AC-26-03 | UC-26 steg 2 säger "konto, moln eller fil". FR-26.4 säger "fil eller lokal lagring" för gäst. | Vilka sparplatser finns? |
| AC-26-06 | UC-26 AF-03 erbjuder att spara ett avslutat parti till historiken. FR-26.8 tillåter bara sparande av pågående parti. | Stryk AF-03 eller ändra FR-26.8. |
| AC-NFR-05-03, -04 | UC-NFR-05 kräver lösenord + e-postlänk (två steg). FR-15 / UC-23 kräver bara lösenord. | Ska e-poststeget in i FR-15? |
| AC-NFR-06 (alla) | NFR-02 anger gränsvärden men inte hur många mätningar som krävs. | Förslag: 95:e percentilen över 100 körningar. |

Dessutom står de fyra ofärdiga kriterierna i avsnitt 8.6 i `08-use-cases-och-test-cases.md`
kvar (AC-19-07, AC-21-07, AC-24-08 samt frågan i UC-NFR-08).

---

## Alla testfall per användningsfall

### UC-01 – Starta nytt parti

Fil: [AC-01-Starta-nytt-parti](AC-01-Starta-nytt-parti.md)

- **AC-01-01** Spelaren startar ett nytt parti
- **AC-01-02** Standardvärden i konfigurationsvyn
- **AC-01-03** Spelaren avbryter konfigurationen (UC-01 AF-01)
- **AC-01-04** Partiet kan inte skapas (UC-01 AF-02)
- **AC-01-05** Ett parti pågår redan (UC-01 AF-03)

### UC-02 – Gör ett drag

Fil: [AC-02-1-Placera.en.sten.på.ledig.punkt](AC-02-1-Placera.en.sten.på.ledig.punkt.md)

- **AC-02-01** Spelaren placerar en sten på en ledig punkt
- **AC-02-02** Turen lämnas över efter ett giltigt drag
- **AC-02-03** Punkten är upptagen (UC-02 AF-01)
- **AC-02-04** Drag utanför sin tur (UC-02 AF-02)
- **AC-02-05** Exakt fem i rad ger vinst (UC-02 AF-03)
- **AC-02-06** Sex eller fler i rad är inte en vinst (UC-02 AF-06)
- **AC-02-06b** Att fylla en lucka till exakt fem är en vinst
- **AC-02-07** Brädet blir fullt utan femma (UC-02 AF-04)
- **AC-02-08** Draget kan inte registreras (UC-02 AF-05)
- **AC-02-09** Draget går att göra med tangentbord

### UC-03 – Bjuda in en vän

Fil: [AC-03-bjuda-in-en-van](AC-03-bjuda-in-en-van.md)

- **AC-03-01** Bjuda in en vän och starta partiet
- **AC-03-02** Inbjudningslänken förfaller
- **AC-03-03** Ogiltig inbjudningslänk
- **AC-03-04** Inbjudaren avbryter inbjudan
- **AC-03-05** Ytterligare spelare försöker ansluta
- **AC-03-06** Två personer försöker använda samma inbjudan

### UC-04 – Välja färg

Fil: [AC-04-valja-farg](AC-04-valja-farg.md)

- **AC-04-01** Spelaren väljer färg före partistart
- **AC-04-02** Ingen färg väljs före partistart
- **AC-04-03** Färgval i ett parti mot en vän
- **AC-04-04** Spelaren försöker ändra färg efter partistart

### UC-05 – Spela mot datorn

Fil: [AC-05-Spela-mot-datorn](AC-05-Spela-mot-datorn.md)

- **AC-05-01** Starta ett parti mot datorn
- **AC-05-02** Datorn gör ett giltigt drag
- **AC-05-03** Kontrollera fem i rad efter spelarens drag
- **AC-05-04** Kontrollera fem i rad efter datorns drag
- **AC-05-05** Tekniskt fel när datorns drag beräknas
- **AC-05-06** Datorns drag överskrider tidsgränsen och nytt försök lyckas
- **AC-05-07** Det andra försöket att beräkna datorns drag misslyckas

### UC-06 – Starta spelet

Fil: [AC-06-Starta-spelet](AC-06-Starta-spelet.md)

- **AC-06-01** Applikationen öppnas
- **AC-06-02** Spelet är spelbart utan inloggning
- **AC-06-03** Applikationen kan inte laddas (UC-06 AF-01)
- **AC-06-04** Ett pågående parti kan återupptas (UC-06 AF-02)
- **AC-06-05** Startsidan nås från valfri vy
- **AC-06-06** Startsidan fungerar på liten skärm

### UC-07 – Välj ditt synliga spelarnamn

Fil: [AC-07-valj-ditt-synliga-spelar-namn](AC-07-valj-ditt-synliga-spelar-namn.md)

- **AC-07-01** Spelaren anger ett giltigt namn
- **AC-07-02** Namnet uppfyller inte reglerna
- **AC-07-03** Spelaren anger inget namn
- **AC-07-04** Spelaren avbryter namnändringen
- **AC-07-05** Namnet saneras och skyddas (NFR-krav)

### UC-08 – Välj svårighetsgrad

Fil: [AC-08-valj-svarighetsgrad](AC-08-valj-svarighetsgrad.md)

- **AC-08-01** Spelaren väljer svårighetsgrad
- **AC-08-02** Svårighetsgrad erbjuds bara mot datorn
- **AC-08-03** Svårighetsgraden är låst under partiet
- **AC-08-04** Senast valda grad föreslås nästa gång
- **AC-08-05** Vald grad kan inte tillämpas
- **AC-08-06** Graden påverkar datorns svarstid inte mer än tillåtet

### UC-09 – Motståndare gör drag

Fil: [AC-09-motstandare-gor-drag](AC-09-motstandare-gor-drag.md)

- **AC-09-01** Motståndaren gör ett giltigt drag
- **AC-09-02** Systemet visar att datorn beräknar
- **AC-09-03** Motståndaren väljer en upptagen punkt (UC-09 AF-01)
- **AC-09-04** Motståndarens drag uteblir (UC-09 AF-02)
- **AC-09-05** Datorn kan inte beräkna ett drag
- **AC-09-06** Motståndaren vinner

### UC-10 – Spela mot vän

Fil: [AC-10-spela-mot-van](AC-10-spela-mot-van.md)

- **AC-10-01** Partiet startar när båda har anslutit
- **AC-10-02** Ett drag syns hos motståndaren
- **AC-10-03** Vännen kopplas från (UC-10 AF-01)
- **AC-10-04** En tredje part försöker ansluta (UC-10 AF-02)
- **AC-10-05** Spelaren lämnar partiet i förtid (UC-10 AF-03)
- **AC-10-06** Inbjudningslänken är oförutsägbar
- **AC-10-07** Spelarnamn saneras hos motståndaren

### UC-11 – Ge upp

Fil: [AC-11-Ge-upp](AC-11-Ge-upp.md)

- **AC-11-01** Spelaren ger upp ett pågående parti
- **AC-11-02** Spelaren avbryter uppgivandet
- **AC-11-03** Spelaren försöker ge upp ett avslutat parti

### UC-12 – Avsluta ett parti

Fil: [AC-12-Avsluta-ett-parti](AC-12-Avsluta-ett-parti.md)

- **AC-12-01** Spelaren avslutar ett pågående parti
- **AC-12-02** Spelaren ångrar sig (UC-12 AF-01)
- **AC-12-03** Statusen kan inte sparas (UC-12 AF-02)
- **AC-12-04** Spelaren stänger webbläsaren (UC-12 AF-03)

### UC-13 – Starta ett nytt parti

Fil: [AC-13-Starta-ett-nytt-parti](AC-13-Starta-ett-nytt-parti.md)

- **AC-13-01** Starta ett nytt parti
- **AC-13-02** Avbryta konfigurationen
- **AC-13-03** Partiet kan inte startas
- **AC-13-04** Bekräftelse krävs när ett parti redan pågår
- **AC-13-05** Spelaren avbryter byte till nytt parti
- **AC-13-06** Spelaren bekräftar byte till nytt parti

### UC-14 – Oavgjort

Fil: [AC-14-Oavgjort](AC-14-Oavgjort.md)

- **AC-14-01** Partiet avslutas som oavgjort
- **AC-14-02** Sista draget ger fem i rad
- **AC-14-03** Inga fler drag efter oavgjort

### UC-15 – Förlust

Fil: [AC-15-forlust](AC-15-forlust.md)

- **AC-15-01** Motståndaren får fem i rad
- **AC-15-02** Motståndaren får inte fem i rad
- **AC-15-03** Inga fler drag efter förlust

### UC-16 – Vinst

Fil: [AC-16-Vin](AC-16-Vin.md)

- **AC-16-01** Spelaren får fem i rad
- **AC-16-02** Spelarens drag ger ingen vinst
- **AC-16-03** Inga fler drag efter vinst

### UC-17 – Spelhistorik

Fil: [AC-17-Spelhistorik](AC-17-Spelhistorik.md)

- **AC-17-01** Spelaren öppnar sin spelhistorik
- **AC-17-02** Historiken kan sorteras
- **AC-17-03** Ett tidigare parti kan öppnas
- **AC-17-04** Ingen historik finns (UC-17 AF-01)
- **AC-17-05** Historiken kan inte hämtas (UC-17 AF-02)
- **AC-17-06** Gästspelares partidata raderas efter 30 dagar

### UC-18 – Spela multiplayer lokalt

Fil: [AC-18-spela-multiplayer-lokalt](AC-18-spela-multiplayer-lokalt.md)

- **AC-18-01** Två spelare startar ett lokalt parti
- **AC-18-02** Turen växlar mellan spelarna på samma enhet
- **AC-18-03** Fel spelare försöker göra ett drag (UC-18 AF-02)
- **AC-18-04** Båda spelarna vill ha samma färg (UC-18 AF-01)
- **AC-18-05** Lokalt parti fungerar utan nätverk
- **AC-18-06** Lokalt parti avslutas med ett resultat
- **AC-18-07** Brädet är läsbart för båda spelarna

### UC-19 – Ångra ett drag

Fil: [AC-19-angra-ett-drag](AC-19-angra-ett-drag.md)

- **AC-19-01** Spelaren ångrar sitt senaste drag
- **AC-19-02** Det finns inget drag att ångra (UC-19 AF-01)
- **AC-19-03** Motståndaren har redan svarat
- **AC-19-04** Partiet är avslutat (UC-19 AF-03)
- **AC-19-05** Ångra i lokalt parti kräver bekräftelse
- **AC-19-06** Ångra är inte tillgängligt i online-parti mot vän
- **AC-19-07** Ångra flera drag i följd

### UC-20 – Visa spelregler

Fil: [AC-20-visa-spelregler](AC-20-visa-spelregler.md)

- **AC-20-01** Spelaren öppnar regelsammanfattningen
- **AC-20-02** Reglerna anger rätt vinstvillkor
- **AC-20-03** Spelaren återgår till vyn hen kom ifrån (UC-20 steg 5)
- **AC-20-04** Reglerna öppnas under ett pågående parti
- **AC-20-05** Spelaren startar ett parti från regelvyn (UC-20 AF-02)
- **AC-20-06** Reglerna kan inte laddas (UC-20 AF-01)
- **AC-20-07** En ny spelare klarar sig utan extern hjälp

### UC-21 – Skapa ett konto

Fil: [AC-21-skapa-ett-konto](AC-21-skapa-ett-konto.md)

- **AC-21-01** Spelaren skapar ett konto
- **AC-21-02** E-postadressen är redan registrerad (UC-21 AF-01)
- **AC-21-03** Uppgifterna uppfyller inte kraven (UC-21 AF-02)
- **AC-21-04** Spelaren avbryter registreringen (UC-21 AF-03)
- **AC-21-05** Lösenordet lagras aldrig i klartext
- **AC-21-06** Registreringen samlar inte in mer än nödvändigt
- **AC-21-07** E-postverifiering

### UC-22 – Logga in

Fil: [AC-22-logga-in](AC-22-logga-in.md)

- **AC-22-01** Spelaren loggar in
- **AC-22-02** Fel uppgifter avslöjar inte vilket fält som var fel (UC-22 AF-01)
- **AC-22-03** Kontot låses efter upprepade misslyckade försök (UC-22 AF-02)
- **AC-22-04** Ett blockerat konto kan inte logga in
- **AC-22-05** Tekniskt fel vid inloggning (UC-22 AF-03)
- **AC-22-06** Utloggat läge är fortfarande spelbart

### UC-23 – Radera ett konto

Fil: [AC-23-radera-ett-konto](AC-23-radera-ett-konto.md)

- **AC-23-01** Spelaren raderar sitt konto
- **AC-23-02** Varningen stämmer med vad som faktiskt händer
- **AC-23-03** Spelaren ångrar sig (UC-23 AF-01)
- **AC-23-04** Fel lösenord vid bekräftelsen (UC-23 AF-03)
- **AC-23-05** Raderingen misslyckas (UC-23 AF-02)
- **AC-23-06** Ett raderat konto kan inte logga in
- **AC-23-07** Motståndarens partihistorik påverkas inte

### UC-24 – Lägg till inloggningsmetod

Fil: [AC-24-lagg-till-inloggningsmetod](AC-24-lagg-till-inloggningsmetod.md)

- **AC-24-01** Spelaren kopplar en ny inloggningsmetod
- **AC-24-02** Lösenordet måste bekräftas innan metoden läggs till
- **AC-24-03** Metoden är redan kopplad till kontot (UC-24 AF-01)
- **AC-24-04** Metoden är kopplad till ett annat konto
- **AC-24-05** Leverantören nekar kopplingen (UC-24 AF-02)
- **AC-24-06** Spelaren avbryter hos leverantören (UC-24 AF-03)
- **AC-24-07** Leverantören får inte mer uppgifter än nödvändigt
- **AC-24-08** Ta bort en inloggningsmetod

### UC-25 – Välj inloggningsmetod

Fil: [AC-25-Inloggnings-Alternativ](AC-25-Inloggnings-Alternativ.md)

- **AC-25-01** Tillgängliga inloggningsmetoder visas
- **AC-25-02** Vald metod leder till rätt flöde
- **AC-25-03** Vald metod är otillgänglig (UC-25 AF-01)
- **AC-25-04** Listan avslöjar inte andra konton
- **AC-25-05** Tangentbordsnavigering

### UC-26 – Spara parti

Fil: [AC-26-Spara-parti](AC-26-Spara-parti.md)

- **AC-26-01** Inloggad spelare sparar ett pågående parti
- **AC-26-02** Hela partitillståndet sparas
- **AC-26-03** Gästspelare erbjuds fil eller lokal lagring (UC-26 AF-04)
- **AC-26-04** Ett tidigare sparat parti skrivs över (UC-26 AF-02)
- **AC-26-05** Sparandet misslyckas (UC-26 AF-01)
- **AC-26-06** Ett avslutat parti kan inte sparas (UC-26 AF-03)
- **AC-26-07** Tillståndet sparas automatiskt vid sidomladdning
- **AC-26-08** Tillståndet bevaras vid tillfälligt nätverksavbrott

### UC-27 – Starta sparat parti

Fil: [AC-27-Starta-sparat-parti](AC-27-Starta-sparat-parti.md)

- **AC-27-01** Listan över sparade partier visas
- **AC-27-02** Spelaren återupptar ett sparat parti
- **AC-27-03** Sparat parti importeras från fil
- **AC-27-04** Inga sparade partier finns (UC-27 AF-01)
- **AC-27-05** Det sparade partiet kan inte laddas (UC-27 AF-02)
- **AC-27-06** Motståndaren är inte ansluten (UC-27 AF-03)

### UC-28 – Rapportera ett tekniskt problem

Fil: [AC-28-Rapportera-ett-tekniskt-problem](AC-28-Rapportera-ett-tekniskt-problem.md)

- **AC-28-01** Rapportera ett tekniskt problem
- **AC-28-02** Beskrivning saknas (UC-28 AF-01)
- **AC-28-03** Problemrapporten kan inte registreras (UC-28 AF-02)
- **AC-28-04** Lokalt sparad rapport skickas om (UC-28 AF-04)
- **AC-28-05** Spelaren avbryter rapporteringen (UC-28 AF-03)
- **AC-28-06** Rapporteringen påverkar inte ett pågående parti
- **AC-28-07** Spelaren informeras om vilka uppgifter som bifogas

### UC-29 – Tillfälligt blockera en spelare

Fil: [AC-29-Tillfalligt-blockera-en-spelare](AC-29-Tillfalligt-blockera-en-spelare.md)

- **AC-29-01** Tillfälligt blockera en spelare
- **AC-29-02** Administratören avbryter blockeringen (UC-29 AF-01)
- **AC-29-03** Blockeringen kan inte genomföras (UC-29 AF-02)
- **AC-29-04** Blockeringen hävs automatiskt när tiden gått ut
- **AC-29-05** Spelaren informeras om blockeringen
- **AC-29-06** Blockering under pågående parti (UC-29 AF-03)
- **AC-29-07** Administratören häver blockeringen i förtid (UC-29 AF-04)
- **AC-29-08** Rapporter är hämtbara för administratören

### UC-30 – Ändra kontoinställningar

Fil: [AC-30-Andra-kontoinstallningar](AC-30-Andra-kontoinstallningar.md)

- **AC-30-01** Spelaren ändrar sitt synliga namn
- **AC-30-02** Nuvarande inställningar visas
- **AC-30-03** Ogiltigt värde avvisas (UC-30 AF-01)
- **AC-30-04** Skript i spelarnamnet körs inte
- **AC-30-05** Spelaren avbryter (UC-30 AF-02)
- **AC-30-06** Ändringen kan inte sparas (UC-30 AF-03)

### UC-31 – Byta lösenord

Fil: [AC-31-Byta-losenord](AC-31-Byta-losenord.md)

- **AC-31-01** Spelaren byter lösenord
- **AC-31-02** Det nya lösenordet gäller vid nästa inloggning
- **AC-31-03** Fel nuvarande lösenord (UC-31 AF-01)
- **AC-31-04** Det nya lösenordet uppfyller inte kraven (UC-31 AF-02)
- **AC-31-05** Upprepningen matchar inte (UC-31 AF-02)
- **AC-31-06** Spelaren avbryter (UC-31 AF-03)
- **AC-31-07** Lösenordet skickas krypterat och lagras som hash

### UC-32 – Återställ spelet

Fil: [AC-32-Aterstall-spelet](AC-32-Aterstall-spelet.md)

- **AC-32-01** Spelaren återställer ett pågående parti
- **AC-32-02** Konfigurationen behålls
- **AC-32-03** Bekräftelse krävs
- **AC-32-04** Spelaren ångrar sig (UC-32 AF-01)
- **AC-32-05** Parti mot vän kräver båda spelarnas samtycke
- **AC-32-06** Ett avslutat parti kan inte återställas (UC-32 AF-02)

### UC-NFR-01 – Ge samtycke till cookie

Fil: [AC-NFR-01-Ge-samtycke-till-cookie](AC-NFR-01-Ge-samtycke-till-cookie.md)

- **AC-NFR-01-01** Cookie-meddelandet visas vid första besöket
- **AC-NFR-01-02** Inga spårningsskript laddas före samtycke
- **AC-NFR-01-03** Gästanvändaren accepterar endast nödvändiga cookies
- **AC-NFR-01-04** Gästanvändaren accepterar alla cookies
- **AC-NFR-01-05** Meddelandet stängs utan val (UC-NFR-01 AF-01)
- **AC-NFR-01-06** Meddelandet visas inte igen
- **AC-NFR-01-07** Gästanvändaren ändrar eller återkallar sitt val (UC-NFR-01 AF-02)

### UC-NFR-02 – Begära tillgång till personuppgifter

Fil: [AC-NFR-02-Begara-tillgang-till-personuppgifter](AC-NFR-02-Begara-tillgang-till-personuppgifter.md)

- **AC-NFR-02-01** Spelaren begär tillgång till sina personuppgifter
- **AC-NFR-02-02** Overifierad begäran avvisas
- **AC-NFR-02-03** Exporten är fullständig och strukturerad
- **AC-NFR-02-04** Andra personers uppgifter lämnas inte ut
- **AC-NFR-02-05** Begäran besvaras inom 30 dagar
- **AC-NFR-02-06** Begäran kan inte behandlas (UC-NFR-02 AF-01)

### UC-NFR-03 – Informeras om delning med tredje part

Fil: [AC-NFR-03-Informeras-om-delning-med-tredje-part](AC-NFR-03-Informeras-om-delning-med-tredje-part.md)

- **AC-NFR-03-01** Tredje parter och deras behandling visas
- **AC-NFR-03-02** Överföring utanför EES och skyddsåtgärder visas
- **AC-NFR-03-03** Ingen internationell överföring sker (UC-NFR-03 AF-01)
- **AC-NFR-03-04** Inga personuppgifter delas (UC-NFR-03 AF-02)
- **AC-NFR-03-05** Informationen kräver ingen inloggning

### UC-NFR-04 – Begär radering av data

Fil: [AC-NFR-04-Begar-radering-av-data](AC-NFR-04-Begar-radering-av-data.md)

- **AC-NFR-04-01** Spelaren begär radering av sina personuppgifter
- **AC-NFR-04-02** Overifierad begäran avvisas (UC-NFR-04 AF-03)
- **AC-NFR-04-03** Personuppgifter är raderade efter genomförd radering
- **AC-NFR-04-04** Bevarad speldata går inte att koppla till spelaren
- **AC-NFR-04-05** Personuppgifter kan inte återskapas
- **AC-NFR-04-06** Bekräftelse på genomförd radering skickas
- **AC-NFR-04-07** Raderingen genomförs inom 30 dagar
- **AC-NFR-04-08** Radering kan inte slutföras i tid (UC-NFR-04 AF-01)
- **AC-NFR-04-09** Rättslig skyldighet hindrar fullständig radering (UC-NFR-04 AF-02)

### UC-NFR-05 – Ta bort konto (GDPR-självbetjäning)

Fil: [AC-NFR-05-Ta-bort-konto](AC-NFR-05-Ta-bort-konto.md)

- **AC-NFR-05-01** Raderingsvalet finns i kontoinställningarna
- **AC-NFR-05-02** Varning visas före första bekräftelsesteget
- **AC-NFR-05-03** Lösenordet utlöser ett bekräftelsemejl (steg 1 av 2)
- **AC-NFR-05-04** E-postlänken inaktiverar kontot (steg 2 av 2)
- **AC-NFR-05-05** Kontot går inte att nå efter e-postbekräftelsen
- **AC-NFR-05-06** Bekräftelse skickas när raderingen är klar

### UC-NFR-06 – Systemets responstid efter spelarens handling

Fil: [AC-NFR-06-Responstid](AC-NFR-06-Responstid.md)

- **AC-NFR-06-01** Startsidan laddas inom 2 sekunder
- **AC-NFR-06-02** Ett drag visas inom 100 ms
- **AC-NFR-06-03** Vinstkontrollen är klar inom 100 ms
- **AC-NFR-06-04** Ogiltigt drag avvisas inom 100 ms (UC-NFR-06 AF-01, AF-02)
- **AC-NFR-06-05** Datorns drag inom 3 sekunder (UC-NFR-06 AF-03)
- **AC-NFR-06-06** Inbjudningslänk inom 1 sekund
- **AC-NFR-06-07** Drag syns hos motståndaren inom 500 ms
- **AC-NFR-06-08** Byte av inställning inom 300 ms

### UC-NFR-07 – Spelaren får återkoppling efter handling

Fil: [AC-NFR-07-Aterkoppling](AC-NFR-07-Aterkoppling.md)

- **AC-NFR-07-01** Färg och startspelare visas vid partistart
- **AC-NFR-07-02** Placerad sten markeras och dragräknaren uppdateras
- **AC-NFR-07-03** Det syns att datorn tänker
- **AC-NFR-07-04** Den avgörande raden markeras
- **AC-NFR-07-05** Återkoppling på upptagen punkt (UC-NFR-07 AF-01)
- **AC-NFR-07-06** Återkoppling när det inte är spelarens tur (UC-NFR-07 AF-02)
- **AC-NFR-07-07** Felmeddelanden har en väg vidare (UC-NFR-07 AF-03)
- **AC-NFR-07-08** Återkopplingen bygger inte enbart på färg

### UC-NFR-08 – Dataskyddsombudet granskar en raderingsbegäran

Fil: [AC-NFR-08-DPO-granskar-en-raderingsbegaran](AC-NFR-08-DPO-granskar-en-raderingsbegaran.md)

- **AC-NFR-08-01** Eskalerade begäranden listas med kvarvarande tid
- **AC-NFR-08-02** Datakategoriernas status visas
- **AC-NFR-08-03** Beslutet registreras spårbart
- **AC-NFR-08-04** Varning fem dagar före fristen
- **AC-NFR-08-05** Passerad frist markeras som avvikelse

### NFR-13 – Språk i gränssnittet

Fil: [AC-NFR-13-sprak-i-granssnittet](AC-NFR-13-sprak-i-granssnittet.md)

- **AC-NFR-13-01** Gränssnittets texter är på engelska
- **AC-NFR-13-02** Standardvärden som visas är på engelska
- **AC-NFR-13-03** Felmeddelanden är på engelska
- **AC-NFR-13-04** Cookie-texterna är på engelska
- **AC-NFR-13-05** E-post från systemet är på engelska
- **AC-NFR-13-06** Dokumentets språk är deklarerat
- **AC-NFR-13-07** Inga svenska strängar i byggartefakten
- **AC-NFR-13-08** Formatering beror inte på webbläsarens språk
