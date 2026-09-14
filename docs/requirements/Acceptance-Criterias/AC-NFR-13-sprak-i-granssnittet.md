## Acceptance Tests – NFR-13 Språk i gränssnittet

Testspråk: Given / When / Then (BDT). Varje kriterium anger vilka krav det verifierar.

NFR-13 hör inte till ett enskilt användningsfall utan gäller tvärs över alla. Kriterierna nedan är
därför formulerade mot systemet som helhet.

---

### AC-NFR-13-01: Gränssnittets texter är på engelska

**Relaterade krav:** NFR-13.1, NFR-13.2, FR-01.2

**Given** att applikationen är laddad  

**When** startsidan visas  

**Then** ska valen heta "Play vs Computer", "Play with a Friend" och "Game Rules"  
**And** ingen synlig text ska vara på svenska.

---

### AC-NFR-13-02: Standardvärden som visas är på engelska

**Relaterade krav:** NFR-13.2, FR-02.4, FR-05.1, FR-05.2

**Given** att spelaren konfigurerar ett parti mot datorn  
**And** inget spelarnamn har angetts  

**When** konfigurationsvyn visas  

**Then** ska standardnamnet vara "Player 1"  
**And** svårighetsgraderna ska heta "Easy", "Medium" och "Hard"  
**And** "Medium" ska vara förvalt.

---

### AC-NFR-13-03: Felmeddelanden är på engelska

**Relaterade krav:** NFR-04.1, NFR-13.2, NFR-04.6

**Given** att ett fel har uppstått som spelaren ska informeras om  

**When** felvyn visas  

**Then** ska meddelandet vara på engelska  
**And** beskriva vad som hänt  
**And** ange nästa steg  
**And** erbjuda minst en väg vidare.

---

### AC-NFR-13-04: Cookie-texterna är på engelska

**Relaterade krav:** NFR-13.2, FR-24.2, FR-24.3, FR-24.8

**Given** att en gästanvändare besöker applikationen första gången  

**When** cookie-meddelandet visas  

**Then** ska valen heta "Accept All" och "Accept Necessary"  
**And** förklaringen av vilka cookies som används ska vara på engelska  
**And** länken för att ändra valet ska heta "Cookie Settings".

---

### AC-NFR-13-05: E-post från systemet är på engelska

**Relaterade krav:** NFR-13.2, FR-30.9, FR-13.4

**Given** att systemet skickar ett meddelande till en spelares e-postadress  

**When** meddelandet tas emot  

**Then** ska ämnesrad och brödtext vara på engelska.

---

### AC-NFR-13-06: Dokumentets språk är deklarerat

**Relaterade krav:** NFR-13.3, NFR-06.1

**Given** att applikationen är laddad  

**When** dokumentets rotelement granskas  

**Then** ska attributet `lang` ha värdet `en`.

> **Varför detta kriterium finns.** En skärmläsare väljer uttal utifrån `lang`. Saknas attributet,
> eller står det `sv` på engelsk text, läses innehållet upp med fel uttalsregler och blir svårt
> att följa. Felet är osynligt för en seende användare, och det är därför det behöver ett eget
> testfall snarare än att antas ingå i NFR-06.1.

---

### AC-NFR-13-07: Inga svenska strängar i byggartefakten

**Relaterade krav:** NFR-13.4

**Given** att applikationen har byggts  

**When** byggartefaktens användarvända textsträngar genomsöks efter tecknen å, ä och ö samt efter
en lista kända svenska ord  

**Then** ska inga träffar finnas.

> **Vad testet faktiskt visar.** Kriteriet fångar svenska strängar som blivit kvar, inte engelska
> meningar med fel innehåll. En knapp som av misstag heter "Delete Game" där den borde heta
> "Resign" passerar. Det är samma begränsning som i AC-NFR-04-05: ett avgränsat, körbart test som
> ersätter ett uttömmande påstående, och avgränsningen ska vara uttalad snarare än underförstådd.
>
> Sökningen måste dessutom avgränsas till användarvända strängar. Kodkommentarer och
> variabelnamn kan vara på svenska utan att bryta mot NFR-13, och ett test som söker i hela
> artefakten ger falska larm.

---

### AC-NFR-13-08: Formatering beror inte på webbläsarens språk

**Relaterade krav:** NFR-13.5, FR-11.2

**Given** att spelaren har avslutade partier i sin spelhistorik  
**And** webbläsarens språk är inställt på svenska  

**When** spelhistoriken visas  

**Then** ska datum och klockslag visas i samma format som med engelsk språkinställning.
