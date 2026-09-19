## Acceptance Tests – UC-30 Ändra kontoinställningar

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-30-01: Spelaren ändrar sitt synliga namn

**Relaterade krav:** FR-18.1, FR-18.2, FR-18.3

**Given** att spelaren är inloggad  
**And** befinner sig i "Account Settings"  

**When** spelaren ändrar sitt synliga namn till ett giltigt namn  
**And** sparar  

**Then** ska systemet uppdatera kontot  
**And** visa en bekräftelse  
**And** det nya namnet ska visas i nästa parti.

---

### AC-30-02: Nuvarande inställningar visas

**Relaterade krav:** FR-18.1

**Given** att spelaren är inloggad  

**When** spelaren väljer "Account Settings"  

**Then** ska systemet visa spelarens nuvarande synliga namn och e-postadress.

---

### AC-30-03: Ogiltigt värde avvisas (UC-30 AF-01)

**Relaterade krav:** FR-18.2, FR-18.4, NFR-04.1

**Given** att spelaren är i "Account Settings"  

**When** spelaren anger en e-postadress utan "@"  
**And** sparar  

**Then** ska systemet inte spara ändringen  
**And** markera fältet  
**And** visa vilken regel som inte uppfylls.

---

### AC-30-04: Skript i spelarnamnet körs inte

**Relaterade krav:** NFR-07.3

**Given** att spelaren är i "Account Settings"  

**When** spelaren sparar namnet `<script>alert(1)</script>`  
**And** namnet visas för en motståndare  

**Then** ska inget skript köras i motståndarens webbläsare  
**And** namnet ska antingen avvisas eller visas som ren text.

---

### AC-30-05: Spelaren avbryter (UC-30 AF-02)

**Relaterade krav:** FR-18.1

**Given** att spelaren har ändrat ett fält men inte sparat  

**When** spelaren avbryter  

**Then** ska inga ändringar sparas  
**And** kontot ska ha samma värden som innan.

---

### AC-30-06: Ändringen kan inte sparas (UC-30 AF-03)

**Relaterade krav:** FR-18.4, NFR-04.1, NFR-04.6

**Given** att spelaren har angett giltiga värden  
**And** ett tekniskt fel uppstår vid sparandet  

**When** spelaren sparar  

**Then** ska systemet visa ett felmeddelande på engelska som beskriver vad som hänt  
**And** behålla de tidigare inställningarna.
