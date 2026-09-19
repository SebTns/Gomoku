## Acceptance Tests – UC-29 Tillfälligt blockera en spelare

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.
Kriterierna hette tidigare AT-UC29-xx och är omnumrerade till AC-29-xx för att följa
UC-numreringen.

---

### AC-29-01: Tillfälligt blockera en spelare

**Relaterade krav:** FR-29.1 – FR-29.4, FR-29.6 – FR-29.8, FR-29.14, NFR-05.1, NFR-05.5, NFR-05.6

**Given** att administratören har öppnat ett modereringsärende för en spelare  
**And** spelarens namn, spelar-ID och modereringsärendet visas  

**When** administratören väljer att blockera spelaren  
**And** väljer hur länge blockeringen ska gälla  
**And** väljer blockeringens omfattning  
**And** bekräftar blockeringen  

**Then** ska systemet genomföra blockeringen inom 1 minut  
**And** registrera spelare, starttid och sluttid i UTC, omfattning, beslutsfattande administratör
och modereringsärende  
**And** informera administratören om att blockeringen har genomförts  
**And** förhindra spelaren från att påbörja nya partier under blockeringstiden.

---

### AC-29-02: Administratören avbryter blockeringen (UC-29 AF-01)

**Relaterade krav:** FR-29.4, FR-29.5

**Given** att administratören har valt en spelare som ska blockeras  
**And** systemet begär bekräftelse på blockeringen  

**When** administratören väljer att avbryta  

**Then** ska ingen blockering genomföras  
**And** spelaren ska inte registreras som blockerad.

---

### AC-29-03: Blockeringen kan inte genomföras (UC-29 AF-02)

**Relaterade krav:** FR-29.9, NFR-04.1

**Given** att administratören har valt en spelare  
**And** valt hur länge blockeringen ska gälla  
**And** bekräftat blockeringen  

**When** systemet inte kan genomföra blockeringen  

**Then** ska systemet informera administratören om att blockeringen inte kunde genomföras  
**And** spelaren ska inte registreras som blockerad  
**And** administratören ska kunna försöka igen.

---

### AC-29-04: Blockeringen hävs automatiskt när tiden gått ut

**Relaterade krav:** FR-29.10, NFR-05.6, NFR-05.7

**Given** att en spelare är blockerad med sluttid T  
**And** systemklockan står på T minus 1 minut  

**When** klockan passerar T  

**Then** ska blockeringens status vara "utgången"  
**And** spelaren ska kunna påbörja ett nytt parti.

> **Testnot.** Testet körs med simulerad tid enligt NFR-05.7. Utan den möjligheten går kravet
> inte att verifiera annat än genom att vänta ut blockeringstiden, vilket gör det oanvändbart i
> en testsvit. Samma problem, fast i en annan storleksordning, gäller NFR-05.2 (12 månader) — det
> kravet verifieras mot lagringsschemat och inte genom test.

---

### AC-29-05: Spelaren informeras om blockeringen

**Relaterade krav:** FR-29.11, FR-29.12, NFR-05.3

**Given** att en spelare är blockerad  

**When** spelaren försöker logga in eller starta ett parti  

**Then** ska systemet informera spelaren om att en blockering gäller  
**And** visa när blockeringen upphör  
**And** visa orsakskategorin  
**And** inte visa vem som har rapporterat spelaren.

---

### AC-29-06: Blockering under pågående parti (UC-29 AF-03)

**Relaterade krav:** FR-29.13, NFR-08.2

**Given** att en spelare deltar i ett parti med status PÅGÅENDE  

**When** en blockering av spelaren träder i kraft  

**Then** ska det pågående partiet inte avbrytas  
**And** spelaren ska kunna spela klart partiet  
**And** spelaren ska hindras från att påbörja ett nytt parti  
**And** meddelandet enligt AC-29-05 ska visas när partiet har avslutats.

---

### AC-29-07: Administratören häver blockeringen i förtid (UC-29 AF-04)

**Relaterade krav:** FR-29.15, NFR-05.2, NFR-05.5

**Given** att en spelare är blockerad och blockeringstiden inte har löpt ut  

**When** administratören häver blockeringen  

**Then** ska blockeringen upphöra att gälla  
**And** hävningen ska registreras med tidpunkt och administratör  
**And** det ursprungliga blockeringsbeslutet ska finnas kvar i modereringsloggen.

---

### AC-29-08: Rapporter är hämtbara för administratören

**Relaterade krav:** NFR-05.4

**Given** att en spelarrapport har kommit in vid tidpunkt T  

**When** administratören öppnar modereringskön  
**And** högst 24 timmar har gått sedan T  

**Then** ska rapporten finnas i kön  
**And** rapporterna ska ligga i inkommen ordning.
