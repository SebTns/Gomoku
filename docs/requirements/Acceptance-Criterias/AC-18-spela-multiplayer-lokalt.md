## Acceptance Tests – UC-18 Spela multiplayer lokalt

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-18-01: Två spelare startar ett lokalt parti

**Relaterade krav:** FR-21.1, FR-21.2, FR-21.3, FR-21.7, FR-03.4

**Given** att applikationen är öppen på en enhet  

**When** spelaren väljer "Play with a Friend" och anger lokalt läge  
**And** båda spelarna anger var sitt synliga spelarnamn  
**And** färgvalet är gjort  

**Then** ska systemet rendera ett tomt bräde av vald storlek  
**And** visa båda spelarnas namn och färg i turindikatorn  
**And** partiet ska innehålla exakt två spelare  
**And** svart ska göra första draget.

---

### AC-18-02: Turen växlar mellan spelarna på samma enhet

**Relaterade krav:** FR-21.4, FR-08.4, FR-08.6

**Given** att ett lokalt parti pågår  
**And** det är spelare A:s tur  

**When** spelare A placerar en sten på en ledig punkt  

**Then** ska turindikatorn visa spelare B:s namn och färg  
**And** nästa drag ska registreras med spelare B:s färg.

---

### AC-18-03: Fel spelare försöker göra ett drag (UC-18 AF-02)

**Relaterade krav:** FR-08.3, FR-21.4

**Given** att ett lokalt parti pågår  
**And** det är spelare B:s tur  

**When** ett drag försöker göras med spelare A:s färg  

**Then** ska systemet avvisa draget  
**And** brädet ska vara oförändrat  
**And** turen ska ligga kvar hos spelare B.

> **Testnot.** I ett lokalt parti finns ingen teknisk skillnad mellan spelarna — det är samma
> enhet, samma session och samma inmatning. Systemet kan bara avvisa draget utifrån vems tur det
> är, inte utifrån vem som faktiskt rör skärmen. Att "fel spelare gör ett drag" går alltså inte
> att upptäcka i lokalt läge; det som testas är turordningen, inte identiteten. Det är en
> begränsning i användningsfallet och inte i implementationen.

---

### AC-18-04: Båda spelarna vill ha samma färg (UC-18 AF-01)

**Relaterade krav:** FR-04.5, FR-04.6

**Given** att ett lokalt parti konfigureras  
**And** båda spelarna väljer svart  

**When** färgvalet bekräftas  

**Then** ska den spelare som valde först behålla svart  
**And** den andra spelaren ska tilldelas vit  
**And** färgvalet ska låsas när partiet startar.

---

### AC-18-05: Lokalt parti fungerar utan nätverk

**Relaterade krav:** FR-21.5, FR-21.6, NFR-01.4

**Given** att applikationen är laddad  
**And** enheten saknar nätverksanslutning  

**When** spelaren startar ett lokalt parti  
**And** spelarna genomför partiet till ett resultat  

**Then** ska partiet kunna spelas i sin helhet  
**And** ingen inbjudningslänk ska genereras  
**And** inget nätverksanrop ska krävas för att göra ett drag.

> **Testförutsättning.** Nätverket måste stängas av utifrån. Detta är det kriterium som faktiskt
> skiljer lokalt läge från online-läge — utan det testar AC-18-01 till AC-18-04 samma sak som
> AC-10 gör för spel mot vän över nätet.

---

### AC-18-06: Lokalt parti avslutas med ett resultat

**Relaterade krav:** FR-08.9, FR-08.11, FR-20.2, FR-21.4

**Given** att ett lokalt parti pågår  

**When** en av spelarna får exakt fem i rad  

**Then** ska systemet avsluta partiet  
**And** utse den spelaren till vinnare med rätt namn  
**And** visa resultatvyn  
**And** inte tillåta fler drag.

---

### AC-18-07: Brädet är läsbart för båda spelarna

**Relaterade krav:** NFR-06.3, NFR-06.5

**Given** att ett lokalt parti pågår på en pekskärm  

**When** brädet visas  

**Then** ska svarta och vita stenar gå att skilja åt på mer än enbart färg  
**And** varje skärningspunkt ska ha en tryckyta på minst 44 × 44 px.
