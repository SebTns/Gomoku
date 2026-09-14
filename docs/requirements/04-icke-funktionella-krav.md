# 4. Icke-funktionella krav

Kraven är formulerade så att de går att verifiera. Ett icke-funktionellt krav utan mätbart
värde eller observerbart utfall är inte ett krav — då är det en ambition och hör hemma i
`03-kompletterande-krav.md` som antagande.

| Grupp | Rubrik | Främst kopplad till |
|-------|--------|---------------------|
| NFR-01 | Kompatibilitet med enheter och webbläsare | Spelare, Gästanvändare |
| NFR-02 | Prestanda och svarstid | Spelare — UC-02, UC-NFR-06, UC-NFR-07 |
| NFR-03 | Kvalitet i problemrapportering | Spelare — UC-28 |
| NFR-04 | Felhantering och robusthet | Spelare, Administratör — UC-28 |
| NFR-05 | Moderering | Administratör — UC-29 |
| NFR-06 | Användbarhet och tillgänglighet | Spelare, Gästanvändare |
| NFR-07 | Säkerhet och dataskydd | Registrerad spelare, DPO |
| NFR-08 | Tillförlitlighet och tillgänglighet | Samtliga aktörer |
| NFR-09 | Underhållbarhet och testbarhet | Utvecklare, Testare |
| NFR-10 | Tillgång till personuppgifter | Registrerad spelare — UC-NFR-02 |
| NFR-11 | Delning av personuppgifter med tredje part | Registrerad spelare — UC-NFR-03 |
| NFR-12 | Radering av personuppgifter | Registrerad spelare, DPO — UC-NFR-04, UC-NFR-05 |
| NFR-13 | Språk i gränssnittet | Samtliga mänskliga aktörer — SR-04.3 |


## NFR-01: Kompatibilitet med enheter och webbläsare

| ID | Krav |
|----|------|
| NFR-01.1 | Systemet ska fungera fullt ut i de två senaste versionerna av Chrome, Edge, Firefox och Safari. |
| NFR-01.2 | Systemet ska vara användbart på skärmbredder från 360 px till 1920 px. |
| NFR-01.3 | Systemet ska kunna styras med både mus och pekskärm. |
| NFR-01.4 | Systemet ska köras i webbläsaren utan att någon installation krävs. |
| NFR-01.5 | Systemet ska vara spelbart i både stående och liggande läge på mobil. |
| NFR-01.6 | Hela spelplanen ska rymmas på skärmen utan horisontell scroll på en enhet med 360 px bredd. |

---

## NFR-02: Prestanda och svarstid

| ID | Krav |
|----|------|
| NFR-02.1 | Startsidan ska vara färdigrenderad inom 2 sekunder vid 25 Mbit/s. |
| NFR-02.2 | Visuell återkoppling på ett drag ska visas inom 100 ms från klick eller tryck. |
| NFR-02.3 | Datorns drag ska levereras inom 3 sekunder oavsett svårighetsgrad. |
| NFR-02.4 | Kontrollen av fem i rad ska vara klar inom 100 ms efter varje drag. |
| NFR-02.5 | En inbjudningslänk ska genereras inom 1 sekund. |
| NFR-02.6 | Ett drag ska synas hos motståndaren inom 500 ms i ett parti mot en vän. |
| NFR-02.7 | Ett byte av svårighetsgrad eller brädstorlek ska återspeglas i gränssnittet inom 300 ms. |

**Mätpunkt för NFR-02.2 och NFR-02.4:** tiden mäts från den händelse där klicket eller
trycket registreras i klienten, till dess att den uppdaterade vyn är renderad. Mätningen görs
på referensenheten i NFR-01.2 vid 25 Mbit/s. Utan denna definition är NFR-02.2 inte testbart.

---

## NFR-03: Kvalitet i problemrapportering

**Relaterat UC:** UC-28

| ID | Krav |
|----|------|
| NFR-03.1 | Funktionen för problemrapportering ska nås inom högst två klick från valfri vy. |
| NFR-03.2 | En inskickad rapport ska bekräftas för spelaren inom 3 sekunder. |
| NFR-03.3 | Varje rapport ska automatiskt innehålla webbläsare, tidpunkt och parti-ID. |
| NFR-03.6 | Den enda personuppgift som får bifogas automatiskt är det synliga spelarnamnet. Inga andra personuppgifter får samlas in via rapporten. |
| NFR-03.7 | Systemet ska informera spelaren om vilka uppgifter som bifogas rapporten innan den skickas. |
| NFR-03.4 | Att öppna rapportformuläret ska inte avbryta eller påverka ett pågående parti. |
| NFR-03.5 | Om rapporten inte kan skickas ska den sparas lokalt så att spelaren kan skicka om den. |

---

## NFR-04: Felhantering och robusthet

