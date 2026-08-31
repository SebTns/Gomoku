# UC-12: Avsluta ett parti

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-12 |
| Namn | Avsluta ett parti |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet, Motståndaren |
| Relaterade FR | FR-xx (Partiavslut och resultat) |
| Relaterade NFR | NFR-04.2, NFR-04.6, NFR-08.2 |

---

## Beskrivning

Spelaren avslutar ett pågående parti i förtid (utan att ge upp), vilket sparar partistatusen korrekt och återför spelaren till menyn.

---

## Förutsättningar

- Ett parti pågår.
- Spelaren vill lämna partiet innan det är avgjort.

---

## Huvudflöde

1. Spelaren väljer "Avsluta parti".
2. Systemet begär bekräftelse.
3. Spelaren bekräftar.
4. Systemet sparar partistatusen (positioner, tur, inställningar) innan avslut.
5. Systemet avslutar partiet med status `AVSLUTAT`.
6. Systemet återför spelaren till menyn.
7. Motståndaren informeras om att partiet har avslutats.

---

## Alternativa flöden

### AF-01: Spelaren ångrar sig
Vid steg 3 väljer spelaren "Avbryt".

- Partiet fortsätter som tidigare.

### AF-02: Statusen kan inte sparas
Vid steg 4 misslyckas sparandet.

- Systemet visar ett felmeddelande och behåller spelaren i partiet.
- Spelaren kan försöka igen eller avbryta.

### AF-03: Spelaren stänger webbläsaren
Vid valfritt steg stängs webbläsaren.

- Partitillståndet ska bevaras så att partiet kan återupptas vid återanslutning (NFR-04.2).

---

## Postconditions

**Lyckat:** Partiet är avslutat, statusen är sparad och spelaren är tillbaka i menyn.

**Misslyckat:** Partiet fortsätter och spelaren har fått ett felmeddelande.

---

## Särskilda krav

- Partitillståndet ska bevaras vid sidomladdning eller nätverksavbrott (NFR-04.2).
- Ett parti ska aldrig hamna i ett tillstånd där ingen kan göra ett giltigt drag (NFR-08.2).

---

## Öppna frågor

- Ska ett avslutat parti vara återupptagbart (→ UC-26, UC-27) eller betraktas som förlorat?
