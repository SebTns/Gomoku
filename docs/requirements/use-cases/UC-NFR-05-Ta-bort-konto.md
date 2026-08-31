# UC-NFR-05: Ta bort konto (GDPR-självbetjäning)

| Fält | Värde |
|-------|-------|
| **Användningsfalls-ID** | UC-NFR-05 |
| **Namn** | Ta bort konto |
| **Version** | 1.0 |
| **Primär aktör** | Registrerad spelare |
| **Sekundära aktörer** | E-posttjänst |
| **Relaterad NFR** | NFR- |
| **GDPR-referens** | Artikel 17 |

## Beskrivning
En registrerad spelare tar bort sitt konto permanent och utlöser fullständig radering av alla tillhörande personuppgifter. Detta är GDPR-ramverket för kontoborttagningsflödet; de detaljerade interaktionsstegen specificeras i UC-18 (Ta bort konto).

## Förutsättningar
- Användaren är inloggad.

## Huvudflöde (grundläggande sökväg)

1. Användaren navigerar till **"Kontoinställningar"** → **"Sekretess och data"** → **"Radera konto"**.

2. Systemet visar en otvetydig varning om att borttagning av konto:
- Är **irreversibel** (NFR-)
- Kommer att radera alla personuppgifter inom 30 dagar (NFR-)
- Kommer att anonymisera historiska spelposter
3. Användaren anger sitt lösenord och klickar på **"Radera mitt konto"** (steg 1 av 2).

4. Systemet skickar ett bekräftelsemejl med en tidsbegränsad länk.
5. Användaren klickar på bekräftelselänken i e-postmeddelandet (steg 2 av 2).
6. Systemet inaktiverar kontot omedelbart.
7. Systemet skapar `DataRequest` (typ: RADERA, status: PÅGÅR).
8. Systemet utlöser raderingsprocessen (→ UC-NFR-).
9. Systemet skickar e-postmeddelande om fullständig radering efter fullständig radering.

## Eftervillkor
- Konto inaktiverat.
- Radering schemalagd och slutförd inom 30 dagar.
- Användaren kan inte logga in eller återställa kontot efter e-postbekräftelse.

## Testkriterier (NFR-07.9-verifiering)
- Raderingsalternativet finns och är tillgängligt i kontoinställningarna.
- Processen kräver minst två distinkta bekräftelsesteg (lösenord + e-postlänk).
- Tydlig varning om oåterkallelighet visas före det första bekräftelsesteget.
- Kontot kan inte nås efter e-postbekräftelse.
- Raderingen slutförs inom 30 dagar.
- E-postmeddelande om fullständig radering skickas när raderingen är klar.