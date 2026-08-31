# UC-27: Starta sparat parti

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-27 |
| Namn | Starta sparat parti |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet, Databasen |
| Relaterade FR | FR-xx (Spelhistorik och sparade partier) |
| Relaterade NFR | NFR-04.2 |

---

## Beskrivning

Spelaren återupptar ett tidigare sparat parti från den punkt där det avbröts.

---

## Förutsättningar

- Spelaren har minst ett sparat parti (UC-26).
- Spelaren är inloggad eller har en lokal profil med sparade partier.

---

## Huvudflöde

1. Spelaren väljer "Sparade partier".
2. Systemet visar en lista över sparade partier.
3. Spelaren väljer ett parti.
4. Systemet laddar partitillståndet.
5. Systemet renderar brädet med alla stenar på rätt positioner.
6. Systemet visar vems tur det är och partikonfigurationen.
7. Spelaren fortsätter partiet (→ UC-02, UC-09).

---

## Alternativa flöden

### AF-01: Inga sparade partier finns
Vid steg 2 finns inga sparade partier.

- Systemet visar en tom lista med en kort förklaring.

### AF-02: Det sparade partiet kan inte laddas
Vid steg 4 är tillståndet korrupt eller från en inkompatibel version.

- Systemet visar ett felmeddelande och behåller spelaren i listan.
- Spelaren kan välja ett annat parti.

### AF-03: Motståndaren är inte tillgänglig
Vid steg 7 gäller partiet en online-motståndare som inte är ansluten.

- Systemet meddelar spelaren och väntar på motståndarens återanslutning.

---

## Postconditions

**Lyckat:** Partiet är återupptaget från rätt position med rätt tur.

**Misslyckat:** Partiet har inte laddats och spelaren har fått information om varför.

---

## Särskilda krav

- Partitillståndet ska kunna återställas korrekt efter avbrott (NFR-04.2).

---

## Öppna frågor

- Ska sparade partier vara tillgängliga i gästläge eller endast för inloggade spelare?
