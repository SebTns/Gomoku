# UC-29: Tillfälligt blockera en spelare


| Fält | Värde |
| --- | --- |
| **Use Case ID** | UC-29 |
| **Namn** | Tillfälligt blockera en spelare |
| **Version** | 1.1 |
| **Primär aktör** | Administratör |
| **Sekundär aktör** | — |
| **Relaterade FR** | FR-29.1 – FR-29.10 |
| **Relaterade NFR** | NFR-05.1 – NFR-05.4 |

## Beskrivning

Administratören vill kunna blockera en spelare tillfälligt när det finns ett modereringsärende som motiverar en blockering.

## Förutsättningar

- Administratören har tillgång till systemets modereringsfunktion.
- Spelaren finns i systemet.
- Det finns ett modereringsärende kopplat till spelaren.

## Huvudflöde

1. Administratören öppnar ett modereringsärende om spelaren.
2. Systemet visar information om spelaren och det aktuella modereringsärendet.
3. Administratören granskar informationen.
4. Administratören väljer att blockera spelaren tillfälligt.
5. Administratören väljer hur länge blockeringen ska gälla.
6. Systemet visar information om den valda blockeringen och begär en bekräftelse.
7. Administratören bekräftar blockeringen.
8. Systemet genomför blockeringen.
9. Systemet registrerar vilken spelare som blockerades, blockeringens starttid, blockeringens sluttid och vilket modereringsärende blockeringen är kopplad till.
10. Systemet informerar administratören om att blockeringen har genomförts.
11. Systemet förhindrar den blockerade spelaren från att delta i nya partier under blockeringstiden.
12. När blockeringstiden har gått ut tar systemet automatiskt bort blockeringen.

## Alternativa flöden

### AF-01: Administratören avbryter blockeringen

Vid steg 7 väljer administratören att avbryta i stället för att bekräfta blockeringen.

- Ingen blockering genomförs.
- Spelaren registreras inte som blockerad.
- Administratören återgår till modereringsärendet.

### AF-02: Blockeringen kan inte genomföras

Vid steg 8 kan systemet inte genomföra blockeringen.

- Systemet informerar administratören om att blockeringen inte kunde genomföras.
- Spelaren registreras inte som blockerad.
- Administratören kan försöka genomföra blockeringen igen.

## Postconditions

**Lyckat:**  
Spelaren är tillfälligt blockerad. Blockeringen och dess giltighetstid är registrerade och administratören har fått en bekräftelse.

**Misslyckat:**  
Spelaren är inte blockerad och administratören har informerats om att blockeringen inte kunde genomföras.

**Avbrutet:**  
Ingen blockering har genomförts och spelaren är inte registrerad som blockerad.

## Särskilda krav

- Blockeringen ska börja gälla inom 1 minut (NFR-05.1).
- Beslutet om blockeringen ska sparas i 12 månader (NFR-05.2).
- Den blockerade spelaren ska inte kunna se vem som har gjort rapporten (NFR-05.3).
- Rapporter ska kunna hämtas av administratören inom 24 timmar (NFR-05.4).

## Öppna frågor

- Ska spelaren få information om att hen har blivit blockerad?
- Ska spelaren få veta orsaken till blockeringen?
- Vad ska hända om spelaren redan deltar i ett pågående parti när blockeringen börjar gälla?
- Ska blockeringen gälla alla spellägen eller endast spel mot andra spelare?