| ID | Krav |
|----|------|
| NFR-04.1 | Alla felmeddelanden ska vara på engelska, beskriva vad som hänt och ange nästa steg för spelaren. |
| NFR-04.2 | Systemet ska bevara ett pågående partis tillstånd vid sidomladdning eller tillfälligt nätverksavbrott och tillåta återanslutning inom 5 minuter. |
| NFR-04.3 | Systemet ska upptäcka en frånkopplad motståndare och meddela den kvarvarande spelaren inom 15 sekunder. |
| NFR-04.4 | Varje inkommen rapport ska registreras med unikt ID och tidsstämpel. |
| NFR-04.5 | Systemet ska logga tekniska fel för felsökning utan att logga personuppgifter. |
| NFR-04.6 | Systemet ska aldrig lämna spelaren i ett läge utan väg vidare — varje felvy ska ha minst en åtgärd (försök igen eller tillbaka till start). |

---

## NFR-05: Moderering

**Relaterat UC:** UC-29

| ID | Krav |
|----|------|
| NFR-05.1 | En blockering av en spelare ska träda i kraft inom 1 minut. |
| NFR-05.2 | Moderationsbeslut ska loggas och sparas i 12 månader. |
| NFR-05.3 | Den rapporterade spelaren ska inte få veta vem som rapporterat. |
| NFR-05.4 | Rapporter ska köas i inkommen ordning och kunna hämtas av administratör inom 24 timmar. |
| NFR-05.5 | Ett modereringsbeslut ska gå att spåra till den administratör som fattade det. |
| NFR-05.6 | En blockering ska registreras med starttid och sluttid i UTC, så att den automatiska hävningen enligt FR-29.10 går att verifiera oberoende av tidszon. |
| NFR-05.7 | Systemet ska kunna visa en blockerings status (aktiv, utgången, hävd) vid varje given tidpunkt utan att blockeringstiden behöver löpa ut i realtid, så att FR-29.10 och NFR-05.2 kan testas med simulerad tid. |

---

## NFR-06: Användbarhet och tillgänglighet

| ID | Krav |
|----|------|
| NFR-06.1 | Systemet ska uppfylla WCAG 2.1 nivå AA. |
| NFR-06.2 | Kontrasten mellan text och bakgrund ska vara minst 4,5:1. |
| NFR-06.3 | Svarta och vita stenar ska gå att skilja åt på mer än enbart färg, så att färgblinda spelare kan spela. |
| NFR-06.4 | Hela spelet ska gå att styra med tangentbord. |
| NFR-06.5 | Klick- och tryckytor ska vara minst 44 × 44 px på pekskärm. |
| NFR-06.6 | En ny spelare ska kunna starta och genomföra ett parti utan extern hjälp inom 2 minuter. |

---

## NFR-07: Säkerhet och dataskydd

| ID | Krav |
|----|------|
| NFR-07.1 | All kommunikation mellan klient och server ska ske över TLS 1.2 eller senare. |
| NFR-07.2 | Inbjudningskoder ska vara oförutsägbara med minst 128 bitars entropi. |
| NFR-07.3 | Spelarnamn och fritext ska saneras så att skript inte kan köras i andra spelares webbläsare. |
| NFR-07.4 | Systemet ska inte samla in fler personuppgifter än det synliga spelarnamnet i gästläge. |
| NFR-07.5 | Partidata för gästspel ska raderas senast 30 dagar efter att partiet avslutats. |
| NFR-07.6 | Lösenord ska lagras som bcrypt-hash. Lösenord i klartext ska aldrig lagras, loggas eller ingå i en dataexport. |
| NFR-07.7 | Ett misslyckat inloggningsförsök ska inte avslöja om e-postadressen är registrerad i systemet. |
| NFR-07.8 | En extern identitetsleverantör ska inte få tillgång till fler personuppgifter än vad kopplingen kräver. |

---

## NFR-08: Tillförlitlighet och tillgänglighet

| ID | Krav |
|----|------|
| NFR-08.1 | Systemet ska ha minst 99 % drifttid mätt per månad, exklusive planerat underhåll. |
| NFR-08.2 | Ett parti ska aldrig hamna i ett tillstånd där ingen spelare kan göra ett giltigt drag utan att partiet avslutas korrekt. |
| NFR-08.3 | Systemet ska klara minst 100 samtidiga pågående partier utan att svarstiderna i NFR-02 överskrids. |

---

## NFR-09: Underhållbarhet och testbarhet

| ID | Krav |
|----|------|
| NFR-09.1 | Spellogiken ska vara separerad från gränssnittet så att regler kan enhetstestas utan webbläsare. |
| NFR-09.2 | Varje funktionellt krav i `02-funktionella-krav.md` ska vara verifierbart genom minst ett automatiserat test. |
| NFR-09.3 | Datorns drag ska gå att göra deterministiska via en seed, så att partier kan återskapas i test. |
| NFR-09.4 | Alla tester ska köras automatiskt vid varje push till huvudgrenen. |
| NFR-09.5 | Kravdokumenten ska versionshanteras i samma repo som koden. |


