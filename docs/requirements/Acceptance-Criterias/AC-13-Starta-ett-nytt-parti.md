

### AC-13-01: Starta ett nytt parti

**Relaterade krav:** FR-03.1, FR-03.2, FR-03.3, FR-03.4

**Given** att spelaren befinner sig på startsidan  
**When** spelaren väljer att starta ett nytt parti  
**Then** ska systemet visa en konfigurationsvy  
**And** visa brädstorlek 15×15 som standard och 19×19 som alternativ  
**And** visa val för motståndartyp och färg  
**When** spelaren bekräftar konfigurationen  
**Then** ska systemet skapa ett parti med status `PÅGÅENDE`  
**And** visa ett tomt bräde med vald storlek  
**And** visa vem som gör det första draget.

---

### AC-13-02: Avbryta konfigurationen

**Relaterade krav:** FR-03.5

**Given** att spelaren befinner sig i konfigurationsvyn för ett nytt parti  
**When** spelaren väljer att avbryta konfigurationen  
**Then** ska inget nytt parti skapas  
**And** spelaren ska återgå till startsidan.

---

### AC-13-03: Partiet kan inte startas

**Relaterade krav:** FR-03.6

**Given** att spelaren har valt en konfiguration för ett nytt parti  
**When** spelaren bekräftar konfigurationen  
**And** partiet inte kan startas  
**Then** ska systemet visa ett felmeddelande  
**And** spelaren ska stanna kvar i konfigurationsvyn  
**And** den valda konfigurationen ska behållas.

---

### AC-13-04: Bekräftelse krävs när ett parti redan pågår

**Relaterade krav:** FR-03.7

**Given** att spelaren redan har ett pågående parti  
**When** spelaren försöker starta ett nytt parti  
**Then** ska systemet begära bekräftelse innan det pågående partiet överges.

---

### AC-13-05: Spelaren avbryter byte till nytt parti

**Relaterade krav:** FR-03.7, FR-03.8

**Given** att spelaren har ett pågående parti  
**And** systemet har begärt bekräftelse innan ett nytt parti startas  
**When** spelaren avbryter bekräftelsen  
**Then** ska det pågående partiet fortsätta  
**And** inget nytt parti ska skapas.

---

### AC-13-06: Spelaren bekräftar byte till nytt parti

**Relaterade krav:** FR-03.7, FR-03.9

**Given** att spelaren har ett pågående parti  
**And** systemet har begärt bekräftelse innan ett nytt parti startas  
**When** spelaren bekräftar att det pågående partiet ska överges  
**Then** ska det pågående partiet avslutas  
**And** spelaren ska kunna fortsätta med konfigurationen av ett nytt parti.
