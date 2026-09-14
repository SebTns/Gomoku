## Acceptance Tests – UC-17 Spelhistorik

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-17-01: Spelaren öppnar sin spelhistorik

**Relaterade krav:** FR-11.1, FR-11.2

**Given** att spelaren har ett konto med avslutade partier i historiken  

**When** spelaren väljer "Spelhistorik"  

**Then** ska systemet visa en lista över spelarens tidigare avslutade partier  
**And** varje rad ska visa datum, motståndare, brädstorlek, svårighetsgrad och resultat.

---

### AC-17-02: Historiken kan sorteras

**Relaterade krav:** FR-11.3

**Given** att spelhistoriken visas med minst tre partier  

**When** spelaren sorterar på datum, resultat eller motståndare  

**Then** ska listan ordnas om enligt den valda sorteringen.

---

### AC-17-03: Ett tidigare parti kan öppnas

**Relaterade krav:** FR-11.4

**Given** att spelhistoriken visas  

**When** spelaren öppnar ett tidigare parti  

**Then** ska systemet visa dragföljden för det partiet  
**And** dragen ska visas i den ordning de gjordes.

---

### AC-17-04: Ingen historik finns (UC-17 AF-01)

**Relaterade krav:** FR-11.1, NFR-04.6

**Given** att spelaren inte har några avslutade partier  

**When** spelaren väljer "Spelhistorik"  

**Then** ska systemet visa en tom lista med en kort förklaring  
**And** erbjuda en väg vidare till att starta ett parti.

---

### AC-17-05: Historiken kan inte hämtas (UC-17 AF-02)

**Relaterade krav:** NFR-04.1, NFR-04.6

**Given** att spelaren har valt "Spelhistorik"  
**And** historiken inte kan hämtas  

**When** vyn visas  

**Then** ska systemet visa ett felmeddelande på svenska  
**And** erbjuda möjlighet att försöka igen.

---

### AC-17-06: Gästspelares partidata raderas efter 30 dagar

**Relaterade krav:** FR-11.5, NFR-07.5, NFR-12.7

**Given** att en gästspelare avslutade ett parti vid tidpunkt T  
**And** systemet körs med simulerad tid  

**When** klockan flyttas fram till T plus 31 dagar  

**Then** ska partidata för det partiet vara raderad.

> **Testnot.** Kravet går inte att verifiera genom att vänta ut 30 dagar i en testsvit. Samma
> problem, och samma lösning, som för NFR-12.2 — se `08-use-cases-och-test-cases.md` 8.5.
