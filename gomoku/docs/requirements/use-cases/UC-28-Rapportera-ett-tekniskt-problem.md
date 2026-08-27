
# UC-28-Rapportera ett teknisk problem
  Use Case ID: UC-28
  Namn: Papportera ett teknidk problem
  Primär aktör: spelare
  Sekund aktör: Administatör

## Beskrivning: Spelaren vill kunna rapportera ett tekniskt problem som hat uppstått i spelet, så att p
roblemet kan undersökas och hanteras.

## Förutsättningar: Spelaren har öppnat Gomoku-spelet, Ett tksniskt problem har uppstått och upptäckts av spelaren.

## Huvudflöde:
   1. Spelaren väjär "Rapportea problem".
   2. Systemet visar ett formuär för problemrapportering.
   3. Spelaren beskriver vad som hände och vad some gick fel.
   4. Spelaren skickar in rapporten.
   5. Syestem sparar rapporten.
   6. Systemet skickar rapporten vidare så att den kan hanteras.
   7. Systemet visar en bekräftelse på rapporten har skickats.
   8. Spelaren kan fortsätta använda spelet.

## Alternativa flöden
   ### AF-01 Information saknas vid steg 5 som behövs i rapporten. Systemet visar vad som saknas.
             Spelaren kompletterar informationen.
             Spelaren försöker skicka rapporten igen.

   ### AF-02 Rapporten kan inte skickas vid steg 6.
             Systemet visar ett felmeddelande.
             Rapporten registreras inte som skickad.
             Spelaren får möjlighet att försöka igen senare.
   ### AF-03 Spelaren avbryter rapporteringen, spelaren väljer att inte skicka rapporten.
             Systemet stänger formuläret. Ingen rapport skickas.

## Postconditions
   **Lyckas:** Rapporten är sparad och skickad för vidare hantering. Spelaren har fått en bekräftelse.
   **Misslyckas:** Rapporten har inte skickas och spelaren får information om något gick fel.

