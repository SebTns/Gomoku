# UC-NFR-04: Begär radering av data (rätt till radering)

| Fält | Värde |
|-------|-------|
| **Use Case ID** | UC-NFR-04 |
| **Namn** | Begär radering av data (rätt till radering) |
| **Version** | 1.1 |
| **Primär aktör** | Registrerad spelare |
| **Sekundära aktörer** | Systemadministratör, dataskyddsombud (DPO), e-posttjänst |
| **Relaterade FR** | FR-30.1 – FR-30.13 |
| **Relaterade NFR** | NFR-12.1 – NFR-12.7, NFR-07.1, NFR-07.5 |
| **Kopplade begränsningar** | SR-03.1, SR-03.2, SR-03.3, SR-03.4 |
| **GDPR-referens** | Artikel 17 |
| **Relaterade AC** | AC-NFR-04-01 – AC-NFR-04-09 |

## Beskrivning
En registrerad spelare utövar sin rätt till radering genom att begära att alla deras
personuppgifter raderas permanent från systemet.

> **Obs:** En fullständig kontoradering som också inaktiverar kontot beskrivs i
> UC-23 (Radera ett konto) och i GDPR-ramverket UC-NFR-05 (Ta bort konto). Detta användningsfall
> omfattar en fristående raderingsbegäran som kan skickas in utan att omedelbart utlösa
> kontoavaktivering, samt den raderingsdelprocess som UC-NFR-05 utlöser.

## Förutsättningar
- Spelaren har personuppgifter registrerade i systemet.
- En raderingsbegäran (typ: RADERING) har skapats och verifierats enligt FR-30.2 — antingen via
  självbetjäning (→ UC-NFR-05) eller via en supportkanal.

## Huvudflöde

1. Systemet tar emot en verifierad raderingsbegäran (typ: RADERING, status: PÅGÅENDE).
2. Systemet bekräftar för spelaren att begäran är mottagen och anger senaste datum för radering.
3. Systemet identifierar alla personuppgifter som är kopplade till spelaren:
   - Användarpost (e-post, användarnamn, lösenordshash, avatar-URL) — **raderas**
   - Samtyckesregister — **anonymiseras**, bevaras för efterlevnadsgranskning (SR-03.4)
   - Raderingsbegäranden — **anonymiseras**, bevaras för efterlevnadsgranskning
   - Drag — **anonymiseras**, spelar-ID nollställs
   - Partier — **anonymiseras** för denna spelare, motståndarreferenser bevaras
   - Spelarstatistik — **raderas**
4. Systemet raderar eller anonymiserar varje datakategori enligt lagringsschemat (SR-03.2).
5. Systemet markerar kontot som raderat med tidpunkt.
6. Systemet sätter begärans status till GENOMFÖRD och registrerar tidpunkten.
7. Systemet skickar en bekräftelse på genomförd radering till spelarens e-postadress. Meddelandet
   skickas innan åtkomsten till kontot återkallas.

## Alternativa flöden

### AF-01: Radering kan inte slutföras inom 30 dagar
Vid steg 4 förhindrar en teknisk försening fullständig radering inom det lagstadgade fönstret.
- Systemet underrättar dataskyddsombudet automatiskt.
- Spelaren får ett meddelande som förklarar förseningen och anger ett nytt datum (FR-30.11).
- Begärans status förblir PÅGÅENDE.

### AF-02: Rättslig reservation förhindrar fullständig radering
Vid steg 3 måste vissa uppgifter behållas på grund av en rättslig skyldighet.
- Systemet raderar alla uppgifter som inte omfattas av skyldigheten.
- Systemet informerar spelaren om vilka uppgifter som bevaras och på vilken rättslig grund
  (FR-30.12).
- Dataskyddsombudet dokumenterar undantaget.

### AF-03: Begäran kan inte verifieras
Vid steg 1 går det inte att fastställa att begäran kommer från spelaren själv.
- Ingen radering påbörjas.
- Systemet informerar den som skickat begäran om att verifiering krävs.
- Begäran registreras som AVVISAD med orsak.

## Postconditions

