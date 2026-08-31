# UC-09: Motståndare gör drag

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-09 |
| Namn | Motståndare gör drag |
| Version | 1.0 |
| Primär aktör | Motståndaren (datorn eller online-motståndaren) |
| Sekundär aktör | Systemet, Spelaren |
| Relaterade FR | FR-06.2, FR-06.3, FR-06.4, FR-06.5, FR-08.4, FR-08.8 |
| Relaterade NFR | NFR-02.3, NFR-02.4, NFR-04.3, NFR-09.3 |

---

## Beskrivning

När det är motståndarens tur genomför motståndaren ett drag som systemet validerar och visar på brädet, varefter turen återgår till spelaren.

---

## Förutsättningar

- Ett parti pågår (UC-01, UC-05 eller UC-10).
- Det är motståndarens tur.

---

## Huvudflöde

1. Systemet fastställer att det är motståndarens tur.
2. Systemet meddelar att motståndaren beräknar sitt drag (om motståndaren är datorn).
3. Motståndaren väljer en ledig skärningspunkt.
4. Systemet validerar att punkten är ledig.
5. Systemet placerar motståndarens sten på brädet.
6. Systemet markerar den senast placerade stenen.
7. Systemet kontrollerar om motståndaren har fem i rad.
8. Om ingen vinst: systemet byter tur till spelaren.
9. Om vinst: partiet avslutas (→ UC-15).

---

## Alternativa flöden

### AF-01: Motståndaren väljer en upptagen punkt
Vid steg 4 är punkten redan upptagen.

- Systemet avvisar draget utan att turen byts.
- Motståndaren väljer en annan punkt.

### AF-02: Motståndarens drag uteblir i tid
Vid steg 3 svarar inte motståndaren inom tillåten tid (gäller online-motståndare).

- Systemet meddelar spelaren att motståndaren inte svarar.
- Spelaren kan välja att vänta eller avsluta partiet.

### AF-03: Motståndaren kopplas från
Vid steg 3 förlorar online-motståndaren anslutningen.

- Systemet upptäcker frånkopplingen och meddelar spelaren.
- Partiet pausas och tillåter återanslutning.

---

## Postconditions

**Lyckat:** Motståndarens sten finns på brädet och det är spelarens tur (eller partiet är avgjort).

**Misslyckat:** Inget drag har registrerats och spelaren har informerats.

---

## Särskilda krav

- Datorns drag ska levereras inom 3 sekunder (NFR-02.3).
- Datorns drag ska kunna återskapas via seed för test (NFR-09.3).

---

## Öppna frågor

- Ska spelaren kunna se motståndarens "tänkande" utöver en indikator (t.ex. markering av kandidatdrag)?
