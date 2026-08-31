# UC-20: Visa spelregler

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-20 |
| Namn | Visa spelregler |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet |
| Relaterade FR | FR-01.2 |
| Relaterade NFR | NFR-06.6 |

---

## Beskrivning

Spelaren läser en kort regelsammanfattning för Gomoku i spelet, så att en ny spelare förstår hur man vinner.

---

## Förutsättningar

- Spelaren har öppnat spelet och befinner sig på startsidan eller i en meny.

---

## Huvudflöde

1. Spelaren väljer "Visa spelregler".
2. Systemet visar regelsammanfattningen (mål, drag, vinstvillkor, oavgjort).
3. Spelaren läser reglerna.
4. Spelaren stänger reglerna.
5. Systemet återför spelaren till den vy hen kom ifrån.

---

## Alternativa flöden

### AF-01: Reglerna kan inte laddas
Vid steg 2 misslyckas laddningen.

- Systemet visar ett felmeddelande med möjlighet att försöka igen.

### AF-02: Spelaren startar ett parti direkt
Vid steg 3 väljer spelaren "Starta parti" från regelvyn.

- Systemet går vidare till konfigurationsvyn (→ UC-01).

---

## Postconditions

**Lyckat:** Spelaren har tagit del av reglerna och kan återgå till spelet.

**Misslyckat:** Spelaren har fått ett felmeddelande.

---

## Särskilda krav

- En ny spelare ska kunna starta och genomföra ett parti utan extern hjälp inom 2 minuter (NFR-06.6).

---

## Öppna frågor

- Ska reglerna innehålla avancerade tävlingsregler (t.ex. förbjudna drag) eller endast grunderna?
