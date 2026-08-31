# UC-25: Välj inloggningsmetod

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-25 |
| Namn | Välj inloggningsmetod |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet |
| Relaterade FR | FR-25.1, FR-25.2, FR-25.3, FR-25.4, FR-25.5 |
| Relaterade NFR | NFR-07.1, NFR-07.3, NFR-06.1 |

---

## Beskrivning

Spelaren vill logg in på sitt konto och väljer mellan de olika inloggninsmetoder som systemet erbjuder (t.ex. e-post/lösenord eller inloggning via Google).

---

## Förutsättningar

- Spelaren befinner sig på inloggningssidan.
- Spelaren är inte i aktiv session.

---

## Huvudflöde

1. Spelaren navigerar till inloggningssidan.
2. Systemet visar dem tillgängliga inloggningsmetoderna.
3. Spelaren väjer en av metoderna.
4. Systemet tar spelaren till den valda inloggningsmetodens flöde.
5. Inloggningsflödet genomförs (UC-22 för e-post, UC-24 för tillagd social inloggning).
6. Systemet uppdaterar spelarens session.
7. Systemet skickar spelaren till huvumenyn eller platsen där spelaren var innan inloggning.

---

## Alternativa flöden

### AF-01: Metod är otillgänglig

Vid steg 3 är någon/några metoder nere.

- Systemet visar ett meddelande om att metoden för närvarande är otillgänglig.
- Spelaren kan välja annan metod eller avbryta.

---

## Postconditions

Lyckat: Spelaren är inloggad och har en giltig session.

Misslyckat: Spelaren förblir utloggad på inloggningssidan.

---

## Särskilda krav

- Ska uppfylla NFR-07.3 och NFR-07.1 genom att aldrig avslöja vilka metoder som är kopplade till vilka konton vid felaktiga inloggningsförsök.

---

## Öppna frågor

- Ska systemet komma ihåg vilken metod spelaren använde sist och prioritera den?


