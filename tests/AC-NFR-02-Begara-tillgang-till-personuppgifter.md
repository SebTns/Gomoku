## Acceptance Tests – UC-NFR-02 Begära tillgång till personuppgifter

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.
GDPR-referens: artikel 15.

---

### AC-NFR-02-01: Spelaren begär tillgång till sina personuppgifter

**Relaterade krav:** FR-27.1, FR-27.3, NFR-10.1

**Given** att spelaren är registrerad och inloggad  

**When** spelaren begär tillgång till sina personuppgifter  

**Then** ska systemet registrera begäran med unikt begärande-ID, typen ÅTKOMST, status och tidpunkt  
**And** bekräfta för spelaren att begäran är mottagen.

---

### AC-NFR-02-02: Overifierad begäran avvisas

**Relaterade krav:** FR-27.2

**Given** att en begäran om tillgång kommer in  
**And** avsändaren inte kan verifieras som den registrerade spelaren  

**When** systemet behandlar begäran  

**Then** ska inga personuppgifter lämnas ut.

---

### AC-NFR-02-03: Exporten är fullständig och strukturerad

**Relaterade krav:** FR-27.4, FR-27.5, NFR-10.2

**Given** att spelaren har ett konto med e-postadress, synligt namn, spelhistorik och ett sparat cookie-val  

**When** exporten för spelarens begäran skapas  

**Then** ska den innehålla samtliga dessa uppgifter  
**And** vara i ett strukturerat, maskinläsbart format (t.ex. JSON)  
**And** inte innehålla lösenordet, varken i klartext eller som hash (NFR-07.6).

---

### AC-NFR-02-04: Andra personers uppgifter lämnas inte ut

**Relaterade krav:** FR-27.8

**Given** att spelaren har spelat partier mot andra registrerade spelare  

**When** exporten skapas  

**Then** ska den inte innehålla motståndarnas e-postadresser eller andra personuppgifter om dem.

---

### AC-NFR-02-05: Begäran besvaras inom 30 dagar

**Relaterade krav:** FR-27.6, SR-03.2

**Given** att en verifierad begäran om tillgång registrerades dag 0  

**When** systemtiden i testmiljön flyttas fram till dag 30  

**Then** ska begäran ha status GENOMFÖRD  
**And** spelaren ska ha fått tillgång till exporten.

---

### AC-NFR-02-06: Begäran kan inte behandlas (UC-NFR-02 AF-01)

**Relaterade krav:** FR-27.7, NFR-04.1

**Given** att spelaren skickar en begäran  
**And** begäran inte kan behandlas  

**When** systemet tar emot begäran  

**Then** ska spelaren informeras om orsaken på engelska  
**And** kunna försöka igen.
