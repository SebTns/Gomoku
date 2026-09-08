

### AC-14-01: Partiet avslutas som oavgjort

**Relaterade krav:** FR-14.1, FR-14.2, FR-14.3

**Given** att ett parti pågår  
**And** det finns en ledig skärningspunkt kvar på spelplanen  
**And** ingen spelare har fem i rad  
**When** en spelare gör ett giltigt drag på den sista lediga skärningspunkten  
**Then** ska systemet kontrollera om någon har fem i rad  
**And** konstatera att ingen spelare har fem i rad  
**And** avsluta partiet som oavgjort  
**And** visa i resultatvyn att partiet slutade oavgjort.

---

### AC-14-02: Sista draget ger fem i rad

**Relaterade krav:** FR-14.1, FR-14.5

**Given** att ett parti pågår  
**And** det finns en ledig skärningspunkt kvar på spelplanen  
**When** en spelare gör ett giltigt drag på den sista lediga skärningspunkten  
**And** draget skapar fem i rad  
**Then** ska systemet registrera resultatet som vinst  
**And** partiet ska inte registreras som oavgjort.

---

### AC-14-03: Inga fler drag efter oavgjort

**Relaterade krav:** FR-14.4

**Given** att partiet har avslutats som oavgjort  
**When** spelaren försöker göra ytterligare ett drag  
**Then** ska systemet förhindra draget.
