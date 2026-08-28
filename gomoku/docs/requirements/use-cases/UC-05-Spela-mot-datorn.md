# UC-05: Spela mot datorn

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-05 |
| **Namn** | Spela mot datorn |
| **Version** | 1.1 |
| **Primär aktör** | Spelare |
| **Sekundär aktör** | Datorn |
| **Relaterade FR** | FR-06.1 – FR-06.8, FR-08.8 |
| **Relaterade NFR** | NFR-02.3, NFR-04.2, NFR-04.6, NFR-09.3 |

## Beskrivning
Spelaren spelar ett helt parti Gomoku mot datorn, från partistart till resultat.

## Förutsättningar
- Spelaren har öppnat spelet och det fungerar.
- Startsidan visas.

## Huvudflöde

1. Systemet visar startsidan.
2. Spelaren väljer "Spela mot datorn".
3. Systemet visar de svårighetsgrader som finns (→ UC-08).
4. Spelaren väljer en svårighetsgrad.
5. Systemet startar ett nytt parti mot datorn (→ UC-01).
6. Systemet visar spelplanen och vem som börjar.
7. Spelaren gör ett drag på en ledig plats (→ UC-02).
8. Systemet registrerar spelarens drag.
9. Systemet visar att datorn beräknar sitt drag.
10. Datorn gör sitt drag på en ledig plats.
11. Systemet registrerar datorns drag.
12. Systemet kontrollerar efter varje drag om någon har fått fem i rad.
13. Spelaren och datorn fortsätter göra drag i tur och ordning tills partiet avgörs.
14. När fem i rad uppstår, eller brädet blir fullt, avslutas partiet.
15. Systemet visar resultatet.

## Alternativa flöden

### AF-01: Partiet mot datorn kan inte starta
Vid steg 5 misslyckas partistarten.
- Systemet visar ett meddelande om att partiet inte kunde startas.
- Spelaren stannar kvar på sidan.
- Spelaren kan försöka starta partiet igen eller gå tillbaka till startsidan.

### AF-02: Datorn kan inte göra sitt drag
Vid steg 10 kan datorn inte ta fram ett drag.
- Systemet visar att något gick fel.
- Partiet pausas och partitillståndet bevaras.
- Spelaren kan försöka igen eller avsluta partiet.

### AF-03: Datorn svarar inte i tid
Vid steg 10 överskrids tidsgränsen på 3 sekunder.
- Systemet informerar spelaren om fördröjningen.
- Systemet försöker igen en gång innan AF-02 tillämpas.

### AF-04: Spelaren avslutar partiet i förtid
Under steg 13 väljer spelaren att avbryta.
- Systemet begär bekräftelse.
- Vid bekräftelse avslutas partiet utan vinnare (→ UC-11).

## Postconditions

**Lyckat:** Partiet mot datorn är avslutat och spelaren kan se resultatet.

**Pågående:** Om partiet inte är avslutat fortsätter spelaren och datorn att göra drag i tur och ordning.

**Misslyckat:** Partiet kunde inte startas eller genomföras, och spelaren har fått besked om varför.

## Särskilda krav
- Datorns drag ska levereras inom 3 sekunder oavsett svårighetsgrad (NFR-02.3).
- Partitillståndet ska bevaras vid ett pausat parti och återanslutning ska vara möjlig inom 5 minuter (NFR-04.2).
- Varje felvy ska ha minst en väg vidare (NFR-04.6).
- Datorns drag ska gå att göra deterministiska via en seed, så att partier kan återskapas i test (NFR-09.3).

## Öppna frågor
- Ska ett avbrutet parti mot datorn räknas som förlust i statistiken (→ UC-17)?
