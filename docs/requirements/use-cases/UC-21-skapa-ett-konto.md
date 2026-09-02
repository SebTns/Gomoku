# UC-21: Skapa ett konto

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-21 |
| Namn | Skapa ett konto |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet, Databasen |
| Relaterade FR | FR-13.1, FR-13.2, FR-13.3, FR-13.4, FR-13.5 |
| Relaterade NFR | NFR-07.1, NFR-07.4 |

---

## Beskrivning

Spelaren registrerar ett konto med namn, e-postadress och lösenord för att få tillgång till kontofunktioner som historik och sparade partier.

---

## Förutsättningar

- Spelaren befinner sig på startsidan.
- Spelaren har inget befintligt konto med samma e-postadress.

---

## Huvudflöde

1. Spelaren väljer "Skapa konto".
2. Systemet visar registreringsformuläret.
3. Spelaren anger synligt namn, e-postadress och lösenord.
4. Systemet validerar uppgifterna (format, längd, lösenordsregler).
5. Systemet kontrollerar att e-postadressen inte redan är registrerad.
6. Systemet skapar kontot.
7. Systemet visar en bekräftelse.
8. Spelaren loggas in eller förs vidare till inloggning.

---

## Alternativa flöden

### AF-01: E-postadressen är redan registrerad
Vid steg 5 finns e-postadressen sedan tidigare.

- Systemet meddelar spelaren och erbjuder inloggning i stället.

### AF-02: Uppgifterna uppfyller inte kraven
Vid steg 4 är något fält ogiltigt.

- Systemet markerar fältet och visar vilken regel som inte uppfylls.
- Spelaren korrigerar och skickar igen.

### AF-03: Spelaren avbryter
Vid steg 3 väljer spelaren "Avbryt".

- Inget konto skapas och spelaren återgår till startsidan.

---

## Postconditions

**Lyckat:** Kontot är skapat och spelaren kan logga in.

**Misslyckat:** Inget konto har skapats och spelaren har fått information om varför.

---

## Särskilda krav

- All kommunikation ska ske över TLS 1.2 eller senare (NFR-07.1).
- Systemet ska inte samla in fler personuppgifter än nödvändigt (NFR-07.4).

---

## Öppna frågor

- Ska e-postadressen verifieras (t.ex. via bekräftelselänk) innan kontot aktiveras?
