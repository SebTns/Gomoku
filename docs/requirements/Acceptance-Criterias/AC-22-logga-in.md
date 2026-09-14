## Acceptance Tests – UC-22 Logga in

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-22-01: Spelaren loggar in

**Relaterade krav:** FR-14.1, FR-14.2, NFR-07.1

**Given** att spelaren har ett konto  
**And** befinner sig på inloggningssidan  

**When** spelaren anger rätt e-postadress och lösenord  

**Then** ska systemet skapa en aktiv session  
**And** föra spelaren till huvudmenyn  
**And** visa att spelaren är inloggad  
**And** överföringen ska ske över TLS 1.2 eller senare.

---

### AC-22-02: Fel uppgifter avslöjar inte vilket fält som var fel (UC-22 AF-01)

**Relaterade krav:** FR-14.3, FR-14.5, NFR-07.7

**Given** att e-postadressen A är registrerad i systemet  
**And** e-postadressen B inte är registrerad  

**When** spelaren loggar in med A och fel lösenord  
**And** därefter loggar in med B och valfritt lösenord  

**Then** ska systemet visa exakt samma felmeddelande i båda fallen  
**And** svarstiderna ska inte skilja sig åt på ett sätt som avslöjar vilket konto som finns  
**And** ingen session ska skapas.

> **Varför detta kriterium finns.** UC-22 AF-01 beskrev ett "generiskt felmeddelande utan att
> avslöja vilket fält som var fel", men FR-14.3 sade bara "ett felmeddelande". Beteendet fanns
> alltså i användningsfallet men inte i kravet, och ett test skrivet enbart mot FR-14.3 hade
> godkänt ett meddelande som lyder "okänd e-postadress". FR-14.5 och NFR-07.7 är tillagda.
> Den andra Then-raden är med för att ett identiskt meddelande inte hjälper om svarstiden skiljer.

---

### AC-22-03: Kontot låses efter upprepade misslyckade försök (UC-22 AF-02)

**Relaterade krav:** FR-14.6, FR-14.7

**Given** att spelaren har ett konto  

**When** spelaren anger fel lösenord fem gånger i följd  

**Then** ska systemet låsa kontot tillfälligt  
**And** ange när kontot kan användas igen  
**And** ett sjätte inloggningsförsök med rätt lösenord ska avvisas medan låsningen gäller.

---

### AC-22-04: Ett blockerat konto kan inte logga in

**Relaterade krav:** FR-14.4, FR-29.6, FR-29.11

**Given** att spelaren är tillfälligt blockerad av en administratör (UC-29)  

**When** spelaren försöker logga in  

**Then** ska systemet förhindra inloggningen  
**And** informera spelaren om att en blockering gäller och när den upphör  
**And** inte avslöja vem som har rapporterat spelaren.

> **Not om spårbarheten.** Detta är den enda punkten där UC-22 och UC-29 möts. Ingen av filerna
> refererar till den andra — UC-29 beskriver att spelaren förhindras delta i nya partier och
> UC-22 att inloggning förhindras om kontot är tillfälligt blockerat, utan att någonstans slå
> fast att det är samma blockering. Kriteriet knyter ihop dem.

---

### AC-22-05: Tekniskt fel vid inloggning (UC-22 AF-03)

**Relaterade krav:** FR-14.8, NFR-04.1, NFR-04.6

**Given** att spelaren har angett rätt uppgifter  
**And** ett tekniskt fel uppstår vid validering  

**When** spelaren försöker logga in  

**Then** ska systemet visa ett felmeddelande på engelska som beskriver vad som hänt  
**And** erbjuda möjlighet att försöka igen  
**And** spelaren ska förbli utloggad.

---

### AC-22-06: Utloggat läge är fortfarande spelbart

**Relaterade krav:** FR-01.3

**Given** att spelaren inte är inloggad  

**When** spelaren väljer att spela mot datorn från startsidan  

**Then** ska partiet kunna startas och genomföras  
**And** ingen inloggning ska krävas.
