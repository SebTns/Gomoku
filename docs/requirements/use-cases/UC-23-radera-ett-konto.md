# UC-23: Radera ett konto

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-23 |
| Namn | Radera ett konto |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet, Databasen |
| Relaterade FR | FR-xx (Konto och inloggning) |
| Relaterade NFR | NFR-07.4 |

---

## Beskrivning

Spelaren raderar sitt konto permanent, varvid kontouppgifter och tillhörande data tas bort.

---

## Förutsättningar

- Spelaren är inloggad.
- Spelaren befinner sig i kontoinställningarna.

---

## Huvudflöde

1. Spelaren väljer "Radera konto".
2. Systemet visar information om vad raderingen innebär.
3. Systemet begär bekräftelse (t.ex. lösenord eller skriv "RADERA").
4. Spelaren bekräftar.
5. Systemet raderar kontot och tillhörande data.
6. Systemet loggar ut spelaren.
7. Systemet visar en bekräftelse på att kontot är raderat.

---

## Alternativa flöden

### AF-01: Spelaren ångrar sig
Vid steg 4 avbryter spelaren.

- Kontot behålls oförändrat.

### AF-02: Raderingen misslyckas
Vid steg 5 uppstår ett tekniskt fel.

- Systemet informerar spelaren om att kontot inte har raderats.
- Spelaren kan försöka igen.

### AF-03: Fel lösenord
Vid steg 3 (om lösenord krävs) är lösenordet fel.

- Systemet avvisar bekräftelsen och ber spelaren försöka igen.

---

## Postconditions

**Lyckat:** Kontot är raderat och spelaren är utloggad.

**Misslyckat:** Kontot finns kvar och spelaren har fått information om varför.

---

## Särskilda krav

- Systemet ska inte samla in fler personuppgifter än nödvändigt (NFR-07.4).

---

## Öppna frågor

- Ska spelhistorik för raderade konton anonymiseras eller raderas helt?
