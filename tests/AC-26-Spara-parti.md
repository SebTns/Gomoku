## Acceptance Tests – UC-26 Spara parti

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

> **Not.** UC-26 och FR-26 säger olika saker på två punkter. Kriterierna nedan följer kraven:
> - Sparplats: UC-26 steg 2 nämner "konto, moln eller fil", FR-26.3/FR-26.4 anger konto för
>   inloggad spelare och "fil eller lokal lagring" för gäst.
> - Avslutat parti: UC-26 AF-03 erbjuder att spara till historiken, FR-26.8 tillåter bara
>   sparande av pågående parti. Historiken hanteras av UC-17.

---

### AC-26-01: Inloggad spelare sparar ett pågående parti

**Relaterade krav:** FR-26.1, FR-26.2, FR-26.3, FR-26.5

**Given** att spelaren är inloggad  
**And** ett parti med status PÅGÅENDE visas  

**When** spelaren väljer "Save Game"  

**Then** ska systemet spara partitillståndet kopplat till spelarens konto  
**And** visa en bekräftelse på att partiet är sparat.

---

### AC-26-02: Hela partitillståndet sparas

**Relaterade krav:** FR-26.2, FR-17.3

**Given** att ett parti pågår på ett 19×19-bräde mot datorn på svårighetsgraden Svår  
**And** 12 drag har gjorts och det är vits tur  

**When** spelaren sparar partiet  
**And** det sparade tillståndet läses tillbaka  

**Then** ska tillståndet innehålla alla 12 stenar på rätt positioner  
**And** ange att det är vits tur  
**And** innehålla spelarnas färger, brädstorleken 19×19 och svårighetsgraden Svår.

---

### AC-26-03: Gästspelare erbjuds fil eller lokal lagring (UC-26 AF-04)

**Relaterade krav:** FR-26.4, NFR-07.4

**Given** att spelaren inte är inloggad  
**And** ett parti pågår  

**When** spelaren väljer "Save Game"  

**Then** ska systemet erbjuda alternativen "exportera till nedladdningsbar fil" och "spara i webbläsarens lokala lagring"  
**And** inte kräva några personuppgifter utöver det synliga spelarnamnet.

---

### AC-26-04: Ett tidigare sparat parti skrivs över (UC-26 AF-02)

**Relaterade krav:** FR-26.6

**Given** att partiet redan har ett sparat tillstånd  

**When** spelaren väljer "Save Game"  

**Then** ska systemet fråga om det tidigare sparade tillståndet ska skrivas över  
**And** vid bekräftelse ska det nya tillståndet ersätta det gamla  
**And** vid avbrott ska det tidigare sparade tillståndet vara oförändrat.

---

### AC-26-05: Sparandet misslyckas (UC-26 AF-01)

**Relaterade krav:** FR-26.7, NFR-04.1, NFR-04.6

**Given** att ett parti pågår  
**And** lagringen inte går att nå  

**When** spelaren väljer "Save Game"  

**Then** ska systemet visa ett felmeddelande på engelska som beskriver vad som hänt  
**And** fråga om spelaren vill försöka igen  
**And** partiet ska fortsätta oförändrat.

---

### AC-26-06: Ett avslutat parti kan inte sparas (UC-26 AF-03)

**Relaterade krav:** FR-26.8

**Given** att partiet har status AVSLUTAT  

**When** spelaren försöker välja "Save Game"  

**Then** ska systemet inte spara partitillståndet  
**And** "Save Game" ska inte vara valbart.

---

### AC-26-07: Tillståndet sparas automatiskt vid sidomladdning

**Relaterade krav:** FR-26.9, NFR-04.2

**Given** att ett parti pågår och 5 drag har gjorts  

**When** spelaren laddar om sidan  

**Then** ska partiet visas med samma 5 stenar på samma positioner  
**And** samma spelare ska ha turen.

---

### AC-26-08: Tillståndet bevaras vid tillfälligt nätverksavbrott

**Relaterade krav:** FR-26.9, NFR-04.2

**Given** att ett parti mot en vän pågår  

**When** spelarens nätverksanslutning bryts  
**And** återställs inom 5 minuter  

**Then** ska partiet återupptas från samma tillstånd som före avbrottet  
**And** inget drag ska ha gått förlorat.
