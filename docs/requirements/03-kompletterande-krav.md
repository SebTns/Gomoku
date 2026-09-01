# 3. Kompletterande krav

## SR-01: Affärsregler

Affärsreglerna har extraherats till ett eget dokument för tydlighetens skull.
Se [08 – Affärsregler](08-business-rules.md).

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
