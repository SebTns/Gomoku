

### AC-11-01: Spelaren ger upp ett pågående parti

**Relaterade krav:** FR-09.1, FR-09.2, FR-09.3, FR-09.4

**Given** att ett parti pågår  
**When** spelaren väljer "Ge upp"  
**Then** ska systemet visa en bekräftelse  
**When** spelaren bekräftar att hen vill ge upp  
**Then** ska systemet avsluta partiet  
**And** registrera spelaren som förlorare  
**And** registrera motståndaren som vinnare  
**And** visa resultatvyn med information om vem som vann och vem som gav upp.

---

### AC-11-02: Spelaren avbryter uppgivandet

**Relaterade krav:** FR-09.2, FR-09.6

**Given** att ett parti pågår  
**And** spelaren har valt "Ge upp"  
**And** systemet visar en bekräftelse  
**When** spelaren väljer "Avbryt"  
**Then** ska uppgivandet inte genomföras  
**And** partiet ska fortsätta.

---

### AC-11-03: Spelaren försöker ge upp ett avslutat parti

**Relaterade krav:** FR-09.5

**Given** att partiet redan är avslutat  
**When** spelaren försöker välja "Ge upp"  
**Then** ska systemet förhindra att spelaren ger upp.
