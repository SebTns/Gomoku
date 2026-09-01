# UC-XX: Namn på use case

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-NFR-05 |
| **Namn** |Spelare får feedback efter handling |
| **Version** | 1.0 |
| **Primär aktör** |Spelare |
| **Sekundär aktör** |Systemet |
| **Relaterade FR** |FR-02.3 , FR-03.6 , FR-03.7 ,  |
| **Relaterade NFR** |NFR-02.1 , NFR-02.2 , NFR-02.5 , NFR-02.7 ,  |

## Beskrivning
Som spelare vill jag få notiser eller svar på vad som händer efter att jag gör ett drag för att enkelt veta vad som har hänt och samtidigt kunna bekräfta eller neka mina drag. 

## Förutsättningar
- Spelaren måste ha startat ett spel och gjort ett drag.
- Spelaren måste ha gjort något interaktivt på sidan för att få feedback överhuvudtaget 

## Huvudflöde

1. Spelare startar sidan 
2. Spelaren startar ett spel mot dator
(Systemet frågar vilken färg spelaren vill köra med)
3. Spelaren väljer att börja spela med svart 
(Systemet skickar en bekräftelse och frågar ifall spelare vill starta)
4. Spelaren gör sitt drag 
(Systemet frågar ifall det draget är det som spelaren är nöjd med)
5. Spelaren väntar på datorn 
(Systemet säger till att det är spelarens tur)
6. Spelaren spelar igen 
7. Datorn lägger fem i rad
(Systemet säger att spelaren har förlorat)
8. Spelaren spelar till en förlust 
(Systemet frågar ifall spelaren vill spela igen eller återgå till huvudmeny)
## Alternativa flöden

### AF-01: Kort namn på avvikelsen
Vid steg N inträffar X.
- Systemet gör Y.
- Aktören kan Z.

## Postconditions

**Lyckat:** Vad som gäller när flödet gått igenom.

**Misslyckat:** Vad som gäller när flödet avbrutits.

## Särskilda krav
- Hänvisningar till NFR som gäller specifikt här.

## Öppna frågor
- Sådant gruppen inte beslutat ännu.

---

**Skrivregler**

- Numrera stegen. Ett steg = en handling.
- Växla mellan aktör och system i stegen, så att det syns vem som gör vad.
- Varje alternativt flöde ska ange vilket steg i huvudflödet det bryter från.
- Skriv inte in lösningar ("en knapp i React"), skriv beteende ("spelaren väljer").
- Fyll alltid i Relaterade FR och NFR — det är de som gör spårbarhetsmatrisen möjlig.

