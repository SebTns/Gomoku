## Acceptance Tests – UC-NFR-08 Dataskyddsombudet granskar en raderingsbegäran

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-NFR-08-01: Eskalerade begäranden listas med kvarvarande tid

**Relaterade krav:** FR-32.1, FR-32.2

**Given** att dataskyddsombudet är inloggat  
**And** två raderingsbegäranden har eskalerats enligt UC-NFR-04 AF-01 och AF-02  

**When** dataskyddsombudet öppnar listan över eskalerade begäranden  

**Then** ska båda begärandena visas  
**And** varje rad ska visa begärande-ID, mottagningsdatum, kvarvarande tid till 30-dagarsgränsen
och orsaken till eskaleringen.

---

### AC-NFR-08-02: Datakategoriernas status visas

**Relaterade krav:** FR-32.3, NFR-12.5

**Given** att en eskalerad begäran är öppnad  

**When** dataskyddsombudet granskar begäran  

**Then** ska systemet visa vilka datakategorier som är raderade  
**And** vilka som är anonymiserade  
**And** vilka som är kvar.

---

### AC-NFR-08-03: Beslutet registreras spårbart

**Relaterade krav:** FR-32.4, FR-32.5, FR-32.6, NFR-12.6

**Given** att dataskyddsombudet har granskat en begäran  

**When** dataskyddsombudet registrerar ett beslut med rättslig grund och motivering  

**Then** ska beslutet sparas med tidpunkt och beslutsfattande dataskyddsombud  
**And** den registrerade spelaren ska underrättas om utfallet  
**And** beslutet ska bevaras i minst 3 år i anonymiserad form.

---

### AC-NFR-08-04: Varning fem dagar före fristen

**Relaterade krav:** FR-32.7, NFR-12.7

**Given** att en eskalerad begäran togs emot vid tidpunkt T  
**And** inget beslut har registrerats  
**And** systemet körs med simulerad tid  

**When** klockan flyttas fram till T plus 25 dagar  

**Then** ska dataskyddsombudet varnas om att 5 dagar återstår.

---

### AC-NFR-08-05: Passerad frist markeras som avvikelse

**Relaterade krav:** FR-32.8, SR-03.2, SR-03.4

**Given** att en eskalerad begäran togs emot vid tidpunkt T  
**And** inget beslut har registrerats  
**And** systemet körs med simulerad tid  

**When** klockan flyttas fram till T plus 31 dagar  

**Then** ska begäran markeras som försenad  
**And** avvikelsen ska bevaras för efterlevnadsgranskning.

> **Anmärkning.** Detta kriterium testar att systemet *upptäcker och dokumenterar* ett
> regelbrott — inte att brottet undviks. Skillnaden är avsiktlig: 30-dagarsgränsen kan missas av
> skäl som ligger utanför systemet, och det som då krävs enligt GDPR är att avvikelsen är känd och
> spårbar. Ett testfall kan verifiera dokumentationen. Det kan inte verifiera efterlevnaden.
