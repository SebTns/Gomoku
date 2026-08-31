# UC-14: Oavgjort

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-14 |
| Namn | Oavgjort |
| Version | 1.0 |
| Primär aktör | Systemet |
| Sekundär aktör | Spelarna |
| Relaterade FR | FR-08.11 |
| Relaterade NFR | NFR-02.4, NFR-08.2 |

---

## Beskrivning

Partiet avslutas som oavgjort när spelplanen är full utan att någon spelare har fått fem i rad.

---

## Förutsättningar

- Ett parti pågår.
- Det finns endast en ledig skärningspunkt kvar (eller färre).

---

## Huvudflöde

1. En spelare gör ett drag som fyller den sista lediga skärningspunkten.
2. Systemet kontrollerar om någon har fem i rad.
3. Systemet konstaterar att ingen har fem i rad.
4. Systemet avslutar partiet med status `OAVGJORT`.
5. Systemet visar ett meddelande om oavgjort i resultatvyn.
6. Systemet förhindrar ytterligare drag.

---

## Alternativa flöden

### AF-01: Sista draget ger fem i rad
Vid steg 2 ger sista draget fem i rad.

- Partiet avslutas som vinst i stället för oavgjort (→ UC-15, UC-16).

---

## Postconditions

**Lyckat:** Partiet är avslutat som oavgjort och resultatet visas.

**Misslyckat:** Inget oavgjort resultat registreras (partiet fortsätter eller avgörs som vinst).

---

## Särskilda krav

- Kontrollen av fem i rad ska vara klar inom 100 ms efter varje drag (NFR-02.4).
- Partiet ska aldrig hamna i ett tillstånd utan giltiga drag (NFR-08.2).

---

## Öppna frågor

- Ska oavgjort även kunna uppstå genom ömsesidig överenskommelse?
