# UC-24: Lägg till inloggningsmetod

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-24 |
| Namn | Lägg till inloggningsmetod |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet, Extern identitetsleverantör (t.ex. Google) |
| Relaterade FR | FR-xx (Konto och inloggning) |
| Relaterade NFR | NFR-07.1 |

---

## Beskrivning

Spelaren kopplar en ytterligare inloggningsmetod (t.ex. inloggning via Google) till sitt konto, så att hen kan logga in på fler sätt.

---

## Förutsättningar

- Spelaren är inloggad.
- Spelaren befinner sig i kontoinställningarna.

---

## Huvudflöde

1. Spelaren väljer "Lägg till inloggningsmetod".
2. Systemet visar tillgängliga metoder.
3. Spelaren väljer en metod (t.ex. Google).
4. Systemet skickar spelaren till den externa leverantörens flöde.
5. Spelaren godkänner kopplingen hos leverantören.
6. Systemet kopplar metoden till kontot.
7. Systemet visar en bekräftelse med de metoder som nu är kopplade.

---

## Alternativa flöden

### AF-01: Metoden är redan kopplad
Vid steg 3 är metoden redan kopplad till kontot.

- Systemet informerar spelaren och lägger inte till den igen.

### AF-02: Leverantören nekar kopplingen
Vid steg 5 godkänner inte leverantören.

- Systemet informerar spelaren och behåller befintliga metoder oförändrade.

### AF-03: Spelaren avbryter
Vid steg 4–5 avbryter spelaren flödet.

- Ingen metod läggs till.

---

## Postconditions

**Lyckat:** Den nya inloggningsmetoden är kopplad till kontot.

**Misslyckat:** Kontot är oförändrat och spelaren har fått information om varför.

---

## Särskilda krav

- All kommunikation ska ske över TLS 1.2 eller senare (NFR-07.1).

---

## Öppna frågor

- Ska spelaren kunna ta bort en inloggningsmetod, och krävs det att minst en metod alltid finns kvar?
