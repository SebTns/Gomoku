## Acceptance Tests – UC-NFR-04 Begär radering av data

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.
GDPR-referens: artikel 17.

---

### AC-NFR-04-01: Spelaren begär radering av sina personuppgifter

**Relaterade krav:** FR-30.1, FR-30.3, FR-30.4, NFR-12.1

**Given** att spelaren är inloggad  
**And** har personuppgifter registrerade i systemet  

**When** spelaren begär radering av sina personuppgifter  

**Then** ska systemet registrera begäran med unikt begärande-ID, typ RADERING, status PÅGÅENDE
och tidpunkt  
**And** bekräfta för spelaren att begäran är mottagen  
**And** ange senaste datum då raderingen ska vara genomförd.

---

### AC-NFR-04-02: Overifierad begäran avvisas (UC-NFR-04 AF-03)

**Relaterade krav:** FR-30.2

**Given** att en raderingsbegäran har kommit in för spelare S  
**And** begäran inte kan verifieras som kommande från S  

**When** systemet behandlar begäran  

**Then** ska ingen radering påbörjas  
**And** begäran ska registreras som AVVISAD med orsak  
**And** avsändaren ska informeras om att verifiering krävs.

---

### AC-NFR-04-03: Personuppgifter är raderade efter genomförd radering

**Relaterade krav:** FR-30.5, FR-30.6, FR-30.8, NFR-12.4

**Given** att en verifierad raderingsbegäran för spelare S har genomförts  

**When** systemet söker efter S personuppgifter i databasen  

**Then** ska användarposten (e-post, användarnamn, lösenordshash, avatar-URL) inte finnas kvar  
**And** spelarstatistiken för S inte finnas kvar  
**And** begärans status vara GENOMFÖRD med registrerad tidpunkt.

---

### AC-NFR-04-04: Bevarad speldata går inte att koppla till spelaren

**Relaterade krav:** FR-30.7, NFR-12.5, NFR-12.6

**Given** att spelare S har raderats  
**And** S drag och partier finns kvar i anonymiserad form  

**When** en granskare försöker koppla de bevarade posterna till S  
**And** även ställer samman dem med övriga uppgifter som finns kvar i systemet
(motståndarreferenser, tidsstämplar, partilängd)  

**Then** ska ingen post kunna knytas till S, varken direkt eller genom sammanställningen  
**And** samtyckesregister och begäranden ska finnas kvar i anonymiserad form.

> **Testnot.** Andra When-raden är den som gör kriteriet meningsfullt. Anonymisering som bara
> nollställer ett spelar-ID håller inte om partiet fortfarande går att identifiera via
> motståndaren och tidpunkten. `00-begreppslista.md` definierar anonymisering som oåterkallelig
> och till skillnad från pseudonymisering — det är den definitionen som testas här.

---

### AC-NFR-04-05: Personuppgifter kan inte återskapas

**Relaterade krav:** FR-30.13, NFR-12.4

**Given** att spelare S har raderats och raderingen är markerad som GENOMFÖRD  

**When** en granskare söker efter S personuppgifter i var och en av följande sökvägar:
databasen, den senaste säkerhetskopian, applikationsloggen, en ny dataexport och sökindexet  

**Then** ska inga personuppgifter om S kunna läsas ut från någon av dessa sökvägar.

> **Anmärkning om vad detta test faktiskt visar.** Kravet är ett negativt påstående: ett
> tillstånd ska vara omöjligt. Ett sådant krav går inte att bevisa genom test, bara att
> falsifiera. Ett godkänt test visar att uppgifterna inte gick att hitta i fem namngivna
> sökvägar — inte att de är omöjliga att återskapa. De fem sökvägarna är därför uppräknade i
> kriteriet i stället för att gömmas bakom ordet "inte kan återställas". Varje ny lagringsplats
> som tillkommer i systemet måste läggas till i listan, annars slutar testet tyst att täcka
> kravet. Se `10-reflektioner.md`.

---

### AC-NFR-04-06: Bekräftelse på genomförd radering skickas

**Relaterade krav:** FR-30.9, NFR-12.3, NFR-07.1

**Given** att raderingen av spelare S är genomförd  

**When** systemet avslutar raderingen  

**Then** ska ett bekräftelsemeddelande skickas till S registrerade e-postadress  
**And** meddelandet ska skickas innan åtkomsten till kontot återkallas  
**And** överföringen ska ske över TLS 1.2 eller senare.

---

### AC-NFR-04-07: Raderingen genomförs inom 30 dagar

**Relaterade krav:** FR-30.10, NFR-12.2, NFR-12.7, SR-03.2

**Given** att en verifierad raderingsbegäran togs emot vid tidpunkt T  
**And** systemet körs med simulerad tid  

**When** klockan flyttas fram till T plus 30 dagar  

**Then** ska begärans status vara GENOMFÖRD  
**And** raderingen ska ha utförts.

> **Testnot.** 30-dagarsgränsen gör kravet testbart i teorin men opraktiskt i en testsvit: ingen
> pipeline väntar en månad. NFR-12.7 finns just för att göra skillnaden hanterbar — kravet
> verifieras mot en simulerad klocka. Det är en annan sak än att verifiera att produktionsjobbet
> faktiskt kör inom 30 dagar, och den skillnaden är värd att vara medveten om.

---

### AC-NFR-04-08: Radering kan inte slutföras i tid (UC-NFR-04 AF-01)

**Relaterade krav:** FR-30.11

**Given** att en verifierad raderingsbegäran togs emot vid tidpunkt T  
**And** raderingen inte kan slutföras inom 30 dagar  

**When** klockan passerar T plus 30 dagar  

**Then** ska dataskyddsombudet underrättas  
**And** spelaren ska informeras om förseningen och ett nytt datum  
**And** begärans status ska fortfarande vara PÅGÅENDE.

---

### AC-NFR-04-09: Rättslig skyldighet hindrar fullständig radering (UC-NFR-04 AF-02)

**Relaterade krav:** FR-30.12

**Given** att en verifierad raderingsbegäran finns för spelare S  
**And** en del av S uppgifter omfattas av en rättslig lagringsskyldighet  

**When** systemet genomför raderingen  

**Then** ska alla uppgifter som inte omfattas av skyldigheten raderas  
**And** S ska informeras om vilka uppgifter som bevaras  
**And** den rättsliga grunden ska anges  
**And** undantaget ska dokumenteras av dataskyddsombudet.
