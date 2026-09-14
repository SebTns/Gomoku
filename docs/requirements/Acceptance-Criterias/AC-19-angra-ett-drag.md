## Acceptance Tests – UC-19 Ångra ett drag

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-19-01: Spelaren ångrar sitt senaste drag

**Relaterade krav:** FR-12.1, FR-12.2, FR-12.4, FR-12.10, NFR-02.2

**Given** att ett parti mot datorn pågår  
**And** spelaren har gjort minst ett drag  
**And** datorn ännu inte har svarat  

**When** spelaren väljer "Undo"  

**Then** ska systemet ta bort spelarens senast placerade sten  
**And** återställa brädet till läget före draget  
**And** återlämna turen till spelaren  
**And** minska dragräknaren med ett  
**And** visa återkopplingen inom 100 ms.

---

### AC-19-02: Det finns inget drag att ångra (UC-19 AF-01)

**Relaterade krav:** FR-12.8, NFR-04.1

**Given** att ett parti mot datorn pågår  
**And** inga drag har gjorts  

**When** spelaren väljer "Undo"  

**Then** ska systemet avvisa ångringen  
**And** visa att det inte finns något att ångra  
**And** brädet ska vara oförändrat.

---

### AC-19-03: Motståndaren har redan svarat

**Relaterade krav:** FR-12.5

**Given** att ett parti mot datorn pågår  
**And** spelaren har gjort ett drag  
**And** datorn har gjort sitt nästa drag  

**When** spelaren väljer "Undo"  

**Then** ska systemet förhindra ångringen  
**And** brädet ska vara oförändrat  
**And** turen ska ligga kvar hos spelaren.

---

### AC-19-04: Partiet är avslutat (UC-19 AF-03)

**Relaterade krav:** FR-12.9, FR-08.13

**Given** att ett parti är avslutat med ett resultat  

**When** spelaren väljer "Undo"  

**Then** ska systemet avvisa ångringen  
**And** resultatet ska vara oförändrat.

---

### AC-19-05: Ångra i lokalt parti kräver bekräftelse

**Relaterade krav:** FR-12.3, FR-12.6

**Given** att ett lokalt parti på samma enhet pågår (UC-18)  
**And** minst ett drag har gjorts  

**When** en spelare väljer "Undo"  

**Then** ska systemet begära en bekräftelse innan draget ångras  
**And** ångringen ska genomföras först när bekräftelsen ges  
**And** brädet ska vara oförändrat om bekräftelsen avbryts.

---

### AC-19-06: Ångra är inte tillgängligt i online-parti mot vän

**Relaterade krav:** FR-12.3, FR-12.7

**Given** att ett online-parti mot en vän pågår  
**And** spelaren har gjort minst ett drag  

**When** spelaren söker efter "Undo"  

**Then** ska funktionen inte vara tillgänglig  
**And** brädet ska vara oförändrat.

> **Löst motsägelse.** FR-12.3 sade tidigare att ångring endast är tillåten mot datorn, medan
> FR-12.6 beskrev hur ångring bekräftas i ett parti mot en vän. Kraven uteslöt varandra, och
> UC-19:s öppna fråga ("mot vän, eller endast mot datorn och lokalt?") lämnades obesvarad. Beslut:
> tillåten mot datorn och i lokalt hot-seat-parti där båda ser skärmen, inte i online-partier där
> motståndaren inte kan se att brädet ändras. AC-19-05 och AC-19-06 är de två kriterier som gör
> beslutet observerbart — utan dem står motsägelsen kvar oupptäckt.

---

### AC-19-07: Ångra flera drag i följd

**Relaterade krav:** FR-12.1, FR-12.5

**Given** att ett parti mot datorn pågår  
**And** spelaren just har ångrat sitt senaste drag  

**When** spelaren väljer "Undo" igen  

**Then** ska systemet svara enligt gruppens beslut i UC-19:s öppna fråga.

> **Öppet — kan inte skrivas färdigt än.** UC-19 har kvar frågan om flera ångringar i följd ska
> tillåtas, och inget FR besvarar den. FR-12.1 talar om "sitt senaste giltiga drag" i singular,
> vilket antyder ett drag men inte utesluter en kedja. Kriteriet är med i listan för att luckan
> ska synas i täckningen i stället för att försvinna. Skriv färdigt det när gruppen har beslutat.
