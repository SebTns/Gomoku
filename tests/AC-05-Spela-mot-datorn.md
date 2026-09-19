

### AC-05-01: Starta ett parti mot datorn

**Relaterade krav:** FR-06.1

**Given** att spelaren har valt att spela mot datorn  
**And** spelaren har slutfört spelkonfigurationen  
**When** spelaren bekräftar att partiet ska starta  
**Then** ska systemet starta ett nytt parti mot datorn  
**And** visa spelplanen.

---

### AC-05-02: Datorn gör ett giltigt drag

**Relaterade krav:** FR-06.2, FR-06.3, FR-06.4

**Given** att ett parti mot datorn pågår  
**And** det är datorns tur  
**And** det finns minst en ledig skärningspunkt på spelplanen  
**When** datorn beräknar sitt drag  
**Then** ska systemet tydligt visa att det är datorns tur  
**And** datorn ska automatiskt göra ett drag  
**And** stenen ska placeras på en ledig skärningspunkt.

---

### AC-05-03: Kontrollera fem i rad efter spelarens drag

**Relaterade krav:** FR-06.5

**Given** att ett parti mot datorn pågår  
**And** spelaren har fyra stenar i rad  
**When** spelaren gör ett giltigt drag som skapar fem stenar i rad  
**Then** ska systemet kontrollera spelarens drag  
**And** identifiera att spelaren har fått fem i rad  
**And** avsluta partiet.

---

### AC-05-04: Kontrollera fem i rad efter datorns drag

**Relaterade krav:** FR-06.5

**Given** att ett parti mot datorn pågår  
**And** datorn har fyra stenar i rad  
**When** datorn gör ett giltigt drag som skapar fem stenar i rad  
**Then** ska systemet kontrollera datorns drag  
**And** identifiera att datorn har fått fem i rad  
**And** avsluta partiet.

---

### AC-05-05: Tekniskt fel när datorns drag beräknas

**Relaterade krav:** FR-06.6, FR-06.7

**Given** att ett parti mot datorn pågår  
**And** det är datorns tur  
**When** datorns drag inte kan beräknas på grund av ett tekniskt fel  
**Then** ska systemet visa ett felmeddelande  
**And** pausa partiet  
**And** bevara placerade stenar, spelarnas färger och information om vems tur det är  
**And** låta spelaren välja mellan att försöka igen och att avsluta partiet.

---

### AC-05-06: Datorns drag överskrider tidsgränsen och nytt försök lyckas

**Relaterade krav:** FR-06.9, NFR-02.3

**Given** att ett parti mot datorn pågår  
**And** det är datorns tur  
**When** datorns drag inte kan beräknas inom 3 sekunder  
**Then** ska systemet automatiskt försöka beräkna draget en gång till  
**And** om det andra försöket lyckas ska datorn göra sitt drag  
**And** partiet ska fortsätta.

---

### AC-05-07: Det andra försöket att beräkna datorns drag misslyckas

**Relaterade krav:** FR-06.6, FR-06.7, FR-06.9

**Given** att ett parti mot datorn pågår  
**And** det första försöket att beräkna datorns drag har överskridit 3 sekunder  
**When** det andra försöket också misslyckas  
**Th** ska systemet visa ett felmeddelande  
**And** pausa partiet  
**And** bevara partitillståndet  
**And** låta spelaren välja mellan att försöka igen och att avsluta partiet.

---



