# UC-NFR-05: Ta bort konto (GDPR-självbetjäning)

| Fält | Värde |
|-------|-------|
| **Användningsfalls-ID** | UC-NFR-05 |
| **Namn** | Ta bort konto |
| **Version** | 1.0 |
| **Primär aktör** | Registrerad spelare |
| **Sekundära aktörer** | E-posttjänst |
| **Relaterade FR** | FR-15.1 – FR-15.5, FR-30.1 – FR-30.13 |
| **Relaterade NFR** | NFR-12.1 – NFR-12.7, NFR-07.1 |
| **Kopplade begränsningar** | SR-03.1, SR-03.2, SR-03.4 |
| **GDPR-referens** | Artikel 17 |
| **Relaterade AC** | AC-NFR-04-01 – AC-NFR-04-09 (raderingsdelen) |

## Beskrivning
En registrerad spelare tar bort sitt konto permanent och utlöser fullständig radering av alla tillhörande personuppgifter. Detta är GDPR-ramverket för kontoborttagningsflödet; de detaljerade interaktionsstegen specificeras i UC-23 (Radera ett konto).

## Förutsättningar
- Användaren är inloggad.

## Huvudflöde (grundläggande sökväg)

1. Användaren navigerar till **"Account Settings"** → **"Privacy & Data"** → **"Delete Account"**.

2. Systemet visar en otvetydig varning om att borttagning av konto:
- Är **irreversibel** (FR-15.3)
- Kommer att radera alla personuppgifter inom 30 dagar (NFR-12.2, SR-03.2)
- Kommer att anonymisera historiska spelposter
3. Användaren anger sitt lösenord och klickar på **"Delete My Account"** (steg 1 av 2).

4. Systemet skickar ett bekräftelsemejl med en tidsbegränsad länk.
5. Användaren klickar på bekräftelselänken i e-postmeddelandet (steg 2 av 2).
6. Systemet inaktiverar kontot omedelbart.
7. Systemet skapar `DataRequest` (typ: RADERA, status: PÅGÅR).
8. Systemet utlöser raderingsprocessen (→ UC-NFR-04).
9. Systemet skickar e-postmeddelande om fullständig radering efter fullständig radering.

## Eftervillkor
- Konto inaktiverat.
- Radering schemalagd och slutförd inom 30 dagar.
- Användaren kan inte logga in eller återställa kontot efter e-postbekräftelse.

## Testkriterier (verifiering av NFR-12 och FR-15)
- Raderingsalternativet finns och är tillgängligt i kontoinställningarna.
- Processen kräver minst två distinkta bekräftelsesteg (lösenord + e-postlänk).
- Tydlig varning om oåterkallelighet visas före det första bekräftelsesteget.
- Kontot kan inte nås efter e-postbekräftelse.
- Raderingen slutförs inom 30 dagar.
- E-postmeddelande om fullständig radering skickas när raderingen är klar.
## Ändringslogg

**1.1** — Fyllde i de tomma fälten `NFR-`. Filen hänvisade till NFR-07.9 och till "UC-18 (Ta bort
konto)". Båda numren kommer från lärarens referensrepo `miwashi-edu/gomoku`, där NFR-07 är
uppdelat i GDPR-underkrav och UC-18 är Delete Account. I detta repo är NFR-07 *Säkerhet och
dataskydd* med fem underkrav, och UC-18 är *Spela multiplayer lokalt*. Rätt referenser här är
UC-23 (Radera ett konto), FR-15 och NFR-12 (Radering av personuppgifter), som skapades för
ändamålet.
