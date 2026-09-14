## Acceptance Tests – UC-12 Avsluta ett parti

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-12-01: Spelaren avslutar ett pågående parti

**Relaterade krav:** FR-10.1, FR-10.2, FR-10.3, FR-10.4, FR-10.5

**Given** att ett parti pågår  

**When** spelaren väljer att avsluta partiet  
**And** bekräftar  

**Then** ska partiet få status AVSLUTAT  
**And** systemet ska visa en sammanfattning med antal drag och spelare  
**And** varken vinnare eller förlorare ska registreras  
**And** motståndaren ska informeras om att partiet avslutats.

> **Anmärkning.** Sista Then-raden gäller bara partier mot en annan människa. I ett parti mot
> datorn finns ingen motståndare att informera.

---

### AC-12-02: Spelaren ångrar sig (UC-12 AF-01)

**Relaterade krav:** FR-10.2

**Given** att ett parti pågår  
**And** spelaren har valt att avsluta partiet  
**And** systemet visar en bekräftelse  

**When** spelaren avbryter  

**Then** ska partiet fortsätta med status PÅGÅENDE  
**And** brädet, turen och dragräknaren ska vara oförändrade.

---

### AC-12-03: Statusen kan inte sparas (UC-12 AF-02)

**Relaterade krav:** FR-10.3, NFR-04.1, NFR-04.6

**Given** att spelaren har bekräftat att partiet ska avslutas  
**And** statusen inte kan sparas  

**When** systemet försöker avsluta partiet  

**Then** ska systemet visa ett felmeddelande  
**And** behålla spelaren i partiet  
**And** låta spelaren försöka igen eller avbryta.

---

### AC-12-04: Spelaren stänger webbläsaren (UC-12 AF-03)

**Relaterade krav:** NFR-04.2, NFR-08.2

**Given** att ett parti pågår  

**When** spelaren stänger webbläsaren utan att avsluta partiet  
**And** öppnar spelet igen inom 5 minuter  

**Then** ska partitillståndet vara bevarat  
**And** partiet ska kunna återupptas med samma bräde, tur och dragräknare.

> **Testnot.** Detta är inte ett avslut utan ett avbrott, och skillnaden är hela poängen: ett
> stängt fönster får inte behandlas som att spelaren avslutade partiet. Utan detta kriterium
> verifieras aldrig att de två fallen hålls isär.
