# UC-02: Gör ett drag

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-02 |
| **Namn** | Gör ett drag |
| **Version** | 1.0 |
| **Primär aktör** | Spelare |
| **Sekundär aktör** | Motståndare (spelare eller datorn) |
| **Relaterade FR** | FR-08.1 – FR-08.13 |
| **Relaterade NFR** | NFR-02.2, NFR-02.4, NFR-06.3, NFR-06.5 |

## Beskrivning
Spelaren placerar en sten på en ledig skärningspunkt på brädet. Systemet validerar draget,
kontrollerar om partiet är avgjort och lämnar över turen. Detta är spelets centrala flöde och
upprepas till dess att partiet avslutas.

## Förutsättningar
- Ett parti med status `PÅGÅENDE` finns.
- Det är spelarens tur.
- Brädet visas.

## Huvudflöde

1. Systemet visar vems tur det är, med spelarnamn och färg.
2. Spelaren väljer en ledig skärningspunkt genom klick eller tryck.
3. Systemet kontrollerar att punkten är ledig.
4. Systemet placerar spelarens sten på punkten.
5. Systemet markerar den senast placerade stenen.
6. Systemet ökar dragräknaren med ett.
7. Systemet registrerar draget med position, färg och dragnummer.
8. Systemet kontrollerar om fem stenar av samma färg ligger i rad horisontellt, vertikalt eller diagonalt.
9. Ingen femma finns och brädet är inte fullt: systemet lämnar över turen till motståndaren.
10. Motståndaren gör sitt drag (→ UC-05 om motståndaren är datorn, → UC-09 om det är en spelare).
11. Flödet upprepas från steg 1 tills partiet avgörs.

## Alternativa flöden

### AF-01: Punkten är upptagen
Vid steg 3 är den valda punkten redan upptagen.
- Systemet avvisar draget.
- Systemet ger visuell återkoppling om att punkten är upptagen.
- Turen byts inte. Spelaren kan välja en annan punkt.

### AF-02: Det är inte spelarens tur
Vid steg 2 försöker spelaren göra ett drag utanför sin tur.
- Systemet avvisar draget.
- Brädet förblir oförändrat.

### AF-03: Fem i rad uppstår
Vid steg 8 hittar systemet fem i rad.
- Systemet avslutar partiet och utser den spelare som lade stenen till vinnare.
- Systemet markerar den vinnande raden visuellt.
- Systemet visar resultatet (→ UC-16 vid vinst, → UC-15 vid förlust).
- Inga fler drag tillåts.

### AF-04: Brädet blir fullt
Vid steg 8 är brädet fullt utan att någon fått fem i rad.
- Systemet avslutar partiet som oavgjort (→ UC-14).
- Systemet visar resultatet.

### AF-05: Draget kan inte registreras
Vid steg 7 misslyckas registreringen av draget.
- Systemet visar ett felmeddelande.
- Brädet återställs till läget före draget.
- Spelaren kan försöka igen.

## Postconditions

**Lyckat:** Draget är registrerat, brädet uppdaterat och turen överlämnad — eller partiet avslutat med ett resultat.

**Misslyckat:** Brädet är oförändrat, ingen tur har bytts och spelaren har fått besked om varför.

## Särskilda krav
- Visuell återkoppling ska visas inom 100 ms från klick eller tryck (NFR-02.2).
- Kontrollen av fem i rad ska vara klar inom 100 ms efter draget (NFR-02.4).
- Klick- och tryckytan per skärningspunkt ska vara minst 44 × 44 px på pekskärm (NFR-06.5).
- Stenarna ska gå att skilja åt på mer än enbart färg (NFR-06.3).

## Öppna frågor
- Ska exakt fem i rad krävas, eller räknas sex eller fler också som vinst? Standardregeln i
  fri Gomoku är att sex eller fler inte vinner — gruppen måste ta ställning.
- Ska ett drag kunna ångras (→ UC-19), och i så fall inom vilken tid?
