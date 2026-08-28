Icke-funktionella krav
NFR-01 Kompatibilitet med enheter och webbläsare
NFR-02 Prestanda och svarstid
NFR-03 Rapportering av problem
NFR-04 Hantering av problem
NFR-05 Moderering och spelarrapporter


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

---

## NFR-03: Kvalitet i problemrapportering

**Relaterat UC:** UC-28

| ID | Krav |
|----|------|
| NFR-03.1 | Funktionen för problemrapportering ska nås inom högst två klick från valfri vy. |
| NFR-03.2 | En inskickad rapport ska bekräftas för spelaren inom 3 sekunder. |
| NFR-03.3 | Varje rapport ska automatiskt innehålla webbläsare, tidpunkt och parti-ID, utan personuppgifter utöver spelarnamnet. |
| NFR-03.4 | Att öppna rapportformuläret ska inte avbryta eller påverka ett pågående parti. |
| NFR-03.5 | Om rapporten inte kan skickas ska den sparas lokalt så att spelaren kan skicka om den. |

---

## NFR-04: Felhantering och robusthet

| ID | Krav |
|----|------|
| NFR-04.1 | Alla felmeddelanden ska vara på svenska, beskriva vad som hänt och ange nästa steg för spelaren. |
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
