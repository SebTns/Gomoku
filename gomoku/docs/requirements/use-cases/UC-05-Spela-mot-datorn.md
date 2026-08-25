
UC-05-spela mot datorn

Aktör: Spelare
Beskrivning: Spelaren vill kunna spela ett parti Gomoku mot datorn.

Precondition: Spelaren har öppnat Gomoku-spelet, spelet fungerar och är redo att starta ett nytt parti.

Huvudflöde:
    1. systemet visar startsidan.
    2. spelare väljer "spela mot datorn".
    3. systemet visar de svårighetsgrader som finns.
    4. spelaren väljer en svårighetsgrad.
    5. systemet startar ett nytt parti mot datorn.
    6. systemet visar spelplanen och vem som börjar.
    7. spelaren gör ett drag på en ledig plats.
    8. systemet registrerar spelarens drag.
    9. Datorn gör sitt drag.
    10. systemet registrerar datorns drag.
    11. spelaren och datorn fortsätter att göra drag i tur och ordning.
    12. systemet kontrollerar efter varje drag om någon har fått fem i rad.
    13. när någon får fem i rad avslutas partiet.
    14. systemet visar resultet.
Alternative flöden: 
    AF-01 Partiet mot datorn kan inte starta
        Systemet visar ett meddelande om att partiet inte kunde startas.
        Spelaren stannar kvar på sidan.
        Spelaren kan försöka starta partiet igen eller gå tillbaka till startsidan.
    AF-02 Datorn kan inte göra sitt drag 
        om datorn inte kan göra sitt drag under partiet:
        System visar att något gick fel.
        Partiet pausas.
        Spelaren kan försöka igen eller avsluta partiet.
            
    
    
Postcondition:
    Lyckat: partiet mot datorn är avslutat och spelaren kan se resultat.
    Pågående: Om partiet inte är avslutade fortsätter spelaren och datorn att gör drag i tur och ordning.
