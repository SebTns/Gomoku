## Acceptance Tests – UC-32 Återställ spelet

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-32-01: Spelaren återställer ett pågående parti

**Relaterade krav:** FR-23.1, FR-23.2, FR-23.4, FR-23.5

**Given** att ett parti mot datorn pågår och 10 drag har gjorts  

**When** spelaren väljer "Reset Game"  
**And** bekräftar  

**Then** ska brädet vara tomt  
**And** dragräknaren och dragregistret vara nollställda  
**And** systemet visa att svart gör första draget.

---

### AC-32-02: Konfigurationen behålls

**Relaterade krav:** FR-23.3

**Given** att ett parti pågår på 19×19 mot datorn på Svår där spelaren har vit  

**When** spelaren återställer partiet  

**Then** ska det nya partiet ha brädstorleken 19×19  
**And** motståndartypen dator  
**And** svårighetsgraden Svår  
**And** spelaren ska fortfarande ha vit.

---

### AC-32-03: Bekräftelse krävs

**Relaterade krav:** FR-23.2

**Given** att ett parti pågår  

**When** spelaren väljer "Reset Game"  

**Then** ska systemet visa en bekräftelse som säger att partiet inte går att återställa efteråt  
**And** brädet ska vara oförändrat tills spelaren har bekräftat.

---

### AC-32-04: Spelaren ångrar sig (UC-32 AF-01)

**Relaterade krav:** FR-23.8

**Given** att systemet visar bekräftelsen för återställning  

**When** spelaren väljer "Cancel"  

**Then** ska partiet fortsätta oförändrat  
**And** samma spelare ska ha turen.

---

### AC-32-05: Parti mot vän kräver båda spelarnas samtycke

**Relaterade krav:** FR-23.6

**Given** att ett parti mot en vän pågår  

**When** spelaren väljer "Reset Game" och bekräftar  

**Then** ska motståndaren få en förfrågan om återställning  
**And** partiet återställs först när motståndaren har godkänt  
**And** om motståndaren nekar ska partiet fortsätta oförändrat.

---

### AC-32-06: Ett avslutat parti kan inte återställas (UC-32 AF-02)

**Relaterade krav:** FR-23.7

**Given** att partiet har status AVSLUTAT  

**When** spelaren försöker välja "Reset Game"  

**Then** ska systemet inte återställa partiet  
**And** hänvisa till "Play Again" (→ UC-13).
