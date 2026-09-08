## Acceptance Tests – UC-03 Bjuda in en vän

### AC-03-01: Bjuda in en vän och starta partiet

**Relaterade krav:** FR-07.1, FR-07.2, FR-07.4, FR-07.5, FR-07.9, NFR-02.5

**Given** att spelaren är på startsidan och har ett synligt spelarnamn

**When** spelaren väljer "Spela med en vän"

**Then** ska systemet skapa en unik inbjudningslänk inom 1 sekund  
**And** visa inbjudningslänken för spelaren  
**And** låta spelaren kopiera eller dela länken  
**And** visa ett väntläge tills motståndaren har anslutit  
**And** starta partiet automatiskt när båda spelarna har anslutit  
**And** visa båda spelarnas synliga spelarnamn när partiet startar.


### AC-03-02: Inbjudningslänken förfaller

**Relaterade krav:** FR-07.3, FR-07.6

**Given** att en inbjudningslänk har genererats  
**And** ingen motståndare har anslutit med länken

**When** 15 minuter har gått sedan länken genererades  
**And** en person försöker ansluta med länken

**Then** ska systemet avvisa anslutningsförsöket  
**And** informera personen om att inbjudningslänken har förfallit  
**And** inget parti ska startas.


### AC-03-03: Ogiltig inbjudningslänk

**Relaterade krav:** FR-07.6

**Given** att en person har en inbjudningslänk som inte är giltig

**When** personen försöker ansluta med länken

**Then** ska systemet avvisa anslutningsförsöket  
**And** informera personen om att inbjudningslänken är ogiltig  
**And** inget parti ska startas.


### AC-03-04: Inbjudaren avbryter inbjudan

**Relaterade krav:** FR-07.7, FR-07.10

**Given** att spelaren har skapat en inbjudningslänk  
**And** motståndaren ännu inte har anslutit

**When** spelaren avbryter inbjudan

**Then** ska systemet avsluta vänteläget  
**And** göra inbjudningslänken ogiltig  
**And** ingen motståndare ska kunna ansluta med den avbrutna inbjudningslänken  
**And** inget parti ska startas.


### AC-03-05: Ytterligare spelare försöker ansluta

**Relaterade krav:** FR-07.8

**Given** att inbjudaren och en motståndare redan har anslutit till partiet

**When** ytterligare en person försöker ansluta till samma parti

**Then** ska systemet avvisa anslutningsförsöket  
**And** partiet ska fortfarande endast innehålla två spelare.


### AC-03-06: Två personer försöker använda samma inbjudan

**Relaterade krav:** FR-07.8

**Given** att inbjudaren väntar på en motståndare  
**And** två personer har tillgång till samma inbjudningslänk

**When** båda försöker ansluta till partiet

**Then** ska endast en av dem kunna ansluta som motståndare  
**And** det andra anslutningsförsöket ska avvisas  
**And** partiet ska innehålla högst två spelare.
