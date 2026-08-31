# UC-13: Starta ett nytt parti

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-13 |
| Namn | Starta ett nytt parti |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet, Motståndaren |
| Relaterade FR | FR-03.1, FR-03.7 |
| Relaterade NFR | NFR-02.7, NFR-06.6 |

---

## Beskrivning

Efter ett avslutat parti startar spelaren ett nytt parti direkt från resultatvyn, varvid spelplanen återställs till startläge.

---

## Förutsättningar

- Ett parti har avslutats (vinst, förlust, oavgjort eller uppgivet).
- Resultatvyn visas.

---

## Huvudflöde

1. Spelaren väljer "Spela igen" i resultatvyn.
2. Systemet återställer spelplanen till startläge (tomt bräde, svart börjar).
3. Systemet skapar ett nytt parti med status `PÅGÅENDE`.
4. Systemet behåller partikonfigurationen (brädstorlek, motståndare, svårighetsgrad) om inget annat anges.
5. Systemet visar det tomma brädet och vem som börjar.

---

## Alternativa flöden

### AF-01: Spelaren vill ändra inställningar
Vid steg 1 väljer spelaren "Ändra inställningar".

- Systemet visar konfigurationsvyn (→ UC-01).
- Efter bekräftelse startas partiet med de nya inställningarna.

### AF-02: Partiet kan inte skapas
Vid steg 3 misslyckas skapandet.

- Systemet visar ett felmeddelande och spelaren stannar i resultatvyn.
- Spelaren kan försöka igen.

---

## Postconditions

**Lyckat:** Ett nytt parti med tomt bräde har skapats och spelet kan börja.

**Misslyckat:** Inget nytt parti har skapats och spelaren har fått ett felmeddelande.

---

## Särskilda krav

- Ändringar av brädstorlek eller svårighetsgrad ska återspeglas inom 300 ms (NFR-02.7).

---

## Öppna frågor

- Avgränsningen mot UC-01 måste beslutas: ska UC-13 endast täcka "spela igen" med samma inställningar?
