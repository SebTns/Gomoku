## Acceptance Tests – UC-NFR-06 Systemets responstid efter spelarens handling

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

Mätpunkt enligt NFR-02: från att klicket eller trycket registreras i klienten till att den
uppdaterade vyn är renderad. Tiderna kan läsas i efterhand via dragens tidsstämplar (FR-08.17).

> **Förslag till gruppen.** NFR-02 anger inte hur många mätningar som krävs. Förslaget är att
> varje tidskrav mäts som 95:e percentilen över minst 100 körningar, så att ett enstaka långsamt
> värde inte avgör utfallet.

---

### AC-NFR-06-01: Startsidan laddas inom 2 sekunder

**Relaterade krav:** NFR-02.1

**Given** en anslutning som är begränsad till 25 Mbit/s  

**When** spelaren öppnar startsidan  

**Then** ska sidan vara färdigrenderad inom 2 sekunder.

---

### AC-NFR-06-02: Ett drag visas inom 100 ms

**Relaterade krav:** NFR-02.2, FR-08.1, FR-08.17

**Given** att det är spelarens tur  

**When** spelaren klickar på en ledig punkt  

**Then** ska stenen synas på brädet inom 100 ms.

---

### AC-NFR-06-03: Vinstkontrollen är klar inom 100 ms

**Relaterade krav:** NFR-02.4, FR-08.8, FR-08.17

**Given** att spelaren har fyra i rad med en öppen ände  

**When** spelaren placerar den femte stenen  

**Then** ska vinsten vara registrerad inom 100 ms efter draget.

---

### AC-NFR-06-04: Ogiltigt drag avvisas inom 100 ms (UC-NFR-06 AF-01, AF-02)

**Relaterade krav:** NFR-02.2, FR-08.2, FR-08.3

**Given** att spelaren klickar på en upptagen punkt, eller klickar när det inte är spelarens tur  

**When** systemet behandlar klicket  

**Then** ska avvisningen synas inom 100 ms  
**And** brädet och turordningen ska vara oförändrade.

---

### AC-NFR-06-05: Datorns drag inom 3 sekunder (UC-NFR-06 AF-03)

**Relaterade krav:** NFR-02.3

**Given** att spelaren spelar mot datorn på Lätt, Medel respektive Svår  

**When** spelaren har gjort sitt drag  

**Then** ska datorns drag visas inom 3 sekunder på varje svårighetsgrad.

---

### AC-NFR-06-06: Inbjudningslänk inom 1 sekund

**Relaterade krav:** NFR-02.5

**Given** att spelaren har valt att bjuda in en vän  

**When** spelaren begär en inbjudningslänk  

**Then** ska länken visas inom 1 sekund.

---

### AC-NFR-06-07: Drag syns hos motståndaren inom 500 ms

**Relaterade krav:** NFR-02.6

**Given** att ett parti mot en vän pågår  

**When** spelaren gör ett drag  

**Then** ska draget synas hos motståndaren inom 500 ms.

---

### AC-NFR-06-08: Byte av inställning inom 300 ms

**Relaterade krav:** NFR-02.7

**Given** att spelaren är i konfigurationsvyn  

**When** spelaren byter svårighetsgrad eller brädstorlek  

**Then** ska ändringen synas i gränssnittet inom 300 ms.
