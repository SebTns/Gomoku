## Acceptance Tests – UC-NFR-05 Ta bort konto (GDPR-självbetjäning)

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.
GDPR-referens: artikel 17.

UC-NFR-05 är GDPR-ramen runt kontoborttagningen. Gränssnittsflödet testas av AC-23-01 –
AC-23-07 och själva raderingen av AC-NFR-04-01 – AC-NFR-04-09. Kriterierna nedan täcker bara
det som är unikt för UC-NFR-05: tvåstegsbekräftelsen via e-post och den slutliga
e-postbekräftelsen.

> **Not.** UC-NFR-05 kräver två bekräftelsesteg (lösenord + e-postlänk), men FR-15 kräver bara
> lösenord. AC-NFR-05-02 och AC-NFR-05-03 saknar därför ett FR att peka på tills gruppen har
> beslutat om e-poststeget ska in i FR-15.

---

### AC-NFR-05-01: Raderingsvalet finns i kontoinställningarna

**Relaterade krav:** FR-15.1, NFR-12.1

**Given** att spelaren är inloggad  

**When** spelaren öppnar "Account Settings" → "Privacy & Data"  

**Then** ska valet "Delete Account" finnas och vara valbart.

---

### AC-NFR-05-02: Varning visas före första bekräftelsesteget

**Relaterade krav:** FR-15.3, NFR-12.2

**Given** att spelaren har valt "Delete Account"  

**When** systemet visar raderingsvyn  

**Then** ska varningen synas innan lösenordsfältet kan skickas  
**And** ange att borttagningen inte går att ångra  
**And** ange att personuppgifterna raderas inom 30 dagar  
**And** ange att historiska partier anonymiseras.

---

### AC-NFR-05-03: Lösenordet utlöser ett bekräftelsemejl (steg 1 av 2)

**Relaterade krav:** FR-15.2, NFR-07.1 — *e-poststeget saknar FR, se not*

**Given** att spelaren har läst varningen  

**When** spelaren anger rätt lösenord och väljer "Delete My Account"  

**Then** ska systemet skicka ett bekräftelsemejl med en tidsbegränsad länk  
**And** kontot ska fortfarande vara aktivt.

---

### AC-NFR-05-04: E-postlänken inaktiverar kontot (steg 2 av 2)

**Relaterade krav:** FR-30.1, FR-30.3 — *e-poststeget saknar FR, se not*

**Given** att spelaren har fått bekräftelsemejlet  

**When** spelaren klickar på länken innan den har gått ut  

**Then** ska kontot inaktiveras omedelbart  
**And** en raderingsbegäran med typen RADERING och status PÅGÅR registreras  
**And** raderingen fortsätter enligt AC-NFR-04-01.

---

### AC-NFR-05-05: Kontot går inte att nå efter e-postbekräftelsen

**Relaterade krav:** FR-15.5

**Given** att spelaren har bekräftat via e-postlänken  

**When** spelaren försöker logga in med samma uppgifter  

**Then** ska inloggningen misslyckas  
**And** kontot ska inte gå att återställa.

---

### AC-NFR-05-06: Bekräftelse skickas när raderingen är klar

**Relaterade krav:** FR-30.9, FR-30.10, NFR-12.2, NFR-12.3, NFR-12.7

**Given** att en raderingsbegäran har verifierats dag 0  

**When** systemtiden i testmiljön flyttas fram och raderingen genomförs  

**Then** ska raderingen vara klar senast dag 30  
**And** ett e-postmeddelande på engelska om genomförd radering skickas.
