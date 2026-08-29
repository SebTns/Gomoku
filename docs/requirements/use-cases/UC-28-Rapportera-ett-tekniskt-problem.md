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
Spelaren vill kunna rapportera ett tekniskt problem som hat uppstått i spelet, så att p
roblemet kan undersökas och hanteras.


## Förutsättningar
- Spelaren har öppnat Gomoku-spelet, Ett teksniskt problem har uppstått och upptäckts av spelaren.
- 
## Huvudflöde

   1. Spelaren väljer "Rapportera problem".
   2. Systemet visar ett formulär för problemrapportering.
   3. Spelaren beskriver vad som hände och vad som gick fel.
   4. Spelaren skickar in rapporten.
   5. Systemet sparar rapporten.
   6. Systemet skickar rapporten vidare så att den kan hanteras.
   7. Systemet visar en bekräftelse på rapporten har skickats.
   8. Spelaren kan fortsätta använda spelet.


## Alternativa flöden

### AF-01: Rapporten kan inte skickas

-Information saknas vid steg 5 som behövs i rapporten.
-Systemet visar vad som saknas.
-Spelaren kompletterar informationen. Spelaren försöker skicka rapport igen.
-Vid steg 6 kan systemet inte spara eller skicka rapporten. 
-Rapporten registreras inte som skickad. 

### AF-02: Avbryta rapporteringen 

-Spelaren avbryter rapporteringen Spelaren väljer att inte skicka rapporten. 
-Systemet stänger formuläret.
-Ingen rapport skickas.
-Spelaren kommer tillbaka till spelet. 

## Postconditions

**Lyckat:** Rapporten är sparad och skickad för vidare hantering. Spelaren har fått en bekräftelse.

**Misslyckat:** Rapporten har inte skickats och spelaren får information om att något gick fel.

## Särskilda krav
- - Problemrapporteringen ska kunna nås inom högst två klick från valfri vy (NFR-03.1).
- En inskickad rapport ska bekräftas inom 3 sekunder (NFR-03.2).
- Rapporten ska automatiskt innehålla webbläsare, tidpunkt och parti-ID (NFR-03.3).
- Rapporteringen ska inte avbryta ett pågående parti (NFR-03.4).
- Om rapporten inte kan skickas ska den sparas lokalt så att spelaren kan försöka igen (NFR-03.5).
- Varje rapport ska registreras med ett unikt ID och en tidsstämpel (NFR-04.4).

## Öppna frågor
- Ska spelaren kunna bifoga en bild eller skärmdump?
- Ska spelaren kunna följa statusen på sin problemrapport?

---


