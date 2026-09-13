# UC-29: Tillfälligt blockera en spelare

| Fält | Värde |
| --- | --- |
| **Use Case ID** | UC-29 |
| **Namn** | Tillfälligt blockera en spelare |
| **Version** | 1.2 |
| **Primär aktör** | Administratör |
| **Sekundär aktör** | Blockerad spelare (mottagare av beslutet) |
| **Relaterade FR** | FR-29.1 – FR-29.15 |
| **Relaterade NFR** | NFR-05.1 – NFR-05.7, NFR-04.1 |
| **Relaterade AC** | AC-29-01 – AC-29-08 |

## Beskrivning

Administratören vill kunna blockera en spelare tillfälligt när det finns ett modereringsärende
som motiverar en blockering.

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
6. Administratören väljer om blockeringen ska omfatta alla spellägen eller endast partier mot
   andra spelare.
7. Systemet visar information om den valda blockeringen och begär en bekräftelse.
8. Administratören bekräftar blockeringen.
9. Systemet genomför blockeringen.
10. Systemet registrerar vilken spelare som blockerades, blockeringens starttid och sluttid i UTC,
    blockeringens omfattning, vilken administratör som fattade beslutet och vilket
    modereringsärende blockeringen är kopplad till.
11. Systemet informerar administratören om att blockeringen har genomförts.
12. Systemet förhindrar den blockerade spelaren från att påbörja nya partier under
    blockeringstiden.
13. Systemet informerar den blockerade spelaren om blockeringen, dess orsakskategori och när den
    upphör, vid nästa inloggnings- eller spelstartsförsök.
14. När blockeringstiden har gått ut tar systemet automatiskt bort blockeringen.

## Alternativa flöden

### AF-01: Administratören avbryter blockeringen
Vid steg 8 väljer administratören att avbryta i stället för att bekräfta blockeringen.
- Ingen blockering genomförs.
- Spelaren registreras inte som blockerad.
- Administratören återgår till modereringsärendet.

### AF-02: Blockeringen kan inte genomföras
Vid steg 9 kan systemet inte genomföra blockeringen.
- Systemet informerar administratören om att blockeringen inte kunde genomföras.
- Spelaren registreras inte som blockerad.
- Administratören kan försöka genomföra blockeringen igen.

### AF-03: Spelaren deltar i ett pågående parti när blockeringen träder i kraft
Vid steg 12 sitter spelaren redan i ett parti med status `PÅGÅENDE`.
- Systemet avbryter inte det pågående partiet.
- Spelaren får spela klart partiet (FR-29.13).
- Systemet förhindrar spelaren från att påbörja något nytt parti.
- Meddelandet i steg 13 visas när partiet har avslutats.

### AF-04: Administratören häver blockeringen i förtid
Efter steg 12, medan blockeringen fortfarande gäller.
- Administratören väljer att häva blockeringen.
- Systemet tar bort blockeringen omedelbart.
- Systemet registrerar hävningen med tidpunkt och vilken administratör som utförde den
  (FR-29.15).
- Det ursprungliga beslutet raderas inte, utan bevaras enligt NFR-05.2.

## Postconditions

**Lyckat:**
Spelaren är tillfälligt blockerad. Blockeringen, dess omfattning, giltighetstid och beslutsfattare
är registrerade, administratören har fått en bekräftelse och spelaren har informerats.

**Misslyckat:**
Spelaren är inte blockerad och administratören har informerats om att blockeringen inte kunde
genomföras.

**Avbrutet:**
Ingen blockering har genomförts och spelaren är inte registrerad som blockerad.

## Särskilda krav

- Blockeringen ska börja gälla inom 1 minut (NFR-05.1).
- Beslutet om blockeringen ska sparas i 12 månader (NFR-05.2).
- Den blockerade spelaren ska inte kunna se vem som har gjort rapporten (NFR-05.3).
- Rapporter ska kunna hämtas av administratören inom 24 timmar (NFR-05.4).
- Beslutet ska gå att spåra till den administratör som fattade det (NFR-05.5).
- Start- och sluttid ska registreras i UTC (NFR-05.6).
- Blockeringens status ska gå att avläsa vid en godtycklig tidpunkt utan att tiden behöver löpa i
  realtid (NFR-05.7), annars går varken FR-29.10 eller NFR-05.2 att testa.

## Beslut på tidigare öppna frågor

| Tidigare öppen fråga | Beslut | Krav |
|---|---|---|
| Ska spelaren få veta att hen blivit blockerad? | Ja — vid nästa inloggnings- eller spelstartsförsök, med sluttid. | FR-29.11 |
| Ska spelaren få veta orsaken? | Orsakskategori ja, rapportörens identitet nej. NFR-05.3 sätter gränsen. | FR-29.12, NFR-05.3 |
| Vad händer vid pågående parti? | Partiet får spelas klart; inga nya partier får påbörjas. | FR-29.13, AF-03 |
| Gäller blockeringen alla spellägen? | Administratören väljer omfattning per beslut. | FR-29.14 |

## Öppna frågor

- Hur testas NFR-05.2 (12 månaders lagring)? Kravet är formulerat i en tidsskala som ingen
  testsvit kan vänta ut. Se anmärkningen i `08-use-cases-och-test-cases.md` — kravet verifieras
  via lagringsschemat och en simulerad klocka (NFR-05.7), inte genom att tiden förflyter.
- Ska upprepade blockeringar av samma spelare eskalera automatiskt i längd?
- Vad händer med spelarens pågående inbjudningar (FR-07) när blockeringen träder i kraft?
