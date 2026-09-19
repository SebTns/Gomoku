## Acceptance Tests – UC-NFR-07 Spelaren får återkoppling efter handling

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-NFR-07-01: Färg och startspelare visas vid partistart

**Relaterade krav:** FR-04.7

**Given** att spelaren har valt vit mot datorn  

**When** partiet startar  

**Then** ska systemet visa att spelaren har vit  
**And** att svart gör första draget.

---

### AC-NFR-07-02: Placerad sten markeras och dragräknaren uppdateras

**Relaterade krav:** FR-08.5, FR-08.7, NFR-02.2

**Given** att det är spelarens tur och dragräknaren visar 4  

**When** spelaren placerar en sten  

**Then** ska den senast placerade stenen markeras  
**And** dragräknaren visa 5  
**And** detta ska synas inom 100 ms.

---

### AC-NFR-07-03: Det syns att datorn tänker

**Relaterade krav:** FR-06.4, FR-08.6

**Given** att spelaren har gjort sitt drag mot datorn  

**When** datorn beräknar sitt drag  

**Then** ska systemet visa att det är datorns tur och att datorn beräknar  
**And** när datorn har spelat ska turen visas som spelarens.

---

### AC-NFR-07-04: Den avgörande raden markeras

**Relaterade krav:** FR-08.10

**Given** att en spelare har fått fem i rad  

**When** systemet visar resultatet  

**Then** ska de fem stenarna i den vinnande raden vara markerade.

---

### AC-NFR-07-05: Återkoppling på upptagen punkt (UC-NFR-07 AF-01)

**Relaterade krav:** FR-08.2

**Given** att det är spelarens tur  

**When** spelaren klickar på en punkt där det redan ligger en sten  

**Then** ska systemet visa att punkten är upptagen  
**And** turen ska ligga kvar hos spelaren.

---

### AC-NFR-07-06: Återkoppling när det inte är spelarens tur (UC-NFR-07 AF-02)

**Relaterade krav:** FR-08.3

**Given** att det är motståndarens tur  

**When** spelaren klickar på brädet  

**Then** ska systemet visa att det inte är spelarens tur  
**And** brädet ska vara oförändrat.

---

### AC-NFR-07-07: Felmeddelanden har en väg vidare (UC-NFR-07 AF-03)

**Relaterade krav:** NFR-04.1, NFR-04.6

**Given** att en systemåtgärd misslyckas under partiet  

**When** felmeddelandet visas  

**Then** ska det vara på engelska  
**And** beskriva vad som hänt och nästa steg  
**And** erbjuda minst en åtgärd (försök igen eller tillbaka till start).

---

### AC-NFR-07-08: Återkopplingen bygger inte enbart på färg

**Relaterade krav:** NFR-06.1, NFR-06.2, NFR-06.3

**Given** att gränssnittet visas i gråskala  

**When** spelaren gör ett drag, gör ett ogiltigt drag och vinner  

**Then** ska varje återkoppling gå att förstå utan färg (t.ex. via ikon, text eller form)  
**And** svarta och vita stenar ska gå att skilja åt  
**And** all text ska ha en kontrast på minst 4,5:1 mot bakgrunden.
