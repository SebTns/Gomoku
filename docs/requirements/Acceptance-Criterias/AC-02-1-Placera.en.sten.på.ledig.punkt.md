## Acceptance Tests – UC-02 Gör ett drag

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

---

### AC-02-01: Spelaren placerar en sten på en ledig punkt

**Relaterade krav:** FR-08.1, FR-08.5, FR-08.6, FR-08.7, FR-08.12, FR-08.17, NFR-02.2

**Given** att ett parti pågår  
**And** det är spelarens tur  
**And** brädet visas med turindikatorn på spelarens namn och färg  

**When** spelaren väljer en ledig skärningspunkt  

**Then** ska systemet placera spelarens sten på punkten  
**And** markera den senast placerade stenen  
**And** registrera draget med position, färg, dragnummer och tidpunkt  
**And** öka dragräknaren med ett  
**And** visa den visuella återkopplingen inom 100 ms från klick eller tryck.

> **Anmärkning.** Tidigare version av detta kriterium angav 0,33 sekunder. NFR-02.2 anger 100 ms.
> Kravet gäller framför acceptanskriteriet, och värdet är rättat. Mätpunkten är definierad i
> `04-icke-funktionella-krav.md` under NFR-02.

---

### AC-02-02: Turen lämnas över efter ett giltigt drag

**Relaterade krav:** FR-08.4, FR-08.6

**Given** att spelaren har placerat en sten på en ledig punkt  
**And** ingen femma har uppstått  
**And** brädet är inte fullt  

**When** draget har registrerats  

**Then** ska systemet lämna över turen till motståndaren  
**And** visa motståndarens namn och färg i turindikatorn.

---

### AC-02-03: Punkten är upptagen (UC-02 AF-01)

**Relaterade krav:** FR-08.2, NFR-02.2

**Given** att ett parti pågår  
**And** det är spelarens tur  
**And** en sten redan ligger på punkten P  

**When** spelaren väljer punkten P  

**Then** ska systemet avvisa draget  
**And** ge visuell återkoppling om att punkten är upptagen  
**And** inte byta tur  
**And** låta spelaren välja en annan punkt.

---

### AC-02-04: Drag utanför sin tur (UC-02 AF-02)

**Relaterade krav:** FR-08.3

**Given** att ett parti pågår  
**And** det är motståndarens tur  

**When** spelaren försöker placera en sten på en ledig punkt  

**Then** ska systemet avvisa draget  
**And** brädet ska vara oförändrat  
**And** turen ska fortfarande ligga hos motståndaren.

---

### AC-02-05: Exakt fem i rad ger vinst (UC-02 AF-03)

**Relaterade krav:** FR-08.8, FR-08.9, FR-08.10, FR-08.13, FR-08.14, FR-08.16, NFR-02.4

**Given** att ett parti pågår  
**And** spelaren har fyra stenar av sin färg i en obruten rad  
**And** båda ändarna av raden är lediga  

**When** spelaren placerar sin femte sten i förlängningen av raden  

**Then** ska systemet avsluta partiet inom 100 ms efter draget  
**And** utse spelaren till vinnare  
**And** markera den vinnande raden visuellt  
**And** inte tillåta fler drag.

---

### AC-02-06: Sex eller fler i rad är inte en vinst (UC-02 AF-06)

**Relaterade krav:** FR-08.15, FR-08.16

**Given** att ett parti pågår och det är svarts tur  
**And** svart har tre stenar i rad på en linje  
**And** därefter följer en ledig punkt på samma linje  
**And** därefter följer tre svarta stenar i rad  
**And** ingen av grupperna är fem i rad, så partiet har status PÅGÅENDE  

**When** svart placerar en sten på den lediga punkten mellan grupperna  
**And** raden därmed blir sju stenar lång  

**Then** ska systemet inte utse någon vinnare  
**And** partiet ska fortsätta med status PÅGÅENDE  
**And** turen ska lämnas över till vit.

