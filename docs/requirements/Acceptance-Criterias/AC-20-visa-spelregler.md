## Acceptance Tests – UC-20 Visa spelregler

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-20-01: Spelaren öppnar regelsammanfattningen

**Relaterade krav:** FR-01.2, FR-22.1, FR-22.2

**Given** att spelaren befinner sig på startsidan  

**When** spelaren väljer "Game Rules"  

**Then** ska systemet visa en regelsammanfattning  
**And** sammanfattningen ska beskriva spelets mål  
**And** hur ett drag görs  
**And** vinstvillkoret  
**And** när partiet blir oavgjort.

---

### AC-20-02: Reglerna anger rätt vinstvillkor

**Relaterade krav:** FR-22.3, FR-08.14, FR-08.15, SR-01.3

**Given** att regelsammanfattningen visas  

**When** spelaren läser avsnittet om vinstvillkoret  

**Then** ska texten ange att exakt fem i rad vinner  
**And** ange att sex eller fler i rad inte är en vinst.

> **Varför detta kriterium finns.** Regelvyn är det enda stället i systemet där vinstvillkoret
> förklaras i ord för spelaren. Om texten säger "fem eller fler" medan FR-08.15 säger något annat,
> är felet osynligt för alla tester som bara kontrollerar spellogiken — spelet beter sig rätt och
> berättar fel. Kriteriet kopplar regeltexten till samma krav som AC-02-06 testar i logiken, så
> att de två inte kan glida isär.

---

### AC-20-03: Spelaren återgår till vyn hen kom ifrån (UC-20 steg 5)

**Relaterade krav:** FR-22.4

**Given** att spelaren har öppnat reglerna från startsidan  

**When** spelaren stänger reglerna  

**Then** ska systemet återföra spelaren till startsidan.

---

### AC-20-04: Reglerna öppnas under ett pågående parti

**Relaterade krav:** FR-22.4, FR-22.7

**Given** att ett parti pågår  
**And** det är spelarens tur  

**When** spelaren öppnar regelsammanfattningen  
**And** därefter stänger den  

**Then** ska spelaren återföras till partiet  
**And** partiet ska ha status PÅGÅENDE  
**And** brädet, turen och dragräknaren ska vara oförändrade.

---

### AC-20-05: Spelaren startar ett parti från regelvyn (UC-20 AF-02)

**Relaterade krav:** FR-22.5, FR-03.1, FR-03.2

**Given** att regelsammanfattningen visas  
**And** inget parti pågår  

**When** spelaren väljer "Start Game"  

**Then** ska systemet visa konfigurationsvyn  
**And** reglerna ska stängas.

---

### AC-20-06: Reglerna kan inte laddas (UC-20 AF-01)

**Relaterade krav:** FR-22.6, NFR-04.1, NFR-04.6

**Given** att spelaren har valt "Game Rules"  
**And** regelsammanfattningen inte kan laddas  

**When** vyn visas  

**Then** ska systemet visa ett felmeddelande på engelska som beskriver vad som hänt  
**And** erbjuda möjlighet att försöka igen  
**And** erbjuda en väg tillbaka till den föregående vyn.

---

### AC-20-07: En ny spelare klarar sig utan extern hjälp

**Relaterade krav:** NFR-06.6

**Given** att en testperson som aldrig har spelat Gomoku får tillgång till applikationen  
**And** endast regelsammanfattningen som stöd  

**When** testpersonen ombeds starta och genomföra ett parti  

**Then** ska testpersonen klara det inom 2 minuter utan hjälp från någon annan.

> **Anmärkning om testbarhet.** Detta är inte ett automatiserbart testfall. NFR-06.6 är formulerat
> i termer av en människas beteende, och verifieras genom en observerad användbarhetstest med
> minst fem testpersoner som inte har sett systemet tidigare. Kravet är testbart — det är bara
> inte testbart i en pipeline. Skillnaden är värd att vara medveten om: ett krav som aldrig körs
> i CI kommer i praktiken att kontrolleras en gång och sedan glömmas.
