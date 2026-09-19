## Acceptance Tests – UC-25 Välj inloggningsmetod

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-25-01: Tillgängliga inloggningsmetoder visas

**Relaterade krav:** FR-25.1, FR-25.2

**Given** att spelaren har ett registrerat konto  
**And** befinner sig på inloggningssidan  

**When** inloggningssidan visas  

**Then** ska systemet visa en lista över tillgängliga inloggningsmetoder  
**And** listan ska innehålla e-post med lösenord samt de externa metoder som är kopplade  
**And** spelaren ska kunna välja en av dem.

---

### AC-25-02: Vald metod leder till rätt flöde

**Relaterade krav:** FR-25.3, FR-25.5, NFR-07.1

**Given** att inloggningssidan visar tillgängliga metoder  

**When** spelaren väljer en metod  

**Then** ska systemet dirigera spelaren till det inloggningsflöde som hör till metoden  
**And** en aktiv användarsession ska skapas när inloggningen är slutförd  
**And** överföringen ska ske över TLS 1.2 eller senare.

---

### AC-25-03: Vald metod är otillgänglig (UC-25 AF-01)

**Relaterade krav:** FR-25.4, NFR-04.1, NFR-04.6

**Given** att inloggningssidan visar tillgängliga metoder  
**And** metoden M är otillgänglig  

**When** spelaren väljer M  

**Then** ska systemet visa ett tydligt felmeddelande om att metoden är otillgänglig  
**And** låta spelaren välja en annan metod  
**And** låta spelaren avbryta  
**And** ingen session ska skapas.

---

### AC-25-04: Listan avslöjar inte andra konton

**Relaterade krav:** NFR-07.7, FR-25.1

**Given** att en person som inte är inloggad öppnar inloggningssidan  

**When** listan över metoder visas  

**Then** ska samma metoder visas oavsett vilken e-postadress som matas in  
**And** listan ska inte avslöja vilka metoder ett visst konto har kopplade.

> **Varför detta kriterium finns.** FR-25.1 säger att systemet ska visa *tillgängliga*
> inloggningsmetoder. Om listan anpassas efter den inmatade e-postadressen blir den ett sätt att
> ta reda på vilka konton som finns och hur de loggar in — samma läcka som NFR-07.7 stänger för
> felmeddelanden.

---

### AC-25-05: Tangentbordsnavigering

**Relaterade krav:** NFR-06.1, NFR-06.4

**Given** att inloggningssidan visas  

**When** spelaren navigerar med tangentbordet  

**Then** ska varje inloggningsmetod gå att nå och aktivera  
**And** den aktuella metoden ska vara synligt markerad.
