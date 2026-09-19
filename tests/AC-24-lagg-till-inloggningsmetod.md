## Acceptance Tests – UC-24 Lägg till inloggningsmetod

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

Kriterierna nedan gäller att *lägga till* en metod. Att *välja* metod vid inloggning är UC-25 och
testas av AC-25.

---

### AC-24-01: Spelaren kopplar en ny inloggningsmetod

**Relaterade krav:** FR-16.1, FR-16.3, FR-16.4, NFR-07.1

**Given** att spelaren är inloggad  
**And** befinner sig i kontoinställningarna  
**And** metoden M inte är kopplad till kontot  

**When** spelaren väljer "Add Login Method"  
**And** väljer metoden M  
**And** bekräftar sitt nuvarande lösenord  
**And** godkänner kopplingen hos den externa leverantören  

**Then** ska systemet koppla M till kontot  
**And** visa en bekräftelse med samtliga kopplade metoder  
**And** all kommunikation ska ske över TLS 1.2 eller senare.

---

### AC-24-02: Lösenordet måste bekräftas innan metoden läggs till

**Relaterade krav:** FR-16.3

**Given** att spelaren är inloggad och har valt en metod att lägga till  

**When** spelaren anger fel nuvarande lösenord  

**Then** ska systemet avvisa tillägget  
**And** inte skicka spelaren vidare till den externa leverantören  
**And** kontots befintliga metoder ska vara oförändrade.

> **Varför detta kriterium finns.** FR-16.3 är det som hindrar att någon som hittar en olåst
> session kopplar sin egen identitet till kontot och därefter kan logga in när som helst. Utan ett
> negativt testfall verifieras kravet aldrig — AC-24-01 passerar även om lösenordskontrollen bara
> visas och inte kontrolleras.

---

### AC-24-03: Metoden är redan kopplad till kontot (UC-24 AF-01)

**Relaterade krav:** FR-16.5

**Given** att metoden M redan är kopplad till spelarens konto  

**When** spelaren försöker lägga till M igen  

**Then** ska systemet informera spelaren om att metoden redan är kopplad  
**And** inte lägga till den en andra gång  
**And** listan över kopplade metoder ska vara oförändrad.

---

### AC-24-04: Metoden är kopplad till ett annat konto

**Relaterade krav:** FR-16.2

**Given** att metoden M redan är kopplad till ett annat konto i systemet  

**When** spelaren försöker koppla M till sitt konto  

**Then** ska systemet avvisa kopplingen  
**And** informera spelaren  
**And** inte avslöja vilket konto M är kopplat till.

> **Not.** Sista Then-raden följer samma princip som NFR-07.7: ett felmeddelande får inte gå att
> använda för att kartlägga vilka konton som finns. FR-16.2 säger bara att systemet ska verifiera
> att metoden inte redan är kopplad till ett annat konto — inte hur det ska meddelas.

---

### AC-24-05: Leverantören nekar kopplingen (UC-24 AF-02)

**Relaterade krav:** FR-16.6, NFR-04.1

**Given** att spelaren har valt en metod och bekräftat sitt lösenord  

**When** den externa identitetsleverantören nekar kopplingen  

**Then** ska systemet informera spelaren  
**And** kontots befintliga metoder ska vara oförändrade  
**And** felmeddelandet ska ange nästa steg för spelaren.

---

### AC-24-06: Spelaren avbryter hos leverantören (UC-24 AF-03)

**Relaterade krav:** FR-16.7

**Given** att spelaren har skickats vidare till den externa leverantörens flöde  

**When** spelaren avbryter innan kopplingen godkänns  

**Then** ska ingen metod läggas till  
**And** spelaren ska återföras till kontoinställningarna  
**And** kontot ska vara oförändrat.

---

### AC-24-07: Leverantören får inte mer uppgifter än nödvändigt

**Relaterade krav:** NFR-07.8, NFR-07.4

**Given** att spelaren kopplar en extern inloggningsmetod  

**When** systemet begär behörighet hos leverantören  

**Then** ska endast den behörighet som krävs för att identifiera kontot begäras  
**And** ingen spelhistorik eller annan personuppgift ska delas med leverantören.

> **Not.** UC-24 anger NFR-07.1 (TLS) som enda särskilda krav, men den externa leverantören är en
> tredje part enligt UC-NFR-03 och NFR-11.1. Kopplingen innebär att personuppgifter behandlas av
> någon annan än oss, vilket är precis det UC-NFR-03 säger att spelaren ska informeras om.
> NFR-07.8 är tillagt eftersom inget krav begränsade vad som delas.

---

### AC-24-08: Ta bort en inloggningsmetod

**Relaterade krav:** —

**Given** att spelaren har två kopplade inloggningsmetoder  

**When** spelaren tar bort den ena  

**Then** ska systemet bete sig enligt gruppens beslut i UC-24:s öppna fråga.

> **Öppet — kan inte skrivas färdigt än.** UC-24 frågar om en metod ska gå att ta bort och om minst
> en alltid måste finnas kvar. Inget FR besvarar det. Frågan är inte kosmetisk: tas den sista
> metoden bort blir kontot omöjligt att logga in på men fortsätter att finnas, med personuppgifter
> som spelaren inte längre kommer åt och därför inte kan begära radering av via självbetjäning
> (FR-30.2). Kriteriet står kvar tomt så att beroendet mot UC-NFR-04 syns i täckningen.
