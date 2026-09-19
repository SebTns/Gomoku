## Acceptance Tests – UC-27 Starta sparat parti

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-27-01: Listan över sparade partier visas

**Relaterade krav:** FR-17.1

**Given** att spelaren har tre sparade partier  

**When** spelaren väljer "Saved Games"  

**Then** ska systemet visa en lista med de tre partierna.

---

### AC-27-02: Spelaren återupptar ett sparat parti

**Relaterade krav:** FR-17.2, FR-17.3

**Given** att spelaren har ett sparat parti på 15×15 mot datorn på Medel  
**And** det sparade partiet har 8 stenar och det är svarts tur  

**When** spelaren väljer partiet i listan  

**Then** ska systemet rendera brädet med de 8 stenarna på rätt positioner  
**And** visa att det är svarts tur  
**And** visa brädstorleken 15×15 och svårighetsgraden Medel  
**And** låta spelaren fortsätta partiet med ett drag (→ UC-02).

---

### AC-27-03: Sparat parti importeras från fil

**Relaterade krav:** FR-17.4, FR-17.3

**Given** att spelaren har en nedladdad fil med ett sparat parti (från AC-26-03)  

**When** spelaren importerar filen  

**Then** ska systemet återställa brädet, turtillståndet och partiets konfiguration från filen.

---

### AC-27-04: Inga sparade partier finns (UC-27 AF-01)

**Relaterade krav:** FR-17.1

**Given** att spelaren inte har några sparade partier  

**When** spelaren väljer "Saved Games"  

**Then** ska systemet visa en tom lista  
**And** en kort förklaring om att inga partier är sparade.

---

### AC-27-05: Det sparade partiet kan inte laddas (UC-27 AF-02)

**Relaterade krav:** FR-17.5, NFR-04.1, NFR-04.6

**Given** att ett sparat parti är korrupt eller från en inkompatibel version  

**When** spelaren väljer partiet  

**Then** ska systemet visa ett felmeddelande på engelska som beskriver vad som hänt  
**And** behålla spelaren i listan över sparade partier  
**And** låta spelaren välja ett annat parti.

---

### AC-27-06: Motståndaren är inte ansluten (UC-27 AF-03)

**Relaterade krav:** NFR-04.2, NFR-04.3

**Given** att det sparade partiet gäller en online-motståndare  
**And** motståndaren inte är ansluten  

**When** spelaren återupptar partiet  

**Then** ska systemet meddela att motståndaren inte är ansluten  
**And** vänta på motståndarens återanslutning utan att tillåta drag.
