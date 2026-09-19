## Acceptance Tests – UC-08 Välj svårighetsgrad

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-08-01: Spelaren väljer svårighetsgrad

**Relaterade krav:** FR-05.1, FR-05.2, FR-05.3, NFR-02.7

**Given** att spelaren konfigurerar ett parti mot datorn  

**When** konfigurationsvyn visas  

**Then** ska systemet erbjuda svårighetsgraderna Lätt, Medel och Svår  
**And** Medel ska vara förvalt  
**And** varje grad ska ha en kort beskrivning av vad den innebär  
**And** ett byte av grad ska återspeglas i gränssnittet inom 300 ms.

---

### AC-08-02: Svårighetsgrad erbjuds bara mot datorn

**Relaterade krav:** FR-05.4

**Given** att spelaren konfigurerar ett parti mot en vän  

**When** konfigurationsvyn visas  

**Then** ska inget val av svårighetsgrad erbjudas.

> **Varför detta kriterium finns.** FR-05.4 är ett negativt krav — det säger vad som *inte* ska
> visas. Utan ett eget testfall verifieras det aldrig, eftersom AC-08-01 bara tittar på fallet mot
> datorn och passerar oavsett hur vän-läget beter sig.

---

### AC-08-03: Svårighetsgraden är låst under partiet

**Relaterade krav:** FR-05.5

**Given** att ett parti mot datorn pågår på graden Svår  

**When** spelaren försöker ändra svårighetsgraden  

**Then** ska ändringen inte gå att genomföra  
**And** partiet ska fortsätta på Svår.

---

### AC-08-04: Senast valda grad föreslås nästa gång

**Relaterade krav:** FR-05.6

**Given** att spelaren har avslutat ett parti som spelades på Lätt  

**When** spelaren konfigurerar ett nytt parti mot datorn  

**Then** ska Lätt vara förvalt i stället för Medel.

---

### AC-08-05: Vald grad kan inte tillämpas

**Relaterade krav:** FR-05.7, NFR-04.1

**Given** att spelaren har valt Svår  
**And** graden inte kan tillämpas  

**When** partiet startas  

**Then** ska partiet starta på Medel  
**And** spelaren ska informeras om att graden ändrades.

---

### AC-08-06: Graden påverkar datorns svarstid inte mer än tillåtet

**Relaterade krav:** NFR-02.3, NFR-09.3

**Given** att ett parti mot datorn pågår på graden Svår  
**And** datorns drag görs deterministiska via en seed  

**When** det blir datorns tur  

**Then** ska datorns drag levereras inom 3 sekunder  
**And** samma seed och samma brädläge ska ge samma drag vid en omkörning.

> **Testnot.** Andra Then-raden är det som gör hela testsviten för UC-05 och UC-09 möjlig.
> NFR-09.3 kräver deterministiska drag — utan det går ett parti mot datorn inte att återskapa,
> och ett misslyckat testfall går inte att felsöka.
