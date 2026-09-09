

### AC-16-01: Spelaren får fem i rad

**Relaterade krav:** FR-08.8, FR-08.9, FR-08.10

**Given** att ett parti pågår  
**And** det är spelarens tur  
**When** spelaren gör ett giltigt drag som skapar fem stenar i rad horisontellt, vertikalt eller diagonalt  
**Then** ska systemet kontrollera att fem i rad har uppstått  
**And** avsluta partiet  
**And** utse spelaren till vinnare  
**And** markera den vinnande raden visuellt.

---

### AC-16-02: Spelarens drag ger ingen vinst

**Relaterade krav:** FR-08.8

**Given** att ett parti pågår  
**And** det är spelarens tur  
**When** spelaren gör ett giltigt drag som inte skapar fem i rad  
**Then** ska systemet konstatera att ingen vinst har uppstått  
**And** partiet ska fortsätta  
**And** turen ska gå vidare till motståndaren.

---

### AC-16-03: Inga fler drag efter vinst

**Relaterade krav:** FR-08.13

**Given** att spelaren har fått fem i rad  
**And** partiet har avslutats  
**When** någon försöker göra ytterligare ett drag  
**Then** ska systemet förhindra draget.
