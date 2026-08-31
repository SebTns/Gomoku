# UC-NFR-01: Ge samtycke till cookie

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-NFR-01 |
| Namn | Ge samtycke till cookie |
| Version | 1.0 |
| Primär aktör | Besökare |
| Sekundär aktör | Systemet |
| Relaterade FR | FR-xx (Icke-funktionella krav) |
| Relaterade NFR | NFR-07.4 |

---

## Beskrivning

Besökaren ger eller nekar samtycke till cookies vid första besöket, i enlighet med gällande regler för dataskydd.

---

## Förutsättningar

- Besökaren öppnar applikationen för första gången (eller efter att tidigare val har rensats).

---

## Huvudflöde

1. Systemet visar ett meddelande om cookies vid första besöket.
2. Systemet förklarar vilka cookies som används och varför.
3. Besökaren väljer "Acceptera alla", "Acceptera nödvändiga" eller gör egna val.
4. Systemet sparar besökarens val.
5. Systemet laddar endast cookies enligt valet.
6. Systemet visar inte meddelandet igen vid nästa besök.

---

## Alternativa flöden

### AF-01: Besökaren gör inget val
Vid steg 3 stänger besökaren meddelandet utan att välja.

- Systemet behandlar det som nekande av icke-nödvändiga cookies.

### AF-02: Besökaren vill ändra sitt val
Vid ett senare besök vill besökaren ändra sitt tidigare val.

- Systemet erbjuder "Cookie-inställningar" där valet kan ändras.

---

## Postconditions

**Lyckat:** Besökarens val är sparat och cookies hanteras därefter.

**Misslyckat:** Inget val är sparat (endast nödvändiga cookies används).

---

## Särskilda krav

- Systemet ska inte samla in fler personuppgifter än nödvändigt (NFR-07.4).

---

## Öppna frågor

- Vilka cookies krävs egentligen för spelet (session, sparade namn, inställningar)?
