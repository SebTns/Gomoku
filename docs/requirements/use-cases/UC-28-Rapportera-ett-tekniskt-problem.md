# UC-28: Rapportera ett teknisk problem

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-28 |
| **Namn** | Rapportera ett teknisk problem|
| **Version** | 1.0 |
| **Primär aktör** |spelare |
| **Sekundär aktör** |Administatör |
| **Relaterade FR** |FR-28.1 – FR-28.6 |
| **Relaterade NFR** |NFR-03.1 – NFR-03.5, NFR-04.1, NFR-04.4 – NFR-04.6 |

## Beskrivning
Spelaren vill kunna rapportera ett tekniskt problem som har uppstått i spelet så att problemet kan registreras och hanteras vidare.



## Förutsättningar
- Spelaren har öppnat Gomoku-spelet, Ett teksniskt problem har uppstått och upptäckts av spelaren.
  
## Huvudflöde

   1. Spelaren väljer "Rapportera problem".
   2. Systemet visar ett formulär för problemrapportering.
   3. Spelaren beskriver det tekniska problemet.
   4. Spelaren väljer att skicka rapporten.
   5. Systemet kontrollerar att en beskrivning av problemet finns.
   6. Systemet registrerar problemrapporten.
   7. Systemet tilldelar rapporten ett unikt rapport-ID.
   8. Systemet visar en bekräftelse på att rapporten har registrerats.
   9. Spelaren kan fortsätta använda spelet.


## Alternativa flöden

### AF-01: Beskrivning saknas

Vid steg 5 saknas en beskrivning av problemet.

- Systemet informerar spelaren om att en beskrivning krävs.
- Rapporten registreras inte.
- Spelaren kan komplettera beskrivningen.
- Flödet återgår till steg 4.

### AF-02: Rapporten kan inte registreras

Vid steg 6 kan systemet inte registrera problemrapporten.

- Systemet informerar spelaren om att rapporten inte har registrerats.
- Rapporten registreras inte som skickad.
- Spelaren kan försöka skicka rapporten igen.
- Om rapporten inte kan skickas ska den sparas lokalt enligt NFR-03.5.

### AF-03: Avbryta rapporteringen

Före steg 4 väljer spelaren att avbryta rapporteringen.

- Systemet stänger rapportformuläret.
- Ingen problemrapport registreras.
- Spelaren återgår till spelet. 

## Postconditions

**Lyckat:** Problemrapporten är registrerad och har fått ett unikt rapport-ID. Spelaren har fått en bekräftelse.

**Misslyckat:** Problemrapporten är inte registrerad och spelaren har informerats om detta.

## Särskilda krav
- Problemrapporteringen ska kunna nås inom högst två klick från valfri vy (NFR-03.1).
- En registrerad rapport ska bekräftas inom 3 sekunder (NFR-03.2).
- Rapporten ska automatiskt innehålla webbläsare, tidpunkt och parti-ID (NFR-03.3).
- Rapporteringen ska inte avbryta ett pågående parti (NFR-03.4).
- Om rapporten inte kan skickas ska den sparas lokalt så att spelaren kan försöka igen (NFR-03.5).
- Varje rapport ska registreras med ett unikt ID och en tidsstämpel (NFR-04.4).

## Öppna frågor
- Ska spelaren kunna bifoga en bild eller skärmdump?
- Ska spelaren kunna följa statusen på sin problemrapport?

---


