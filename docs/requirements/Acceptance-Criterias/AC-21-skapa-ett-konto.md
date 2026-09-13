## Acceptance Tests – UC-21 Skapa ett konto

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-21-01: Spelaren skapar ett konto

**Relaterade krav:** FR-13.1, FR-13.2, FR-13.4, NFR-07.1

**Given** att spelaren befinner sig på startsidan  
**And** e-postadressen inte är registrerad sedan tidigare  

**When** spelaren väljer "Skapa konto"  
**And** anger synligt namn, en giltig e-postadress och ett lösenord på minst 8 tecken  
**And** bekräftar  

**Then** ska systemet skapa kontot  
**And** visa en bekräftelse  
**And** logga in spelaren automatiskt  
**And** all kommunikation ska ske över TLS 1.2 eller senare.

---

### AC-21-02: E-postadressen är redan registrerad (UC-21 AF-01)

**Relaterade krav:** FR-13.3, FR-13.5

**Given** att e-postadressen redan är registrerad i systemet  

**When** spelaren försöker skapa ett konto med samma e-postadress  

**Then** ska systemet avvisa registreringen  
**And** informera spelaren  
**And** erbjuda inloggning i stället  
**And** inget nytt konto ska skapas.

---

### AC-21-03: Uppgifterna uppfyller inte kraven (UC-21 AF-02)

**Relaterade krav:** FR-13.2, FR-13.5, FR-02.2, FR-02.3

**Given** att spelaren har öppnat registreringsformuläret  

**When** spelaren anger ett lösenord på färre än 8 tecken, eller en e-postadress i ogiltigt format,
eller ett synligt namn som bryter mot FR-02.2  
**And** bekräftar  

**Then** ska systemet avvisa registreringen  
**And** markera det fält som är fel  
**And** visa vilken regel som inte uppfylls  
**And** låta spelaren korrigera och skicka igen  
**And** inget konto ska skapas.

---

### AC-21-04: Spelaren avbryter registreringen (UC-21 AF-03)

**Relaterade krav:** FR-13.5

**Given** att spelaren har fyllt i registreringsformuläret  

**When** spelaren väljer "Avbryt"  

**Then** ska inget konto skapas  
**And** spelaren ska återgå till startsidan  
**And** inga inmatade uppgifter ska sparas.

---

### AC-21-05: Lösenordet lagras aldrig i klartext

**Relaterade krav:** NFR-07.6, NFR-04.5

**Given** att ett konto har skapats med lösenordet P  

**When** en granskare söker efter P i databasen, applikationsloggen och en dataexport  

**Then** ska P inte förekomma i klartext någonstans  
**And** det lagrade värdet ska vara en bcrypt-hash.

> **Varför detta kriterium finns.** `00-begreppslista.md` anger bcrypt och att klartextlösenord
> aldrig lagras eller loggas, men det stod inte som ett krav någonstans — bara som en definition.
> En definition testas inte. NFR-07.6 är tillagt så att kriteriet har något att referera till.
> Notera samma begränsning som i AC-NFR-04-05: detta test söker i tre namngivna sökvägar och
> bevisar inte frånvaro i alla.

---

### AC-21-06: Registreringen samlar inte in mer än nödvändigt

**Relaterade krav:** NFR-07.4, FR-13.1

**Given** att registreringsformuläret visas  

**When** spelaren granskar vilka fält som krävs  

**Then** ska endast synligt namn, e-postadress och lösenord vara obligatoriska  
**And** inga ytterligare personuppgifter ska krävas för att skapa ett konto.

---

### AC-21-07: E-postverifiering

**Relaterade krav:** —

**Given** att ett konto har skapats  

**When** kontot används första gången  

**Then** ska systemet bete sig enligt gruppens beslut om e-postverifiering.

> **Öppet — kan inte skrivas färdigt än.** UC-21:s öppna fråga är om e-postadressen ska verifieras
> med bekräftelselänk innan kontot aktiveras. Inget FR besvarar den, och FR-13.4 säger tvärtom att
> spelaren loggas in automatiskt efter registrering — vilket förutsätter att verifiering *inte*
> krävs. Beslutet får konsekvenser för UC-NFR-04 och UC-NFR-05, där e-postbekräftelse är själva
> verifieringsmekanismen för en raderingsbegäran (FR-30.2). Ett konto med en overifierad
> e-postadress kan inte radera sig själv på det sättet. Kriteriet står kvar tomt så att
> beroendet syns.
