## Acceptance Tests – UC-01 Starta nytt parti

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-01-01: Spelaren startar ett nytt parti

**Relaterade krav:** FR-03.1, FR-03.2, FR-03.3, FR-03.4, FR-04.3, NFR-02.1

**Given** att spelaren är på startsidan  
**And** har valt "Starta nytt parti"  
**And** ser konfigurationsvyn med brädstorlek, motståndartyp och färgval  

**When** spelaren bekräftar inställningarna  

**Then** ska systemet skapa ett parti med status PÅGÅENDE  
**And** tilldela färgerna enligt spelarens val  
**And** rendera ett tomt bräde av vald storlek  
**And** visa att svart gör första draget.

---

### AC-01-02: Standardvärden i konfigurationsvyn

**Relaterade krav:** FR-03.2, FR-05.2

**Given** att spelaren har valt "Starta nytt parti"  

**When** konfigurationsvyn visas  

**Then** ska 15×15 vara förvald brädstorlek  
**And** 19×19 ska finnas som alternativ  
**And** Medel ska vara förvald svårighetsgrad när motståndaren är datorn.

---

### AC-01-03: Spelaren avbryter konfigurationen (UC-01 AF-01)

**Relaterade krav:** FR-03.5

**Given** att spelaren är i konfigurationsvyn  

**When** spelaren avbryter  

**Then** ska inget parti skapas  
**And** spelaren ska återgå till startsidan  
**And** inga inställningar ska sparas.

---

### AC-01-04: Partiet kan inte skapas (UC-01 AF-02)

**Relaterade krav:** FR-03.6, NFR-04.1, NFR-04.6

**Given** att spelaren har bekräftat konfigurationen  
**And** partiet inte kan skapas  

**When** systemet försöker starta partiet  

**Then** ska systemet visa ett felmeddelande på svenska som beskriver vad som hänt  
**And** behålla spelaren i konfigurationsvyn  
**And** låta spelaren försöka igen.

---

### AC-01-05: Ett parti pågår redan (UC-01 AF-03)

**Relaterade krav:** FR-03.7, FR-03.8, FR-03.9

**Given** att ett parti med status PÅGÅENDE finns  

**When** spelaren väljer att starta ett nytt parti  

**Then** ska systemet begära en bekräftelse innan det pågående partiet överges  
**And** vid avbrott ska det pågående partiet fortsätta och inget nytt parti skapas  
**And** vid bekräftelse ska det pågående partiet avslutas innan konfigurationen fortsätter.
