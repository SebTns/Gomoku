

### AC-15-01: Motståndaren får fem i rad

**Relaterade krav:** FR-08.8, FR-08.9, FR-08.10

**Given** att ett parti pågår  
**And** det är motståndarens tur  
**When** motståndaren gör ett giltigt drag som skapar fem stenar i rad  
**Then** ska systemet kontrollera att fem i rad har uppstått  
**And** avsluta partiet  
**And** registrera motståndaren som vinnare och spelaren som förlorare  
**And** markera den vinnande raden visuellt.

---

### AC-15-02: Motståndaren får inte fem i rad

**Relaterade krav:** FR-08.8

**Given** att ett parti pågår  
**And** det är motståndarens tur  
**When** motståndaren gör ett giltigt drag som inte skapar fem i rad  
**Then** ska systemet konstatera att ingen vinst har uppstått  
**And** partiet ska fortsätta enligt spelets regler.

---

### AC-15-03: Inga fler drag efter förlust

**Relaterade krav:** FR-08.13

**Given** att motståndaren har fått fem i rad  
**And** partiet har avslutats  
**When** spelaren försöker göra ytterligare ett drag  
**Then** ska systemet förhindra draget. 

