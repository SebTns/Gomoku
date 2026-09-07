## Acceptance Tests – UC-29 Tillfälligt blockera en spelare

### AT-UC29-01: Tillfälligt blockera en spelare

**Relaterade krav:** FR-29.1–FR-29.4, FR-29.6–FR-29.8, FR-29.10

**Given** att administratören har öppnat ett modereringsärende för en spelare  
**And** information om spelaren och modereringsärendet visas  

**When** administratören väljer att blockera spelaren  
**And** väljer hur länge blockeringen ska gälla  
**And** bekräftar blockeringen  

**Then** ska systemet genomföra blockeringen  
**And** registrera vilken spelare som blockerades, blockeringens starttid, sluttid och modereringsärende  
**And** informera administratören om att blockeringen har genomförts  
**And** förhindra spelaren från att delta i nya partier under blockeringstiden  
**And** automatiskt ta bort blockeringen när blockeringstiden har gått ut.


### AT-UC29-02: Administratören avbryter blockeringen

**Relaterade krav:** FR-29.4, FR-29.5

**Given** att administratören har valt en spelare som ska blockeras  
**And** systemet begär bekräftelse på blockeringen  

**When** administratören väljer att avbryta  

**Then** ska ingen blockering genomföras  
**And** spelaren ska inte registreras som blockerad.


### AT-UC29-03: Blockeringen kan inte genomföras

**Relaterade krav:** FR-29.9

**Given** att administratören har valt en spelare  
**And** valt hur länge blockeringen ska gälla  
**And** bekräftat blockeringen  

**When** systemet inte kan genomföra blockeringen  

**Then** ska systemet informera administratören om att blockeringen inte kunde genomföras  
**And** spelaren ska inte registreras som blockerad.
