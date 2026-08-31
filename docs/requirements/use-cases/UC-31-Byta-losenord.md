# UC-31: Byta lösenord

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-31 |
| Namn | Byta lösenord |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet, Databasen |
| Relaterade FR | FR-xx (Konto och inloggning) |
| Relaterade NFR | NFR-07.1 |

---

## Beskrivning

Spelaren byter lösenord på sitt konto för att välja ett nytt, säkrare lösenord.

---

## Förutsättningar

- Spelaren är inloggad.
- Spelaren befinner sig i kontoinställningarna.

---

## Huvudflöde

1. Spelaren väljer "Byta lösenord".
2. Systemet visar formuläret med nuvarande lösenord, nytt lösenord och upprepning av nytt lösenord.
3. Spelaren fyller i formuläret.
4. Systemet validerar det nuvarande lösenordet.
5. Systemet validerar att det nya lösenordet uppfyller reglerna och matchar upprepningen.
6. Systemet uppdaterar lösenordet.
7. Systemet visar en bekräftelse.

---

## Alternativa flöden

### AF-01: Fel nuvarande lösenord
Vid steg 4 stämmer inte det nuvarande lösenordet.

- Systemet avvisar och ber spelaren försöka igen.

### AF-02: Nytt lösenord uppfyller inte kraven
Vid steg 5 uppfyller det nya lösenordet inte reglerna eller matchar inte upprepningen.

- Systemet visar vilken regel som inte uppfylls.
- Spelaren korrigerar och skickar igen.

### AF-03: Spelaren avbryter
Vid steg 3 avbryter spelaren.

- Lösenordet ändras inte.

---

## Postconditions

**Lyckat:** Lösenordet är ändrat och spelaren kan logga in med det nya lösenordet.

**Misslyckat:** Lösenordet är oförändrat och spelaren har fått information om varför.

---

## Särskilda krav

- All kommunikation ska ske över TLS 1.2 eller senare (NFR-07.1).

---

## Öppna frågor

- Ska spelaren loggas ut från andra enheter när lösenordet ändras?
