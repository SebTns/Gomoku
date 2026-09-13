# 3. Kompletterande krav

## SR-01: Affärsregler

Uppsatsmallen kräver inget eget affärsregeldokument, och något sådant finns inte i detta repo.
Reglerna nedan är de som styr systemets beteende men inte hör hemma som funktionella krav.
Definitionerna i `00-begreppslista.md` tar företräde vid konflikt.

| ID | Regel | Källa |
|----|-------|-------|
| SR-01.1 | Ett parti spelas alltid mellan exakt två spelare. | `00-begreppslista.md`, Parti |
| SR-01.2 | Svart gör alltid första draget. | `00-begreppslista.md`, Svart — FR-04.3 |
| SR-01.3 | Vinstvillkoret är exakt fem stenar i rad. Sex eller fler i rad är inte en vinst. | `00-begreppslista.md`, 5 i rad / 6 eller mer i rad — FR-08.14, FR-08.15 |
| SR-01.4 | En placerad sten kan inte flyttas eller tas bort. | `00-begreppslista.md`, Sten |
| SR-01.5 | Ett uppgivande registreras som förlust för den som ger upp och vinst för motståndaren. | `00-begreppslista.md`, Ge upp — FR-09.3 |
| SR-01.6 | AI-motståndaren behandlas som en spelare enligt spelreglerna men rankas inte på topplistan. | `00-begreppslista.md`, AI-motståndare |
| SR-01.7 | Endast spelare med minst 10 avslutade partier visas på topplistan. | `00-begreppslista.md`, Topplista |
| SR-01.8 | En inbjudan är giltig i 15 minuter och kan användas av högst en motståndare. | FR-07.3, FR-07.8 |
| SR-01.9 | En gästanvändare har inte tillgång till historik, topplista eller sociala funktioner. | `00-begreppslista.md`, Gästanvändare |

> **Not.** Hänvisningen till `08-business-rules.md` är borttagen. Filen fanns i lärarens
> referensrepo `miwashi-edu/gomoku` men har aldrig funnits här, och i vår numrering är 08
> *Use Cases och Test Cases*.

## SR-02: Tekniska begränsningar

| ID | Begränsning |
|----|-----------|
| SR-02.1 | Applikationen ska fungera i alla nuvarande evergreen-webbläsare: Chrome, Firefox, Safari och Edge. |
| SR-02.2 | Frontend-gränssnittet ska implementeras som en Single-Page Application (SPA) med hjälp av React. |
| SR-02.3 | Backend-API:et ska vara RESTful och endast tillhandahållas via HTTPS. |
| SR-02.4 | Realtidskommunikation (multiplayer-rörelser, aviseringar) ska använda WebSockets. |
| SR-02.5 | All beständig data ska lagras i en relationsdatabas (PostgreSQL). |
| SR-02.6 | Systemet ska vara containeriserat med Docker och kunna distribueras till en molnmiljö. |
| SR-02.7 | Inga analyser eller spårningsskript från tredje part får laddas innan användaren ger sitt samtycke till cookies. |

## SR-03: Regulatoriska begränsningar

| ID | Begränsning |
|----|-----------|
| SR-03.1 | Systemet omfattas av GDPR eftersom det behandlar personuppgifter för EU-invånare. |
| SR-03.2 | Begäran om åtkomst, radering och dataportabilitet måste uppfyllas inom 30 dagar. |
| SR-03.3 | Personuppgifter i vila och under överföring måste krypteras (AES-256 i vila, TLS 1.2+ under överföring). |
| SR-03.4 | Samtyckesregister och revisionsloggar måste behållas i minst 3 år. |
| SR-03.5 | En anmälan om dataintrång måste utfärdas till tillsynsmyndigheten inom 72 timmar efter upptäckten. |

## SR-04: Antaganden

| ID | Antagande |
|----|-----------|
| SR-04.1 | Spelare har tillgång till en enhet med en modern webbläsare och en stabil internetanslutning. |
| SR-04.2 | Den primära målgruppen finns i Europeiska unionen. |
| SR-04.3 | Systemet kommer initialt endast att stödja engelska; lokalisering är utanför ramen för v1. |
| SR-04.4 | AI:n körs på serversidan; klienter skickar flyttförfrågningar och tar emot AI-svar. |
