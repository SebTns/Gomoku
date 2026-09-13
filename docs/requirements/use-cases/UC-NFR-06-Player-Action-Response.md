# UC-NFR-06: Systemets responstid efter en spelarhandling

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-NFR-06 |
| **Namn** | Systemets responstid efter spelarens handling |
| **Version** | 1.1 |
| **Primär aktör** | Spelare |
| **Sekundär aktör** | — |
| **Relaterade FR** | FR-08.1 – FR-08.6, FR-08.17 |
| **Relaterade NFR** | NFR-02.1 – NFR-02.7 |
| **Relaterade AC** | AC-02-01, AC-02-03, AC-02-04 |

## Beskrivning
Spelaren vill att spelet svarar direkt på en handling, så att det går att spela utan att tveka på
om draget gick igenom. Detta användningsfall beskriver responstiden som krav, inte draget i sig —
draget beskrivs i UC-02.

> **Not om aktören.** Primär aktör var tidigare angiven som "Systemet". Kursens definition är att
> en aktör är en *konsument* av förväntade resultat. Systemet konsumerar ingenting; det är
> spelaren som förväntar sig responsen. Primär aktör är därför Spelare.

## Förutsättningar
- Spelaren befinner sig i ett parti med status `PÅGÅENDE`.
- Spelplanen visas för spelaren.
- Det är spelarens tur att göra ett drag.

## Huvudflöde

1. Spelaren väljer en ledig skärningspunkt på spelplanen.
2. Systemet registrerar spelarens handling.
3. Systemet uppdaterar spelplanen och visar resultatet av handlingen inom 100 ms (NFR-02.2).
4. Systemet kontrollerar vinstvillkoret inom 100 ms efter draget (NFR-02.4).
5. Systemet byter tur till nästa spelare.

## Alternativa flöden

### AF-01: Punkten är upptagen
Vid steg 1 väljer spelaren en upptagen skärningspunkt.
- Systemet avvisar handlingen inom 100 ms.
- Turen ligger kvar hos spelaren.

### AF-02: Det är inte spelarens tur
Vid steg 1 försöker spelaren placera en sten när det inte är spelarens tur.
- Systemet avvisar handlingen inom 100 ms.
- Spelordningen är oförändrad.

### AF-03: Motståndaren är datorn
Vid steg 5 är det datorns tur.
- Datorns drag ska levereras inom 3 sekunder oavsett svårighetsgrad (NFR-02.3).

## Postconditions

**Lyckat:** Systemet har behandlat spelarens handling inom den angivna responstiden och uppdaterat
partitillståndet.

**Misslyckat:** Systemet har inte svarat inom den angivna responstiden, eller har svarat utan att
partitillståndet uppdaterats.

## Särskilda krav
- Startsidan ska vara färdigrenderad inom 2 sekunder vid 25 Mbit/s (NFR-02.1).
- Visuell återkoppling på ett drag inom 100 ms (NFR-02.2).
- Datorns drag inom 3 sekunder (NFR-02.3).
- Vinstkontroll inom 100 ms (NFR-02.4).
- Inbjudningslänk inom 1 sekund (NFR-02.5).
- Ett drag ska synas hos motståndaren inom 500 ms i parti mot vän (NFR-02.6).
- Byte av svårighetsgrad eller brädstorlek inom 300 ms (NFR-02.7).

## Beslut på tidigare öppna frågor

| Tidigare öppen fråga | Beslut |
|---|---|
| Vilken exakt tid gäller för varje handling? | Tiderna är angivna per handling i NFR-02.1 – NFR-02.7. |
| Från vilken tidpunkt mäts responstiden? | Från att klicket eller trycket registreras i klienten till att den uppdaterade vyn är renderad. Mätpunkten är definierad under NFR-02 i `04-icke-funktionella-krav.md`. |
| Gäller samma tid för giltiga och ogiltiga handlingar? | Ja. NFR-02.2 gäller den visuella återkopplingen, oavsett om draget accepteras eller avvisas. |

## Öppna frågor
- Ska responstiden mätas på en definierad referensenhet, och i så fall vilken? NFR-01.2 anger ett
  spann av skärmbredder, inte en prestandanivå.
