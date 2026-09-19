## Acceptance Tests – UC-NFR-03 Informeras om delning med tredje part

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.
GDPR-referens: artikel 28 och 46.

---

### AC-NFR-03-01: Tredje parter och deras behandling visas

**Relaterade krav:** FR-31.1, FR-31.2, NFR-11.1

**Given** att personuppgifter behandlas av en tredje part (t.ex. en e-posttjänst)  

**When** spelaren öppnar informationen om behandling av personuppgifter  

**Then** ska systemet lista varje tredje part  
**And** beskriva vilken behandling den utför.

---

### AC-NFR-03-02: Överföring utanför EES och skyddsåtgärder visas

**Relaterade krav:** FR-31.3, FR-31.4, NFR-11.2

**Given** att en tredje part behandlar personuppgifter i ett land utanför EES  

**When** spelaren läser informationen  

**Then** ska systemet ange vilket land uppgifterna överförs till  
**And** vilka skyddsåtgärder som gäller (t.ex. standardavtalsklausuler).

---

### AC-NFR-03-03: Ingen internationell överföring sker (UC-NFR-03 AF-01)

**Relaterade krav:** FR-31.5

**Given** att inga personuppgifter överförs utanför EES  

**When** spelaren läser informationen  

**Then** ska systemet uttryckligen visa att ingen sådan överföring sker.

---

### AC-NFR-03-04: Inga personuppgifter delas (UC-NFR-03 AF-02)

**Relaterade krav:** FR-31.6

**Given** att inga personuppgifter delas med tredje part  

**When** spelaren läser informationen  

**Then** ska systemet visa att inga personuppgifter delas med tredje part.

---

### AC-NFR-03-05: Informationen kräver ingen inloggning

**Relaterade krav:** FR-31.7

**Given** att besökaren inte är inloggad  

**When** besökaren öppnar informationen om behandling av personuppgifter  

**Then** ska informationen visas utan att inloggning krävs.