**Lyckat:** Alla personuppgifter är raderade eller anonymiserade inom 30 dagar. Begärans status är
GENOMFÖRD. Bekräftelsemeddelande är skickat. Samtyckes- och begärandeuppgifter finns kvar i
icke-identifierbar form.

**Misslyckat:** Raderingen är inte genomförd, dataskyddsombudet är underrättat och spelaren har
informerats om orsak och nytt datum.

## Särskilda krav
- Raderingen ska vara genomförd senast 30 dagar efter verifierad begäran (NFR-12.2, SR-03.2).
- Raderade personuppgifter ska inte kunna återskapas (NFR-12.4).
- Bevarad speldata ska vara anonymiserad enligt definitionen i `00-begreppslista.md` (NFR-12.5).
- Samtyckesregister och begäranden ska bevaras i minst 3 år i anonymiserad form (NFR-12.6, SR-03.4).
- Raderingen ska gå att verifiera i testmiljö utan att 30 dagar förflyter (NFR-12.7).
- All kommunikation ska ske över TLS 1.2 eller senare (NFR-07.1).

## Testkriterier

Verifieras av AC-NFR-04-01 – AC-NFR-04-09. Sammanfattning:

| Kriterium | Verifieras av | Kommentar |
|---|---|---|
| Spelaren kan initiera en raderingsbegäran | AC-NFR-04-01 | Positivt, direkt observerbart |
| Begäran verifieras innan radering | AC-NFR-04-02 | Negativt fall |
| Personuppgifter är raderade efter genomförd radering | AC-NFR-04-03 | Positivt, per namngiven sökväg |
| Bevarad speldata kan inte kopplas till individen | AC-NFR-04-04 | Positivt, med sammanställningstest |
| Personuppgifter kan inte återskapas | AC-NFR-04-05 | **Går inte att bevisa — se nedan** |
| Bekräftelsemejl skickas | AC-NFR-04-06 | Positivt |
| Radering inom 30 dagar | AC-NFR-04-07 | Simulerad tid (NFR-12.7) |
| Försening hanteras | AC-NFR-04-08 | Negativt fall, AF-01 |
| Rättslig reservation hanteras | AC-NFR-04-09 | Negativt fall, AF-02 |

**Om det kriterium som inte går att bevisa.** "Personuppgifter kan inte återställas efter
radering" är ett negativt påstående om ett tillstånd som ska vara omöjligt. Ett test kan bara
visa att uppgifterna *går* att återskapa från en viss sökväg — aldrig att det är omöjligt från
varje tänkbar sökväg. Kravet är därför omformulerat till en avgränsad, testbar form:
uppgifterna ska inte gå att läsa ut ur fem namngivna sökvägar (databas, senaste
säkerhetskopia, applikationslogg, dataexport, sökindex). Det är inte samma sak som kravet i
GDPR-mening, och skillnaden är medveten. Se `10-reflektioner.md`.

## Öppna frågor
- Vilken supportkanal gäller för en raderingsbegäran som inte görs via självbetjäning? Det finns
  inget use case för GDPR-support i detta repo. Lärarens referensrepo har ett (UC-NFR-09 Contact
  GDPR Support) — antingen skrivs ett motsvarande UC eller så tas hänvisningen bort.
- Ska en gästspelares partidata omfattas? NFR-07.5 raderar den efter 30 dagar automatiskt, men
  gästen har inget konto att begära radering från.
- Hur hanteras motståndarens rätt till sin egen partihistorik när den ena parten raderas?

## Ändringslogg

**1.1** — Rättade felaktiga korsreferenser. Filen hänvisade till "UC-18 (Radera konto)",
"UC-NFR-07" och "UC-NFR-09". I detta repo är UC-18 *Spela multiplayer lokalt*, UC-NFR-07 är
*Player Action Feedback* och UC-NFR-09 finns inte. Numren kom från lärarens referensrepo
`miwashi-edu/gomoku`, där de stämmer. Texten var alltså inflyttad utan att numren skrivits om.
Rätt referenser i detta repo är UC-23 (Radera ett konto) och UC-NFR-05 (Ta bort konto).
Det tomma fältet **Relaterad NFR** (`NFR-`) är ifyllt med NFR-12, som skapades för ändamålet —
ingen befintlig NFR täckte radering.
