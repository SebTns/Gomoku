# UC-28: Rapportera ett tekniskt problem

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-28 |
| **Namn** | Rapportera ett tekniskt problem |
| **Version** | 1.1 |
| **Primär aktör** | Spelare |
| **Sekundär aktör** | Administratör |
| **Relaterade FR** | FR-28.1 – FR-28.10 |
| **Relaterade NFR** | NFR-03.1 – NFR-03.7, NFR-04.1, NFR-04.4 – NFR-04.6 |
| **Relaterade AC** | AC-28-01 – AC-28-06 |

## Beskrivning
Spelaren vill kunna rapportera ett tekniskt problem som har uppstått i spelet så att problemet
kan registreras och hanteras vidare.

## Förutsättningar
- Spelaren har öppnat Gomoku-spelet.
- Ett tekniskt problem har uppstått och upptäckts av spelaren.

## Huvudflöde

1. Spelaren väljer "Report a Problem".
2. Systemet visar ett formulär för problemrapportering.
3. Systemet visar vilka uppgifter som bifogas automatiskt (webbläsare, tidpunkt, parti-ID och
   synligt spelarnamn).
4. Spelaren beskriver det tekniska problemet.
5. Spelaren väljer att skicka rapporten.
6. Systemet kontrollerar att en beskrivning av problemet finns.
7. Systemet registrerar problemrapporten.
8. Systemet tilldelar rapporten ett unikt rapport-ID och en tidsstämpel.
9. Systemet visar en bekräftelse på att rapporten har registrerats.
10. Spelaren kan fortsätta använda spelet.

## Alternativa flöden

### AF-01: Beskrivning saknas
Vid steg 6 saknas en beskrivning av problemet.
- Systemet informerar spelaren om att en beskrivning krävs.
- Rapporten registreras inte.
- Spelaren kan komplettera beskrivningen.
- Flödet återgår till steg 5.

### AF-02: Rapporten kan inte registreras
Vid steg 7 kan systemet inte registrera problemrapporten.
- Systemet informerar spelaren om att rapporten inte har registrerats.
- Rapporten registreras inte som skickad.
- Systemet sparar rapporten lokalt (NFR-03.5).
- Spelaren kan försöka skicka rapporten igen.

### AF-03: Avbryta rapporteringen
Före steg 5 väljer spelaren att avbryta rapporteringen.
- Systemet stänger rapportformuläret.
- Ingen problemrapport registreras.
- Spelaren återgår till spelet.

### AF-04: Rapporten skickas om från lokal lagring
Efter AF-02 finns en lokalt sparad rapport.
- Systemet erbjuder spelaren att skicka om den sparade rapporten.
- Vid lyckad sändning fortsätter flödet från steg 8.
- Den lokalt sparade kopian tas bort när rapporten har registrerats.

## Postconditions

**Lyckat:** Problemrapporten är registrerad och har fått ett unikt rapport-ID och en tidsstämpel.
Spelaren har fått en bekräftelse. Ett eventuellt pågående parti är oförändrat.

**Misslyckat:** Problemrapporten är inte registrerad, spelaren har informerats om detta och
rapporten finns kvar lokalt så att den kan skickas om.

**Avbrutet:** Ingen problemrapport är registrerad och ingenting har sparats lokalt.

## Särskilda krav
- Problemrapporteringen ska kunna nås inom högst två klick från valfri vy (NFR-03.1).
- En registrerad rapport ska bekräftas inom 3 sekunder (NFR-03.2).
- Rapporten ska automatiskt innehålla webbläsare, tidpunkt och parti-ID (NFR-03.3).
- Den enda personuppgift som får bifogas automatiskt är det synliga spelarnamnet (NFR-03.6).
- Spelaren ska informeras om vad som bifogas innan rapporten skickas (NFR-03.7).
- Rapporteringen ska inte avbryta ett pågående parti (NFR-03.4).
- Om rapporten inte kan skickas ska den sparas lokalt så att spelaren kan försöka igen (NFR-03.5).
- Felmeddelanden ska vara på engelska, beskriva vad som hänt och ange nästa steg (NFR-04.1).
- Varje rapport ska registreras med ett unikt ID och en tidsstämpel (NFR-04.4).
- Systemet ska inte logga personuppgifter i den tekniska felloggen (NFR-04.5).
- Varje felvy ska ha minst en väg vidare (NFR-04.6).

## Kända motsägelser

**Är spelarnamnet en personuppgift?** `00-begreppslista.md` definierar personuppgifter som all
information som rör en identifierbar person och räknar uttryckligen upp användarnamn. NFR-03.3
formulerades ursprungligen som att rapporten skickas "utan personuppgifter utöver spelarnamnet",
vilket läser som att spelarnamnet inte vore en personuppgift. Begreppslistan tar företräde:
spelarnamnet *är* en personuppgift, och det är därför NFR-03.3 har delats upp i NFR-03.3,
NFR-03.6 och NFR-03.7 — insamlingen är tillåten men ska vara minimerad och synlig för spelaren.

## Öppna frågor
- Ska spelaren kunna bifoga en bild eller skärmdump? I så fall måste NFR-03.6 skrivas om, eftersom
  en skärmdump kan innehålla personuppgifter som systemet inte kontrollerar.
- Ska spelaren kunna följa statusen på sin problemrapport? Det kräver att rapport-ID kopplas till
  spelaren och därmed bevaras längre än rapporten i sig.
- Hur länge ska en lokalt sparad rapport ligga kvar om spelaren aldrig skickar om den?
