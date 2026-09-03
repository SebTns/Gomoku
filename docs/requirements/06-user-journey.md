
## UJ-01: Spelare spelar ett parti mot datorn

**Aktör:** Spelare

```mermaid
journey
    title UJ-01: Spelare spelar ett parti mot datorn
   section Förbereda
      Väljer att spela mot datorn: 4: Spelare
      Visar val för spelet: 4: System
      Väljer färg: 4: Spelare

    section Konfigurera
      Väljer svårighetsgrad: 4: Spelare
      Sparar valen: 4: System

    section Starta
      Startar spelet: 4: Spelare
      Visar spelplanen: 4: System

    section Spela
      Gör sitt drag: 5: Spelare
      Registrerar draget: 5: System
      Datorn gör sitt drag: 3: AI-motståndare
      Uppdaterar spelplanen: 4: System
      Spelaren fortsätter göra drag: 5: Spelare

    section Avsluta
      Kontrollerar resultatet: 4: System
      Ser resultatet: 3: Spelare
      Avslutar eller startar nytt parti: 4: Spelare
```

## UJ-02: Spelare sparar och fortsätter ett parti
**Aktörer:** Spelare · System

 
```mermaid
journey
    title UJ-02: Spelare sparar och fortsätter ett parti

    section Spela
      Gör ett drag: 5: Spelare
      Registrerar draget: 5: System
      Fortsätter spela: 5: Spelare

    section Spara
      Väljer att spara partiet: 4: Spelare
      Sparar partiets aktuella läge: 4: System
      Bekräftar att partiet är sparat: 4: System

    section Återvända
      Öppnar spelet igen: 4: Spelare
      Väljer ett sparat parti: 4: Spelare
      Hämtar det sparade partiet: 3: System

    section Fortsätta
      Visar det tidigare spelläget: 4: System
      Fortsätter det sparade partiet: 5: Spelare
      Gör ett nytt drag: 5: Spelare
```


## UJ-03: Spelare spelar ett parti med en vän
**Aktör:** Spelare, Motspelare, System


```mermaid
journey
    title UJ-02: Spelare spelar ett parti med en vän

    section Förbereda
      Väljer att spela med en vän: 5: Spelare
      Väljer synligt spelarnamn: 4: Spelare
      Bjuder in en vän: 4: Spelare

    section Ansluta
      Ansluter till partiet: 4: Motspelare
      Visar partiet: 4: System

    section Spela
      Gör sitt drag: 5: Spelare
      Registrerar draget: 5: System
      Gör sitt drag: 5: Motspelare
      Uppdaterar spelplanen: 5: System
      Fortsätter spela: 5: Spelare, Motspelare

    section Avsluta
      Kontrollerar resultatet: 4: System
      Visar resultatet: 4: System
      Ser resultatet: 3: Spelare, Motspelare
      Avslutar eller startar ett nytt parti: 4: Spelare
```


## UJ-04: Spelare rapporterar ett tekniskt problem
**Deltagare:** Spelare, System, Administratör

```mermaid
journey
    title UJ-04: Spelare rapporterar ett tekniskt problem

    section Upptäcka problem
      Upptäcker ett tekniskt problem: 2: Spelare
      Öppnar rapportfunktionen: 3: Spelare
      Visar rapportformuläret: 4: System

    section Rapportera
      Beskriver problemet: 3: Spelare
      Skickar rapporten: 4: Spelare
      Registrerar rapporten: 4: System
      Visar en bekräftelse: 4: System

    section Hantera
      Tar emot rapporten: 3: Administratör
      Granskar informationen: 3: Administratör
      Registrerar hanteringen: 4: System
```

