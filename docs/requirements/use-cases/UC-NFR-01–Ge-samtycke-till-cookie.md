# UC-NFR-01: Ge samtycke till cookie

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-NFR-01 |
| Namn | Ge samtycke till cookie |
| Version | 1.0 |
| Primär aktör | Gästanvändare |
| Sekundär aktör | Tredjepartsleverantör (analystjänst) |
| Relaterade FR | FR-24.1 – FR-24.9 |
| Relaterade NFR | NFR-07.4 |
| Kopplade begränsningar | SR-02.7, SR-03.1 |

---

## Beskrivning

Gästanvändaren ger eller nekar samtycke till cookies vid första besöket, i enlighet med gällande regler för dataskydd.

---

## Förutsättningar

- Gästanvändaren öppnar applikationen för första gången (eller efter att tidigare val har rensats).

---

## Huvudflöde

1. Systemet visar ett meddelande om cookies vid första besöket.
2. Systemet förklarar vilka cookies som används och varför.
3. Gästanvändaren väljer "Acceptera alla", "Acceptera nödvändiga" eller gör egna val.
4. Systemet sparar gästanvändarens val.
5. Systemet laddar endast cookies enligt valet.
6. Systemet visar inte meddelandet igen vid nästa besök.

---

## Alternativa flöden

### AF-01: Gästanvändaren gör inget val
Vid steg 3 stänger besökaren meddelandet utan att välja.

- Systemet behandlar det som nekande av icke-nödvändiga cookies.

### AF-02: Gästanvändaren vill ändra sitt val
Vid ett senare besök vill besökaren ändra sitt tidigare val.

- Systemet erbjuder "Cookie-inställningar" där valet kan ändras.

---

## Postconditions

**Lyckat:** Gästanvändarens val är sparat och cookies hanteras därefter.

**Misslyckat:** Inget val är sparat (endast nödvändiga cookies används).

---

## Särskilda krav

- Systemet ska inte samla in fler personuppgifter än nödvändigt (NFR-07.4).
- Inga analys- eller spårningsskript från tredje part får laddas innan samtycke har lämnats (SR-02.7).

---

## Öppna frågor

- Vilka cookies krävs egentligen för spelet (session, sparade namn, inställningar)?
