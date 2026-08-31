# UC-18: Spela multiplayer lokalt

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-18 |
| Namn | Spela multiplayer lokalt |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Vännen (lokal motspelare), Systemet |
| Relaterade FR | FR-04.5, FR-08.1, FR-08.3, FR-08.4 |
| Relaterade NFR | NFR-06.3, NFR-06.5 |

---

## Beskrivning

Två spelare spelar mot varandra på samma enhet (hot-seat) utan internet, där de turas om att göra drag på samma bräde.

---

## Förutsättningar

- Applikationen är öppen.
- Spelaren väljer "Spela mot vän" och anger lokalt läge.

---

## Huvudflöde

1. Spelaren väljer "Spela mot vän" (lokalt läge).
2. Systemet låter båda spelarna ange namn (→ UC-07).
3. Systemet låter spelarna välja färg (→ UC-04).
4. Systemet renderar ett tomt bräde.
5. Spelarna turas om att göra drag på samma enhet (→ UC-02).
6. Systemet kontrollerar efter varje drag om partiet är avgjort.
7. Vid avgjort parti visas resultatvyn (→ UC-14, UC-15, UC-16).

---

## Alternativa flöden

### AF-01: Båda vill ha samma färg
Vid steg 3 vill båda spelarna ha samma färg.

- Systemet låter den spelare som valde först behålla färgen (FR-04.5).

### AF-02: Fel spelare försöker göra drag
Vid steg 5 försöker den spelare som inte har turen göra ett drag.

- Systemet avvisar draget utan att turen byts.

---

## Postconditions

**Lyckat:** Partiet har genomförts på en enhet och avslutats med ett resultat.

**Misslyckat:** Partiet har avbrutits utan resultat.

---

## Särskilda krav

- Svarta och vita stenar ska gå att skilja åt på mer än enbart färg (NFR-06.3).
- Klick- och tryckytor ska vara minst 44 × 44 px på pekskärm (NFR-06.5).

---

## Öppna frågor

- Ska lokalt läge även stödja fler än två spelare (t.ex. lag)?