> **Varför uppställningen ser ut så här.** En överlinje kan bara uppstå genom att en **lucka
> fylls**. Att förlänga en rad en sten i taget går inte, eftersom raden då passerar exakt fem och
> partiet avgörs i det ögonblicket — fem i rad är en vinst oavsett om ändarna är blockerade.
> Blockerade ändar spelar roll för hotbilden i spelet, inte för vinstvillkoret.
>
> Det brädläge som krävs är alltså två grupper av samma färg på samma linje med exakt en ledig
> punkt emellan, där **ingen grupp är fem lång** och grupperna tillsammans plus den nya stenen
> blir fler än fem. Giltiga kombinationer: 1+4, 2+3, 2+4, 3+3, 3+4 och 4+4, vilket ger sex till
> nio i rad.

> **Testnot.** Kriteriet är det som skiljer en korrekt implementation från en som stannar vid fem
> intilliggande stenar. En sådan implementation hittar en femma mitt i sjuan och utropar vinst.
> Den passerar varje test som bara lägger stenar en i taget, eftersom ett sådant test aldrig
> skapar en överlinje. Uppställningen kräver därför ett konstruerat brädläge.
>
> Det är också därför FR-08.16 finns: den placerade stenen hamnar **mitt i** raden, så kontrollen
> måste mäta åt båda hållen från den. En implementation som bara räknar framåt ser tre stenar och
> missar hela sjuan.

---

### AC-02-06b: Att fylla en lucka till exakt fem är en vinst

**Relaterade krav:** FR-08.9, FR-08.14, FR-08.16

**Given** att ett parti pågår och det är svarts tur  
**And** svart har två stenar i rad, en ledig punkt, och därefter två svarta stenar på samma linje  
**And** partiet har status PÅGÅENDE  

**When** svart placerar en sten på den lediga punkten  
**And** raden därmed blir exakt fem stenar lång  

**Then** ska systemet avsluta partiet  
**And** utse svart till vinnare  
**And** markera den vinnande raden visuellt.

> **Varför båda behövs.** AC-02-06 och AC-02-06b har samma sorts brädläge — två grupper med en
> lucka emellan — men motsatt förväntat resultat. Skillnaden är bara radens totala längd efter
> draget: fem vinner, sex eller fler gör det inte. Tillsammans låser de fast att kontrollen mäter
> **hela** raden genom den placerade stenen och inte bara letar efter fem stenar någonstans i den.
> Ett av kriterierna ensamt räcker inte: AC-02-06b passerar även för en implementation som räknar
> fel uppåt, och AC-02-06 passerar även för en som aldrig utser någon vinnare alls.

---

### AC-02-07: Brädet blir fullt utan femma (UC-02 AF-04)

**Relaterade krav:** FR-08.11, FR-20.1, FR-20.2, FR-20.3, FR-20.4

**Given** att ett parti pågår  
**And** exakt en punkt är ledig  
**And** ingen spelare har fem i rad  

**When** spelaren placerar en sten på den sista lediga punkten  
**And** draget inte skapar fem i rad  

**Then** ska systemet avsluta partiet som oavgjort  
**And** visa i resultatvyn att partiet slutade oavgjort  
**And** inte tillåta fler drag.

---

### AC-02-08: Draget kan inte registreras (UC-02 AF-05)

**Relaterade krav:** FR-08.12, NFR-04.1, NFR-04.6

**Given** att ett parti pågår  
**And** det är spelarens tur  

**When** spelaren väljer en ledig punkt  
**And** registreringen av draget misslyckas  

**Then** ska systemet visa ett felmeddelande på engelska som beskriver vad som hänt och nästa steg  
**And** återställa brädet till läget före draget  
**And** låta spelaren försöka igen.

---

### AC-02-09: Draget går att göra med tangentbord

**Relaterade krav:** NFR-06.4, NFR-06.5

**Given** att ett parti pågår  
**And** det är spelarens tur  

**When** spelaren navigerar till en ledig skärningspunkt och bekräftar med tangentbordet  

**Then** ska stenen placeras på samma sätt som vid klick eller tryck  
**And** den aktuella punkten ska vara synligt markerad under navigeringen.
