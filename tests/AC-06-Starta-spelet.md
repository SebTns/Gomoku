## Acceptance Tests – UC-06 Starta spelet

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-06-01: Applikationen öppnas

**Relaterade krav:** FR-01.1, FR-01.2, NFR-02.1, NFR-01.4

**Given** att spelaren har en enhet med en modern webbläsare  
**And** känner till spelets adress  

**When** spelaren öppnar adressen  

**Then** ska startsidan vara färdigrenderad inom 2 sekunder vid 25 Mbit/s  
**And** visa valen "Play vs Computer", "Play with a Friend" och "Game Rules"  
**And** ingen installation ska krävas.

---

### AC-06-02: Spelet är spelbart utan inloggning

**Relaterade krav:** FR-01.3

**Given** att spelaren inte är inloggad  

**When** spelaren väljer "Play vs Computer" från startsidan  

**Then** ska partiet kunna startas och genomföras  
**And** ingen inloggning ska krävas.

---

### AC-06-03: Applikationen kan inte laddas (UC-06 AF-01)

**Relaterade krav:** FR-01.4, NFR-04.1, NFR-04.6

**Given** att spelaren har öppnat adressen  
**And** applikationen inte kan laddas  

**When** sidan visas  

**Then** ska systemet visa ett meddelande om att spelet inte kunde startas  
**And** erbjuda spelaren att försöka igen.

---

### AC-06-04: Ett pågående parti kan återupptas (UC-06 AF-02)

**Relaterade krav:** FR-01.2, NFR-04.2

**Given** att spelaren har ett pågående parti sedan tidigare  

**When** spelaren öppnar applikationen  

**Then** ska valet "Resume Game" visas  
**And** partitillståndet ska återställas när valet görs  
**And** brädet, turen och dragräknaren ska vara desamma som när partiet lämnades.

---

### AC-06-05: Startsidan nås från valfri vy

**Relaterade krav:** FR-01.5

**Given** att spelaren befinner sig i en godtycklig vy i spelet  

**When** spelaren navigerar mot startsidan  

**Then** ska startsidan nås inom en (1) navigering.

---

### AC-06-06: Startsidan fungerar på liten skärm

**Relaterade krav:** NFR-01.2, NFR-01.5, NFR-01.6, NFR-06.5

**Given** att spelaren använder en enhet med 360 px skärmbredd  

**When** startsidan visas  

**Then** ska hela innehållet rymmas utan horisontell scroll  
**And** sidan ska fungera i både stående och liggande läge  
**And** varje tryckyta ska vara minst 44 × 44 px.
