# UC-02: Gör ett drag

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-02 |
| **Namn** | Gör ett drag |
| **Version** | 1.1 |
| **Primär aktör** | Spelare |
| **Sekundär aktör** | Motståndare (spelare eller datorn) |
| **Relaterade FR** | FR-08.1 – FR-08.17 |
| **Relaterade NFR** | NFR-02.2, NFR-02.4, NFR-06.3, NFR-06.4, NFR-06.5, NFR-08.2 |
| **Relaterade AC** | AC-02-01 – AC-02-08 |

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
7. Systemet registrerar draget med position, färg, dragnummer och tidpunkt.
8. Systemet kontrollerar om den senast placerade stenen ingår i en obruten rad av exakt fem
   stenar av samma färg horisontellt, vertikalt eller diagonalt.
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
Vid steg 8 ingår den senast placerade stenen i en obruten rad av exakt fem stenar.
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

### AF-06: Överlinje — sex eller fler i rad
Vid steg 8 ingår den senast placerade stenen i en obruten rad av sex eller fler stenar av
samma färg.
- Systemet utser **ingen** vinnare (FR-08.15).
- Partiet fortsätter och turen lämnas över som i steg 9.
- Se Regelbeslut nedan.

## Postconditions

**Lyckat:** Draget är registrerat, brädet uppdaterat och turen överlämnad — eller partiet avslutat med ett resultat.

**Misslyckat:** Brädet är oförändrat, ingen tur har bytts och spelaren har fått besked om varför.

## Särskilda krav
- Visuell återkoppling ska visas inom 100 ms från klick eller tryck (NFR-02.2).
- Kontrollen av fem i rad ska vara klar inom 100 ms efter draget (NFR-02.4).
- Klick- och tryckytan per skärningspunkt ska vara minst 44 × 44 px på pekskärm (NFR-06.5).
- Stenarna ska gå att skilja åt på mer än enbart färg (NFR-06.3).
- Ett drag ska gå att göra med tangentbord (NFR-06.4).
- Partiet ska aldrig kunna hamna i ett läge där ingen spelare kan göra ett giltigt drag utan att
  partiet avslutas korrekt (NFR-08.2).

## Regelbeslut

**Vinstvillkoret är exakt fem i rad. Sex eller fler i rad är inte en vinst.**

Frågan stod tidigare öppen i denna fil. Den är avgjord mot `00-begreppslista.md`, som anger
"5 i rad = *Exakt* fem på varandra följande stenar" och "6 eller mer i rad = Inte en vinst enligt
vanliga Gomoku-regler". Begreppslistan säger uttryckligen att dess definitioner tar företräde vid
konflikt, så den är normerande. Beslutet är skrivet till krav i FR-08.14 – FR-08.16 och testas av
AC-02-05 och AC-02-06.

Konsekvensen är att kontrollen i steg 8 måste mäta radens **fulla längd** åt båda hållen från den
senast placerade stenen, inte bara leta efter fem intilliggande stenar. En implementation som
stannar vid fem hittar en vinst även i en sexa, och skulle passera ett test som bara lägger fem
stenar.

## Öppna frågor
- Ska ett drag kunna ångras (→ UC-19), och i så fall inom vilken tid? FR-12 finns skriven, men
  UC-02 beskriver inte var i flödet ångringen bryter in.
- Ska överlinjen markeras visuellt för spelaren, så att det syns *varför* draget inte vann?

## Kända motsägelser
- **Svarstid.** `AC-02` angav tidigare 0,33 sekunder för visuell återkoppling medan NFR-02.2 anger
  100 ms. NFR-02.2 gäller; acceptanskriteriet är rättat. Två dokument gav två svar på samma fråga,
  och det var acceptanskriteriet — inte kravet — som hade fel.
