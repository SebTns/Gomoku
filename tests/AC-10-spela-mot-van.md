## Acceptance Tests – UC-10 Spela mot vän

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

UC-10 börjar där UC-03 slutar: inbjudan är accepterad och partiet är igång. Inbjudningsflödet
testas av AC-03, och lokalt spel på samma enhet av AC-18.

---

### AC-10-01: Partiet startar när båda har anslutit

**Relaterade krav:** FR-07.5, FR-07.9, FR-08.1

**Given** att en inbjudan har skapats  
**And** vännen har anslutit med länken  

**When** partiet startar  

**Then** ska båda spelarnas synliga spelarnamn visas för båda  
**And** brädet ska visas för båda spelarna  
**And** svart ska göra första draget.

---

### AC-10-02: Ett drag syns hos motståndaren

**Relaterade krav:** FR-08.4, NFR-02.6

**Given** att ett online-parti mot en vän pågår  
**And** det är spelarens tur  

**When** spelaren placerar en sten  

**Then** ska draget synas hos vännen inom 500 ms  
**And** turindikatorn ska visa vännens namn hos båda spelarna.

> **Testnot.** Detta kriterium kräver två klienter samtidigt. Det går inte att verifiera i ett
> enhetstest av spellogiken, eftersom det som testas är synkroniseringen mellan två sessioner —
> inte reglerna. Testförutsättningen ligger alltså utanför den kod NFR-09.1 gör enhetstestbar.

---

### AC-10-03: Vännen kopplas från (UC-10 AF-01)

**Relaterade krav:** NFR-04.2, NFR-04.3

**Given** att ett online-parti mot en vän pågår  

**When** vännen förlorar anslutningen  

**Then** ska systemet meddela spelaren inom 15 sekunder  
**And** partiet ska pausas med bevarat partitillstånd  
**And** vännen ska kunna återansluta inom 5 minuter och fortsätta partiet.

---

### AC-10-04: En tredje part försöker ansluta (UC-10 AF-02)

**Relaterade krav:** FR-07.8

**Given** att två spelare redan deltar i partiet  

**When** ytterligare en person försöker ansluta  

**Then** ska anslutningsförsöket avvisas  
**And** partiet ska fortfarande innehålla exakt två spelare  
**And** det pågående partiet ska inte störas.

---

### AC-10-05: Spelaren lämnar partiet i förtid (UC-10 AF-03)

**Relaterade krav:** FR-10.1, FR-10.2, FR-10.3, FR-10.5

**Given** att ett online-parti mot en vän pågår  

**When** spelaren avslutar partiet i förtid och bekräftar  

**Then** ska partiet få status AVSLUTAT  
**And** vännen ska informeras om att partiet avslutats  
**And** ingen vinnare eller förlorare ska registreras.

---

### AC-10-06: Inbjudningslänken är oförutsägbar

**Relaterade krav:** NFR-07.2, FR-07.1

**Given** att ett stort antal inbjudningslänkar har genererats  

**When** koderna analyseras  

**Then** ska varje kod ha minst 128 bitars entropi  
**And** ingen kod ska gå att härleda ur en annan.

> **Anmärkning om testbarhet.** Entropi går inte att mäta på en enskild kod — bara att sannolikgöra
> över en mängd. Testet visar alltså att koderna inte är *uppenbart* förutsägbara, inte att de är
> säkra. Den verkliga verifieringen är en granskning av vilken slumpkälla som används. Samma
> begränsning som i AC-NFR-04-05: ett negativt påstående går att falsifiera, inte bevisa.

---

### AC-10-07: Spelarnamn saneras hos motståndaren

**Relaterade krav:** NFR-07.3, FR-07.9

**Given** att vännen har angett ett spelarnamn som innehåller skript  

**When** partiet startar och namnet visas för spelaren  

**Then** ska namnet visas som text  
**And** inget skript ska köras i spelarens webbläsare.
