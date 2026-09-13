## Acceptance Tests – UC-28 Rapportera ett tekniskt problem

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-28-01: Rapportera ett tekniskt problem

**Relaterade krav:** FR-28.1 – FR-28.7, NFR-03.2, NFR-04.4

**Given** att spelaren befinner sig i spelet  
**And** spelaren har upptäckt ett tekniskt problem  

**When** spelaren öppnar funktionen "Rapportera problem"  
**And** beskriver problemet  
**And** skickar rapporten  

**Then** ska systemet kontrollera att en beskrivning finns  
**And** registrera problemrapporten  
**And** tilldela rapporten ett unikt rapport-ID och en tidsstämpel  
**And** visa en bekräftelse inom 3 sekunder.

---

### AC-28-02: Beskrivning saknas (UC-28 AF-01)

**Relaterade krav:** FR-28.3, FR-28.4, NFR-04.1

**Given** att spelaren har öppnat rapportformuläret  
**And** beskrivningsfältet är tomt  

**When** spelaren väljer att skicka rapporten  

**Then** ska systemet informera spelaren om att en beskrivning krävs  
**And** inte registrera någon rapport  
**And** låta spelaren komplettera beskrivningen och skicka igen.

---

### AC-28-03: Problemrapporten kan inte registreras (UC-28 AF-02)

**Relaterade krav:** FR-28.8, FR-28.9, NFR-03.5, NFR-04.1, NFR-04.6

**Given** att spelaren har fyllt i en beskrivning av ett tekniskt problem  
**And** nätverksanslutningen till servern är bruten  

**When** spelaren försöker skicka rapporten  

**Then** ska systemet informera spelaren om att rapporten inte har registrerats  
**And** spara rapporten lokalt  
**And** erbjuda minst en väg vidare (försök igen eller tillbaka till spelet).

> **Testförutsättning.** Nätverksfelet måste framkallas utifrån — via en nätverksstubb, en
> avstängd anslutning eller en proxy som avvisar anropet. Förutsättningen ligger alltså utanför
> applikationen, och testet kan inte skrivas som ett rent enhetstest. Det är en direkt konsekvens
> av att NFR-03.5 handlar om systemets beteende när systemet inte kan nås.

---

### AC-28-04: Lokalt sparad rapport skickas om (UC-28 AF-04)

**Relaterade krav:** FR-28.9, NFR-03.5

**Given** att en rapport har sparats lokalt efter ett misslyckat försök  
**And** nätverksanslutningen är återställd  

**When** spelaren väljer att skicka om den sparade rapporten  

**Then** ska systemet registrera rapporten  
**And** tilldela den ett unikt rapport-ID  
**And** ta bort den lokalt sparade kopian.

---

### AC-28-05: Spelaren avbryter rapporteringen (UC-28 AF-03)

**Relaterade krav:** FR-28.10

**Given** att spelaren har öppnat rapportformuläret och skrivit en beskrivning  

**When** spelaren väljer att avbryta  

**Then** ska systemet stänga rapportformuläret  
**And** ingen problemrapport ska registreras  
**And** ingenting ska sparas lokalt  
**And** spelaren ska återgå till spelet.

---

### AC-28-06: Rapporteringen påverkar inte ett pågående parti

**Relaterade krav:** NFR-03.1, NFR-03.4

**Given** att ett parti pågår  
**And** det är spelarens tur  

**When** spelaren öppnar funktionen "Rapportera problem"  

**Then** ska funktionen gå att nå inom högst två klick från den aktuella vyn  
**And** partiet ska behålla status PÅGÅENDE  
**And** brädet, turen och dragräknaren ska vara oförändrade när formuläret stängs.

---

### AC-28-07: Spelaren informeras om vilka uppgifter som bifogas

**Relaterade krav:** NFR-03.3, NFR-03.6, NFR-03.7, NFR-04.5

**Given** att spelaren har öppnat rapportformuläret  

**When** formuläret visas  

**Then** ska systemet visa att webbläsare, tidpunkt, parti-ID och synligt spelarnamn bifogas  
**And** inga andra personuppgifter ska bifogas rapporten  
**And** den tekniska felloggen ska inte innehålla några personuppgifter.

> **Anmärkning.** Spelarnamnet är en personuppgift enligt `00-begreppslista.md`. NFR-03.3 sade
> tidigare "utan personuppgifter utöver spelarnamnet", vilket läste som motsatsen. Kravet är
> uppdelat i NFR-03.3, NFR-03.6 och NFR-03.7 så att insamlingen är uttalad och minimerad i
> stället för bortdefinierad.
