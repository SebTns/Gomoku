## Acceptance Tests – UC-NFR-01 Ge samtycke till cookie

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-NFR-01-01: Cookie-meddelandet visas vid första besöket

**Relaterade krav:** FR-24.1, FR-24.2, FR-24.3

**Given** att en gästanvändare öppnar applikationen för första gången  

**When** startsidan har laddats  

**Then** ska systemet visa ett cookie-meddelande  
**And** förklara vilka cookies som används och varför  
**And** erbjuda "Accept All", "Accept Necessary" och egna val.

---

### AC-NFR-01-02: Inga spårningsskript laddas före samtycke

**Relaterade krav:** FR-24.1, SR-02.7

**Given** att en gästanvändare öppnar applikationen för första gången  

**When** nätverksanropen och de satta cookies inspekteras innan något val görs  

**Then** ska inga analys- eller spårningsskript från tredje part ha laddats  
**And** endast nödvändiga cookies ska vara satta.

---

### AC-NFR-01-03: Gästanvändaren accepterar endast nödvändiga cookies

**Relaterade krav:** FR-24.4, FR-24.5

**Given** att cookie-meddelandet visas  

**When** gästanvändaren väljer "Accept Necessary"  

**Then** ska systemet spara valet med tidpunkt och version av informationen  
**And** endast ladda nödvändiga cookies.

---

### AC-NFR-01-04: Gästanvändaren accepterar alla cookies

**Relaterade krav:** FR-24.4, FR-24.5

**Given** att cookie-meddelandet visas  

**When** gästanvändaren väljer "Accept All"  

**Then** ska systemet spara valet med tidpunkt och version av informationen  
**And** ladda de cookies som omfattas av valet.

---

### AC-NFR-01-05: Meddelandet stängs utan val (UC-NFR-01 AF-01)

**Relaterade krav:** FR-24.6

**Given** att cookie-meddelandet visas  

**When** gästanvändaren stänger meddelandet utan att välja  

**Then** ska systemet behandla det som ett nekande av icke-nödvändiga cookies  
**And** inga icke-nödvändiga cookies ska laddas.

---

### AC-NFR-01-06: Meddelandet visas inte igen

**Relaterade krav:** FR-24.7

**Given** att gästanvändaren har gjort ett val  

**When** gästanvändaren besöker applikationen igen  

**Then** ska cookie-meddelandet inte visas.

---

### AC-NFR-01-07: Gästanvändaren ändrar eller återkallar sitt val (UC-NFR-01 AF-02)

**Relaterade krav:** FR-24.8, FR-24.9

**Given** att gästanvändaren tidigare har valt "Accept All"  

**When** gästanvändaren öppnar "Cookie Settings" och återkallar samtycket  

**Then** ska systemet spara det nya valet  
**And** sluta ladda icke-nödvändiga cookies  
**And** återkallandet ska kräva högst lika många steg som att lämna samtycket.
