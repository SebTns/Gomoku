# UC-16: Vinst

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-16 |
| Namn | Vinst |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet, Motståndaren |
| Relaterade FR | FR-06.5, FR-08.8, FR-08.9, FR-08.10, FR-08.13 |
| Relaterade NFR | NFR-02.4, NFR-04.6, NFR-06.3 |

---

## Beskrivning

Partiet avslutas med vinst för spelaren när spelaren får fem i rad, varvid vinsten registreras, den vinnande raden markeras och vinstmeddelandet visas.

---

## Förutsättningar

- Ett parti pågår.
- Det är spelarens tur.
- Spelaren har fyra stenar i rad med öppen förlängning.

---

## Huvudflöde

1. Spelaren placerar en sten (→ UC-02).
2. Systemet kontrollerar om spelaren har fem i rad horisontellt, vertikalt eller diagonalt.
3. Systemet konstaterar fem i rad.
4. Systemet avslutar partiet och registrerar vinst för spelaren.
5. Systemet markerar den vinnande raden visuellt.
6. Systemet visar vinstmeddelandet i resultatvyn.
7. Systemet förhindrar ytterligare drag.

---

## Alternativa flöden

### AF-01: Spelarens drag ger ingen vinst
Vid steg 3 har spelaren inte fem i rad.

- Turen går vidare till motståndaren (→ UC-09).

### AF-02: Båda färgerna får fem i rad i samma drag
Vid steg 3 (endast teoretiskt möjligt i vissa varianter) har båda spelarna fem i rad.

- Systemet avgör partiet till förmån för den spelare som gjorde det sista draget.

---

## Postconditions

**Lyckat:** Vinsten är registrerad, vinstmeddelandet visas och partiet är avslutat.

**Misslyckat:** Partiet fortsätter utan att vinst registreras.

---

## Särskilda krav

- Kontrollen av fem i rad ska vara klar inom 100 ms efter varje drag (NFR-02.4).
- Svarta och vita stenar ska gå att skilja åt på mer än enbart färg (NFR-06.3).

---

## Öppna frågor

- Ska vinstraden markeras permanent i resultatvyn eller endast i partiet?
