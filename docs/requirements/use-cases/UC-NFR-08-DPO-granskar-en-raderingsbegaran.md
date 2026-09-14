# UC-NFR-08: Dataskyddsombudet granskar en raderingsbegäran

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-NFR-08 |
| **Namn** | Dataskyddsombudet granskar en raderingsbegäran |
| **Version** | 1.0 |
| **Primär aktör** | Dataskyddsombud (DPO) |
| **Sekundär aktör** | Administratör, E-posttjänst |
| **Relaterade FR** | FR-32.1 – FR-32.8 |
| **Relaterade NFR** | NFR-12.2, NFR-12.6, NFR-07.1 |
| **Kopplade begränsningar** | SR-03.1, SR-03.2, SR-03.4 |
| **GDPR-referens** | Artikel 17, artikel 39 |
| **Relaterade AC** | AC-NFR-08-01 – AC-NFR-08-05 |

## Beskrivning
Dataskyddsombudet granskar raderingsbegäranden som inte kan hanteras automatiskt — en begäran som
riskerar att missa 30-dagarsgränsen, eller där en rättslig skyldighet hindrar fullständig radering
— och dokumenterar beslutet.

> **Varför detta användningsfall finns.** Dataskyddsombudet stod som primär aktör i
> `01-inledning.md` utan att äga ett enda användningsfall. UC-NFR-04 skickar två eskaleringar till
> DPO (AF-01 och AF-02) men beskriver aldrig vad som händer på andra sidan. Flödet fanns alltså i
> systemet men inte i dokumentationen.

## Förutsättningar
- Dataskyddsombudet är inloggat med flerfaktorsautentisering.
- Det finns minst en raderingsbegäran som har eskalerats enligt UC-NFR-04 AF-01 eller AF-02.

## Huvudflöde

1. Dataskyddsombudet öppnar listan över eskalerade raderingsbegäranden.
2. Systemet visar varje begäran med begärande-ID, mottagningsdatum, kvarvarande tid till
   30-dagarsgränsen och orsaken till eskaleringen.
3. Dataskyddsombudet öppnar en begäran.
4. Systemet visar vilka datakategorier som är raderade, vilka som är anonymiserade och vilka som
   är kvar.
5. Dataskyddsombudet bedömer om en kvarvarande kategori omfattas av en rättslig
   lagringsskyldighet.
6. Dataskyddsombudet registrerar beslutet med rättslig grund och en motivering.
7. Systemet registrerar beslutet med tidpunkt och vilket dataskyddsombud som fattade det.
8. Systemet underrättar den registrerade spelaren om utfallet.
9. Systemet uppdaterar begärans status.

## Alternativa flöden

### AF-01: Förseningen kan åtgärdas
Vid steg 5 finns ingen rättslig grund för att behålla uppgifterna — förseningen är teknisk.
- Dataskyddsombudet begär att raderingen slutförs.
- Systemet återupptar raderingen (→ UC-NFR-04 steg 4).
- Begärans status återgår till PÅGÅENDE.

### AF-02: Begäran kan inte bedömas utan mer underlag
Vid steg 5 saknar dataskyddsombudet uppgifter för att kunna avgöra frågan.
- Dataskyddsombudet begär underlag från administratören.
- Begäran markeras som avvaktande med en tidsfrist.
- 30-dagarsgränsen fortsätter löpa, och systemet varnar när det återstår 5 dagar.

### AF-03: 30-dagarsgränsen har redan passerats
Vid steg 2 har en begäran passerat gränsen utan beslut.
- Systemet markerar begäran som försenad.
- Dataskyddsombudet dokumenterar orsaken för efterlevnadsgranskningen.
- Avvikelsen bevaras enligt SR-03.4.

## Postconditions

**Lyckat:** Begäran har ett registrerat beslut med rättslig grund och beslutsfattare. Spelaren är
underrättad. Begärans status är uppdaterad.

**Misslyckat:** Begäran saknar beslut, är markerad som försenad och avvikelsen är dokumenterad.

## Särskilda krav
- Åtkomst till personuppgifter ska kräva flerfaktorsautentisering (NFR-07.1, SR-03.3).
- Beslut ska bevaras i minst 3 år i anonymiserad form (NFR-12.6, SR-03.4).
- Granskningen ska gå att genomföra i testmiljö utan att 30 dagar förflyter (NFR-12.7).

## Öppna frågor
- Ska dataskyddsombudet kunna se den registrerades personuppgifter för att fatta beslutet, eller
  bara datakategorierna? Att visa uppgifterna motverkar syftet med raderingen, men att dölja dem
  kan göra beslutet omöjligt att fatta. Frågan är inte avgjord.
- Vem granskar dataskyddsombudets egna beslut?
- Ska samma flöde användas för begäranden om åtkomst (UC-NFR-02), eller behövs ett eget?
