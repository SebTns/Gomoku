
## UJ-01: Spelare spelar ett parti mot datorn

**Aktör:** Spelare

```mermaid
journey
    title UJ-01: Spelare spelar ett parti mot datorn
     section Förbereda
        Väljer att spelar mot datorn: 5: Spelare
        Väler färg: 4: Spelare

    section Konfigurera
      Väljer svårighetsgrad: 3: Spelare

    section Starta
        Starta spelet: 5: Spelare

      section Spela
      Gör sitt drag: 5: Spelare
      Väntar på datorns drag: 3: Spelare
      Fortsätter spela mot datorn: 4: Spelare

    section Avsluta
      Ser resultatet av partiet: 3: Spelare
      Avslutar eller startar nytt parti: 5: Spelare
```
