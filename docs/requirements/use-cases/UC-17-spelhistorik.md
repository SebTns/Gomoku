# UC-17: Spelhistorik

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-17 |
| Namn | Spelhistorik |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet, Databasen |
| Relaterade FR | FR-xx (Spelhistorik och sparade partier) |
| Relaterade NFR | NFR-07.5 |

---

## Beskrivning

Spelaren visar sin spelhistorik med tidigare partier, inklusive datum, motståndare och resultat.

---

## Förutsättningar

- Spelaren har öppnat spelet.
- Spelaren har ett konto eller en lokal profil med sparad historik.

---

## Huvudflöde

1. Spelaren väljer "Spelhistorik".
2. Systemet hämtar spelarens avslutade partier.
3. Systemet visar en lista med datum, motståndare, brädstorlek och resultat.
4. Spelaren kan välja ett parti för att se detaljer.
5. Spelaren återgår till menyn.

---

## Alternativa flöden

### AF-01: Ingen historik finns
Vid steg 3 finns inga avslutade partier.

- Systemet visar en tom lista med en kort förklaring.

### AF-02: Historiken kan inte hämtas
Vid steg 2 misslyckas hämtningen.

- Systemet visar ett felmeddelande med möjlighet att försöka igen.

---

## Postconditions

**Lyckat:** Spelaren har sett sin spelhistorik.

**Misslyckat:** Spelaren har fått ett felmeddelande och kan försöka igen.

---

## Särskilda krav

- Partidata för gästspel ska raderas senast 30 dagar efter avslutat parti (NFR-07.5).

---

## Öppna frågor

- Ska historiken kräva inloggning eller även finnas i gästläge (lokalt)?
