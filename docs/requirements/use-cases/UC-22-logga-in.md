# UC-22: Logga in

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-22 |
| Namn | Logga in |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet, Databasen |
| Relaterade FR | FR-xx (Konto och inloggning) |
| Relaterade NFR | NFR-07.1, NFR-07.4 |

---

## Beskrivning

Spelaren loggar in på sitt konto med e-postadress och lösenord för att få tillgång till sina kontofunktioner.

---

## Förutsättningar

- Spelaren har ett konto (UC-21).
- Spelaren befinner sig på inloggningssidan.

---

## Huvudflöde

1. Spelaren anger e-postadress och lösenord.
2. Systemet validerar uppgifterna mot kontot.
3. Systemet skapar en session för spelaren.
4. Systemet för spelaren till huvudmenyn.
5. Systemet visar att spelaren är inloggad.

---

## Alternativa flöden

### AF-01: Fel e-postadress eller lösenord
Vid steg 2 matchar inte uppgifterna.

- Systemet visar ett generiskt felmeddelande utan att avslöja vilket fält som var fel.
- Spelaren kan försöka igen.

### AF-02: Kontot är låst
Vid steg 2 är kontot tillfälligt låst (t.ex. efter flera misslyckade försök).

- Systemet meddelar spelaren och anger när kontot kan användas igen.

### AF-03: Inloggningen kan inte genomföras
Vid steg 2 uppstår ett tekniskt fel.

- Systemet visar ett felmeddelande med möjlighet att försöka igen.

---

## Postconditions

**Lyckat:** Spelaren är inloggad med en giltig session.

**Misslyckat:** Spelaren förblir utloggad och har fått information om varför.

---

## Särskilda krav

- All kommunikation ska ske över TLS 1.2 eller senare (NFR-07.1).

---

## Öppna frågor

- Ska systemet erbjuda "kom ihåg mig" (långvarig session)?
