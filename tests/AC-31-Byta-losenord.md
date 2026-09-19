## Acceptance Tests – UC-31 Byta lösenord

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-31-01: Spelaren byter lösenord

**Relaterade krav:** FR-19.1, FR-19.2, FR-19.3, FR-19.4

**Given** att spelaren är inloggad  
**And** har valt "Change Password"  

**When** spelaren anger rätt nuvarande lösenord  
**And** ett nytt lösenord på minst 8 tecken  
**And** samma nya lösenord i upprepningsfältet  

**Then** ska systemet spara det nya lösenordet  
**And** visa en bekräftelse.

---

### AC-31-02: Det nya lösenordet gäller vid nästa inloggning

**Relaterade krav:** FR-19.4

**Given** att spelaren har bytt lösenord enligt AC-31-01  

**When** spelaren loggar ut och loggar in igen  

**Then** ska inloggning med det nya lösenordet lyckas  
**And** inloggning med det gamla lösenordet misslyckas.

---

### AC-31-03: Fel nuvarande lösenord (UC-31 AF-01)

**Relaterade krav:** FR-19.2, FR-19.5

**Given** att spelaren har valt "Change Password"  

**When** spelaren anger fel nuvarande lösenord  

**Then** ska systemet avvisa bytet  
**And** visa ett felmeddelande  
**And** lösenordet ska vara oförändrat.

---

### AC-31-04: Det nya lösenordet uppfyller inte kraven (UC-31 AF-02)

**Relaterade krav:** FR-19.3, FR-19.5

**Given** att spelaren har valt "Change Password"  

**When** spelaren anger ett nytt lösenord på 7 tecken  

**Then** ska systemet avvisa bytet  
**And** visa att lösenordet måste vara minst 8 tecken.

---

### AC-31-05: Upprepningen matchar inte (UC-31 AF-02)

**Relaterade krav:** FR-19.5

**Given** att spelaren har valt "Change Password"  

**When** spelaren anger olika lösenord i fälten för nytt lösenord och upprepning  

**Then** ska systemet avvisa bytet  
**And** visa att lösenorden inte matchar.

---

### AC-31-06: Spelaren avbryter (UC-31 AF-03)

**Relaterade krav:** FR-19.1

**Given** att spelaren har börjat fylla i formuläret  

**When** spelaren avbryter  

**Then** ska lösenordet vara oförändrat.

---

### AC-31-07: Lösenordet skickas krypterat och lagras som hash

**Relaterade krav:** NFR-07.1, NFR-07.6

**Given** att spelaren byter lösenord  

**When** anropet till servern inspekteras  
**And** kontots lagrade lösenordsfält läses  

**Then** ska anropet gå över TLS 1.2 eller senare  
**And** det lagrade värdet ska vara en bcrypt-hash  
**And** lösenordet i klartext ska inte finnas i loggarna.