## NFR-10: Tillgång till personuppgifter

| **ID** | **Krav** |
| --- | --- |
| NFR-10.1 | Systemet ska göra det möjligt för en registrerad spelare att begära tillgång till sina personuppgifter. |
| NFR-10.2 | Systemet ska tillhandahålla de begärda personuppgifterna i ett strukturerat format. |

---

## NFR-11: Delning av personuppgifter med tredje part

| **ID** | **Krav** |
| --- | --- |
| NFR-11.1 | Systemet ska informera användaren om personuppgifter behandlas av tredje part. |
| NFR-11.2 | Systemet ska informera användaren om personuppgifter överförs till ett land utanför det tillämpliga dataskyddsområdet och vilka skyddsåtgärder som gäller. |

---

## NFR-12: Radering av personuppgifter

**Relaterat UC:** UC-NFR-04, UC-NFR-05  
**Relaterade FR:** FR-30.1 – FR-30.13  
**GDPR-referens:** Artikel 17 (rätten till radering)

| ID | Krav |
|----|------|
| NFR-12.1 | Systemet ska göra det möjligt för en registrerad spelare att begära radering av sina personuppgifter. |
| NFR-12.2 | En verifierad raderingsbegäran ska vara genomförd senast 30 dagar efter att den togs emot (SR-03.2). |
| NFR-12.3 | Systemet ska bekräfta en genomförd radering till spelaren via e-post. |
| NFR-12.4 | Personuppgifter som har raderats ska inte kunna återskapas från säkerhetskopior, loggar, cacheminnen eller export efter att raderingen är genomförd. |
| NFR-12.5 | Speldata som bevaras efter en radering ska vara anonymiserad enligt definitionen i `00-begreppslista.md` och inte gå att koppla till en identifierbar person, varken direkt eller genom sammanställning med andra uppgifter i systemet. |
| NFR-12.6 | Samtyckesregister och begäranden ska bevaras i anonymiserad form i minst 3 år för efterlevnadsgranskning (SR-03.4). |
| NFR-12.7 | Raderingen ska kunna verifieras i en testmiljö utan att 30-dagarsfönstret behöver förflyta i realtid. |

**Anmärkning om testbarhet.** NFR-12.4 är formulerat som ett negativt påstående — att ett
tillstånd ska vara omöjligt. Ett sådant krav går inte att bevisa genom test, bara att
falsifiera: ett test kan visa att uppgifterna *går* att återskapa, aldrig att de aldrig gör
det. Kravet verifieras därför genom ett begränsat antal namngivna sökvägar (databas,
säkerhetskopia, applikationslogg, dataexport, sökindex). Se AC-NFR-04-05.

---

## NFR-13: Språk i gränssnittet

**Kopplad begränsning:** SR-04.3  
**Relaterade NFR:** NFR-04.1, NFR-06.1

| ID | Krav |
|----|------|
| NFR-13.1 | All text som systemet presenterar för en användare ska vara på engelska. |
| NFR-13.2 | Kravet i NFR-13.1 omfattar knappar och etiketter, fel- och bekräftelsemeddelanden, regelsammanfattningen, cookie-texter, standardvärden som visas för användaren, samt e-post som systemet skickar. |
| NFR-13.3 | Dokumentets rotelement ska ange `lang="en"`, så att skärmläsare uttalar innehållet korrekt (WCAG 2.1, kriterium 3.1.1). |
| NFR-13.4 | Den byggda applikationen ska inte innehålla några användarvända textsträngar på annat språk än engelska. |
| NFR-13.5 | Datum, klockslag och tal som visas för användaren ska formateras entydigt och inte bero på webbläsarens språkinställning. |

**Anmärkning om dokumentationens språk.** Kravdokumentationen i detta repo är skriven på svenska,
och begreppsmodellen i `05-begreppsmodell.md` använder svenska begreppsnamn. Det är ingen
motsägelse mot NFR-13: kraven skiljer på **dokumentationsspråk** och **produktspråk**.
Dokumentationen läses av gruppen, gränssnittet av användaren. Där ett krav anger en knapptext
inom citattecken är den engelska strängen den som gäller; den svenska prosan runt omkring namnger
funktionen, inte etiketten.

**Om testbarheten.** NFR-13.1 och NFR-13.2 är svåra att verifiera uttömmande — det är samma sorts
negativa påstående som NFR-12.4, fast om språk i stället för data. NFR-13.4 är formulerat för att
ge en avgränsad kontroll som går att köra: en sökning i byggartefakten efter svenska tecken
(å, ä, ö) och efter en lista kända svenska ord. Den fångar inte en engelsk mening med fel
terminologi, och den ska inte påstås göra det. Se AC-NFR-13.

---
