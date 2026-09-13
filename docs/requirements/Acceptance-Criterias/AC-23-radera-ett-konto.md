## Acceptance Tests – UC-23 Radera ett konto

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

Detta användningsfall är gränssnittsflödet för kontoradering. Själva raderingen av
personuppgifter beskrivs i UC-NFR-04 och testas av AC-NFR-04-01 – AC-NFR-04-09. Kriterierna
nedan överlappar inte dem, utan slutar där raderingsprocessen tar vid.

---

### AC-23-01: Spelaren raderar sitt konto

**Relaterade krav:** FR-15.1, FR-15.2, FR-15.4, FR-15.5

**Given** att spelaren är inloggad  
**And** befinner sig i kontoinställningarna  

**When** spelaren väljer "Radera konto"  
**And** anger sitt lösenord  
**And** bekräftar  

**Then** ska systemet radera kontots personuppgifter  
**And** anonymisera den data som måste bevaras enligt FR-30.7  
**And** logga ut spelaren  
**And** återgå till startsidan  
**And** visa en bekräftelse på att kontot är raderat.

---

### AC-23-02: Varningen stämmer med vad som faktiskt händer

**Relaterade krav:** FR-15.3, FR-15.4, FR-30.7, NFR-12.5, NFR-12.6, SR-03.4

**Given** att spelaren har valt "Radera konto"  

**When** systemet visar varningen om vad raderingen innebär  

**Then** ska texten ange att kontots personuppgifter raderas  
**And** ange att partier och drag bevaras i anonymiserad form  
**And** ange att samtyckesregister bevaras i minst 3 år i anonymiserad form  
**And** inte påstå att all data raderas.

> **Löst motsägelse.** FR-15.4 sade tidigare att systemet ska permanent radera all data kopplad
> till kontot, och FR-15.3 att spelaren varnas om att all data går förlorad. Det motsäger
> FR-30.7, NFR-12.5 och NFR-12.6, där drag, partier och samtyckesregister uttryckligen bevaras i
> anonymiserad form — samtyckesregistren i minst 3 år enligt SR-03.4. Två dokument gav två svar på
> vad det betyder att radera ett konto. GDPR-kraven gäller, och FR-15.4 är omskrivet. Detta
> kriterium testar varningstexten, inte raderingen: ett gränssnitt som lovar mer än systemet gör
> är ett fel även när logiken är korrekt, och det är den sortens fel ingen enhetstest hittar.

---

### AC-23-03: Spelaren ångrar sig (UC-23 AF-01)

**Relaterade krav:** FR-15.7

**Given** att spelaren har valt "Radera konto"  
**And** systemet begär bekräftelse  

**When** spelaren avbryter  

**Then** ska kontot behållas oförändrat  
**And** spelaren ska fortfarande vara inloggad  
**And** ingen raderingsbegäran ska registreras.

---

### AC-23-04: Fel lösenord vid bekräftelsen (UC-23 AF-03)

**Relaterade krav:** FR-15.2, FR-15.6

**Given** att spelaren har valt "Radera konto"  
**And** systemet begär lösenordet  

**When** spelaren anger fel lösenord  

**Then** ska systemet avvisa bekräftelsen  
**And** kontot ska finnas kvar  
**And** spelaren ska kunna försöka igen.

---

### AC-23-05: Raderingen misslyckas (UC-23 AF-02)

**Relaterade krav:** FR-15.8, NFR-04.1, NFR-04.6

**Given** att spelaren har bekräftat raderingen med rätt lösenord  
**And** ett tekniskt fel uppstår  

**When** systemet försöker genomföra raderingen  

**Then** ska systemet informera spelaren om att kontot inte har raderats  
**And** spelaren ska fortfarande vara inloggad  
**And** kunna försöka igen.

---

### AC-23-06: Ett raderat konto kan inte logga in

**Relaterade krav:** FR-15.4, FR-15.5, FR-14.1, NFR-07.7

**Given** att spelaren har raderat sitt konto  

**When** spelaren försöker logga in med samma uppgifter  

**Then** ska inloggningen avvisas  
**And** felmeddelandet ska vara detsamma som för en icke-registrerad e-postadress.

---

### AC-23-07: Motståndarens partihistorik påverkas inte

**Relaterade krav:** FR-30.7, FR-11.1, FR-11.2, NFR-12.5

**Given** att spelare A och spelare B har spelat ett parti mot varandra  
**And** spelare A raderar sitt konto  

**When** spelare B öppnar sin spelhistorik  

**Then** ska partiet finnas kvar i B:s historik  
**And** datum, brädstorlek och resultat ska vara oförändrade  
**And** motståndaren ska visas anonymiserad.

> **Varför detta kriterium finns.** UC-23:s öppna fråga — om spelhistorik för raderade konton ska
> anonymiseras eller raderas helt — handlar bara om den raderade spelarens egen historik. Den
> svårare frågan står ingenstans: partiet tillhör två personer. Raderar man det försvinner data
> som B har rätt till; behåller man det står A:s identitet kvar i B:s vy. FR-30.7 löser det genom
> anonymisering av A:s referens, och detta är det enda kriterium där den lösningen verifieras från
> B:s håll.
