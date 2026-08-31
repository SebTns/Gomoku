# UC-30: Ändra kontoinställningar

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-30 |
| Namn | Ändra kontoinställningar |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet, Databasen |
| Relaterade FR | FR-xx (Konto och inloggning) |
| Relaterade NFR | NFR-07.3 |

---

## Beskrivning

Spelaren ändrar sina kontoinställningar, såsom synligt namn och e-postadress, så att profilen är uppdaterad.

---

## Förutsättningar

- Spelaren är inloggad.
- Spelaren befinner sig i kontoinställningarna.

---

## Huvudflöde

1. Spelaren väljer "Ändra kontoinställningar".
2. Systemet visar nuvarande inställningar.
3. Spelaren ändrar önskade fält.
4. Spelaren sparar ändringarna.
5. Systemet validerar de nya värdena.
6. Systemet uppdaterar kontot.
7. Systemet visar en bekräftelse.

---

## Alternativa flöden

### AF-01: Nya värden är ogiltiga
Vid steg 5 uppfyller något fält inte reglerna.

- Systemet markerar fältet och visar vilken regel som inte uppfylls.
- Spelaren korrigerar och sparar igen.

### AF-02: Spelaren avbryter
Vid steg 3–4 avbryter spelaren.

- Inga ändringar sparas.

### AF-03: Ändringen kan inte sparas
Vid steg 6 uppstår ett tekniskt fel.

- Systemet visar ett felmeddelande och behåller de tidigare inställningarna.

---

## Postconditions

**Lyckat:** Kontot är uppdaterat med de nya inställningarna.

**Misslyckat:** Kontot är oförändrat och spelaren har fått information om varför.

---

## Särskilda krav

- Spelarnamn och fritext ska saneras så att skript inte kan köras i andra spelares webbläsare (NFR-07.3).

---

## Öppna frågor

- Ska ändring av e-postadress kräva verifiering av den nya adressen?
