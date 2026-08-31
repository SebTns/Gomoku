# UC-11: Ge upp

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-11 |
| Namn | Ge upp |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet |
| Relaterade FR | FR-xx (Partiavslut och resultat) |
| Relaterade NFR | NFR-04.1, NFR-04.6 |

---

## Beskrivning

Spelaren avslutar ett pågående parti i förtid genom att ge upp, vilket registrerar en förlust för spelaren och en vinst för motståndaren.

---

## Förutsättningar

- Ett parti pågår.
- Det är spelarens tur eller motståndarens tur.

---

## Huvudflöde

1. Spelaren väljer "Ge upp".
2. Systemet begär bekräftelse.
3. Spelaren bekräftar.
4. Systemet avslutar partiet med status `AVSLUTAT`.
5. Systemet registrerar förlust för spelaren och vinst för motståndaren.
6. Systemet visar resultatvyn med vinnare och förlorare.
7. Systemet förhindrar ytterligare drag.

---

## Alternativa flöden

### AF-01: Spelaren ångrar sig
Vid steg 3 väljer spelaren "Avbryt".

- Partiet fortsätter som tidigare utan att något registreras.

### AF-02: Partiet är redan avslutat
Vid steg 1 har partiet redan avgjorts.

- Systemet avvisar "Ge upp" och visar resultatvyn.

---

## Postconditions

**Lyckat:** Partiet är avslutat och resultatet (förlust/vinst) är registrerat och synligt.

**Misslyckat:** Partiet fortsätter oförändrat.

---

## Särskilda krav

- Felmeddelanden och bekräftelseförfrågningar ska vara på svenska (NFR-04.1).
- Spelaren ska alltid ha en väg vidare från resultatvyn (NFR-04.6).

---

## Öppna frågor

- Ska det finnas en tidsgräns innan "Ge upp" är tillgängligt (t.ex. tidigast efter 5 drag)?
