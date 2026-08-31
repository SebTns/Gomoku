# UC-15: Förlust

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-15 |
| Namn | Förlust |
| Version | 1.0 |
| Primär aktör | Systemet |
| Sekundär aktör | Spelaren, Motståndaren |
| Relaterade FR | FR-08.9, FR-08.10, FR-08.13 |
| Relaterade NFR | NFR-02.4, NFR-04.6 |

---

## Beskrivning

Partiet avslutas med förlust för spelaren när motståndaren får fem i rad (eller när spelaren ger upp), varvid förlusten registreras och förlustmeddelandet visas.

---

## Förutsättningar

- Ett parti pågår.
- Motståndaren har fyra stenar i rad med öppen förlängning, eller spelaren ger upp (UC-11).

---

## Huvudflöde

1. Motståndaren gör ett drag (→ UC-09) eller spelaren ger upp (→ UC-11).
2. Systemet kontrollerar om motståndaren har fem i rad.
3. Systemet konstaterar fem i rad för motståndaren.
4. Systemet avslutar partiet och registrerar förlust för spelaren.
5. Systemet markerar den vinnande raden visuellt.
6. Systemet visar förlustmeddelandet i resultatvyn.
7. Systemet förhindrar ytterligare drag.

---

## Alternativa flöden

### AF-01: Spelaren ger upp i stället
Vid steg 1 väljer spelaren "Ge upp".

- Förlusten registreras utan att fem i rad kontrolleras (→ UC-11).

---

## Postconditions

**Lyckat:** Förlusten är registrerad, förlustmeddelandet visas och partiet är avslutat.

**Misslyckat:** Partiet fortsätter utan att förlust registreras.

---

## Särskilda krav

- Kontrollen av fem i rad ska vara klar inom 100 ms efter varje drag (NFR-02.4).
- Resultatvyn ska erbjuda minst en väg vidare (NFR-04.6).

---

## Öppna frågor

- Ska förlusten visas med en kort förklaring (t.ex. "fem i rad för motståndaren")?
