## Acceptance Tests – UC-09 Motståndare gör drag

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

UC-09 är spegelbilden av UC-02: samma bräde, men draget kommer från motståndaren i stället för
från spelaren. Kriterierna nedan testar det spelaren ska kunna observera.

---

### AC-09-01: Motståndaren gör ett giltigt drag

**Relaterade krav:** FR-06.2, FR-06.3, FR-08.4, FR-08.5, FR-08.8

**Given** att ett parti pågår  
**And** det är motståndarens tur  

**When** motståndaren placerar en sten på en ledig skärningspunkt  

**Then** ska stenen placeras på punkten  
**And** den senast placerade stenen ska markeras  
**And** turen ska gå tillbaka till spelaren  
**And** systemet ska kontrollera vinstvillkoret efter draget.

---

### AC-09-02: Systemet visar att datorn beräknar

**Relaterade krav:** FR-06.4, NFR-02.3

**Given** att ett parti mot datorn pågår  

**When** det blir datorns tur  

**Then** ska systemet visa att datorn beräknar sitt drag  
**And** draget ska levereras inom 3 sekunder  
**And** indikeringen ska försvinna när draget är gjort.

---

### AC-09-03: Motståndaren väljer en upptagen punkt (UC-09 AF-01)

**Relaterade krav:** FR-06.3, FR-08.2

**Given** att ett parti pågår  
**And** det är motståndarens tur  
**And** en sten redan ligger på punkten P  

**When** motståndaren försöker placera en sten på P  

**Then** ska systemet avvisa draget  
**And** turen ska ligga kvar hos motståndaren  
**And** brädet ska vara oförändrat.

---

### AC-09-04: Motståndarens drag uteblir (UC-09 AF-02)

**Relaterade krav:** NFR-04.3, NFR-08.2

**Given** att ett online-parti mot en vän pågår  
**And** det är motståndarens tur  

**When** motståndaren kopplas från  

**Then** ska systemet meddela spelaren inom 15 sekunder  
**And** partiet ska inte hamna i ett läge där ingen kan göra ett giltigt drag  
**And** spelaren ska ha minst en väg vidare.

---

### AC-09-05: Datorn kan inte beräkna ett drag

**Relaterade krav:** FR-06.6, FR-06.7, FR-06.9, NFR-04.1

**Given** att ett parti mot datorn pågår  
**And** datorns drag inte kan beräknas  

**When** det blir datorns tur  

**Then** ska systemet försöka beräkna draget en gång till  
**And** vid ett andra misslyckande visa ett felmeddelande  
**And** pausa partiet med bevarat partitillstånd  
**And** låta spelaren välja mellan att försöka igen och att avsluta partiet.

---

### AC-09-06: Motståndaren vinner

**Relaterade krav:** FR-06.5, FR-08.9, FR-08.13, FR-08.14, NFR-02.4

**Given** att ett parti pågår  
**And** motståndaren har fyra stenar i en obruten rad med en ledig ände  

**When** motståndaren placerar sin femte sten i raden  

**Then** ska partiet avslutas inom 100 ms efter draget  
**And** motståndaren ska utses till vinnare  
**And** spelaren ska få resultatet presenterat som en förlust (→ UC-15)  
**And** inga fler drag ska tillåtas.
