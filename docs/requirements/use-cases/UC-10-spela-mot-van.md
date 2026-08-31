# UC-10: Spela mot vän

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-10 |
| Namn | Spela mot vän |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Vännen, Systemet |
| Relaterade FR | FR-07.5, FR-07.8, FR-07.9, FR-08.1, FR-08.4 |
| Relaterade NFR | NFR-02.6, NFR-04.2, NFR-04.3, NFR-07.2 |

---

## Beskrivning

Spelaren spelar ett parti i realtid mot en vän online, där båda spelarnas drag synkroniseras via systemet tills partiet avslutas.

---

## Förutsättningar

- Spelaren har skapat en inbjudan (UC-03) och vännen har anslutit.
- Båda spelarna har en giltig session.

---

## Huvudflöde

1. Systemet startar partiet när båda spelarna har anslutit.
2. Systemet visar båda spelarnas namn och färger.
3. Spelarna gör drag i tur och ordning (→ UC-02, UC-09).
4. Systemet synkroniserar varje drag till båda spelarna.
5. Systemet kontrollerar efter varje drag om partiet är avgjort.
6. Vid vinst, förlust eller oavgjort avslutas partiet (→ UC-14, UC-15, UC-16).

---

## Alternativa flöden

### AF-01: Vännen kopplas från
Vid steg 3–4 förlorar vännen anslutningen.

- Systemet upptäcker frånkopplingen inom 15 sekunder och meddelar spelaren.
- Partiet pausas och tillåter återanslutning inom 5 minuter.

### AF-02: En tredje part försöker ansluta
Vid steg 1 försöker ytterligare en spelare ansluta till partiet.

- Systemet avvisar anslutningsförsöket (partiet är begränsat till två spelare).

### AF-03: Spelaren lämnar partiet
Vid steg 3–4 avslutar spelaren partiet i förtid.

- Partiet avslutas och vännen informeras (→ UC-12).

---

## Postconditions

**Lyckat:** Partiet har genomförts med synkroniserade drag och avslutats med ett resultat.

**Misslyckat:** Partiet har avbrutits och båda spelarna har informerats.

---

## Särskilda krav

- Ett drag ska synas hos motståndaren inom 500 ms (NFR-02.6).
- Inbjudningskoder ska vara oförutsägbara (NFR-07.2).

---

## Öppna frågor

- Ska spelarna kunna se varandras markörer eller chatta under partiet?
