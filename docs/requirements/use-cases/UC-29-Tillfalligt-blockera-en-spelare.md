# UC-29: Tillfälligt blockera en spelare

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-29 |
| **Namn** |Tillfälligt blockera en spelare|
| **Version** | 1.0 |
| **Primär aktör** | Administör|
| **Sekundär aktör** |Spelare|
| **Relaterade FR** |FR-29.1 – FR-29.5  |
| **Relaterade NFR** |NFR-05.1 – NFR-05.4|

## Beskrivning
Administratören ska kunna blockera en spelare tillfälligt om spelaren har brutit mot reglerna
eller blivit rapporterad flera gånger.

## Förutsättningar
- Administratören har tillgång till systemet.
- Spelaren finns i systemet.
- Det finns en rapport eller ett ärende om spelaren.

## Huvudflöde

1. Administratören öppnar ett ärende om spelaren. 
2. Systemet visar information om ärendet.
3. Administratören går igenom informationen.
4. Administratören väljer att blockera spelaren tillfälligt.
5. Systemet frågar om administratören vill genomföra blockeringen.
6. Administratören bekräftar.
7. Systemet blockerar spelaren.
8. Systemet sparar information om blockeringen.
9. Systemet visar att spelaren har blivit blockerad.  

## Alternativa flöden

### AF-01: Administratören ångrar sig.
Vid steg 6 väljer administratören att avbryta .
- Spelaren blockeras inte.
- Administratören går tillbaka till ärendet.

### AF-02: Blockeringen fungerar inte.
vid steg 7 går det inte att blockera spelaren.
-Systemet visar att något gick fel.
-Spelaren blockeras inte.
-Administratören kan försöka igen.

## Postconditions

**Lyckat:** Spelaren är tillfälligt blockerad och blockeringen är sparad .
i systemet.
**Misslyckat:** Spelaren är inte blockerad och administratören får information om att något gick fel.

## Särskilda krav
- Blockeringen ska börja gälla inom 1 minut(NFR-05.1).
- Beslutet om blockeringen ska sparas i 12 månader(NFR-05.2).
- Spelaren ska inte kunna se vem som har gjort rapporten(NFR-05.3).
- Rapporter ska kunna hämtas av administratören inom 24 timmar(NFR-05.4).

## Öppna frågor
- Hur länge ska spelaren vara blockerad?
- Ska spelaren få veta varför hen har blivit blockerad?
- Ska administratören kunna välja hur länge blockeringen gäller? 

