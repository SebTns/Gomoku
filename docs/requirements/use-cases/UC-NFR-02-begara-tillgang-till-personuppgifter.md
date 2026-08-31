| Fält | Värde |
| --- | --- |
| Use Case ID | UC-NFR-02 |
| Namn | Begära tillgång till personuppgifter |
| Version | 1.0 |
| Primär aktör | Registrerad spelare |
| Sekundär aktör | systemet |
| Relaterade FR | — |
| Relaterade NFR | NFR-10.1, NFR-10.2 |
| GDPR-referens | Artikel 15 |

## Beskrivning
Spelaren vill kunna begära en kopia av de personuppgifter som finns registrerade om spelaren.

## Förutsättningar
- Spelaren har personuppgifter registrerade i systemet. 

## Huvudflöde

1.	Spelaren väljer att begära tillgång till sina personuppgifter. 
2.	Systemet tar emot begäran. 
3.	Systemet samlar spelarens personuppgifter. 
4.	Systemet gör uppgifterna tillgängliga i ett strukturerat format. 
5.	Spelaren tar del av uppgifterna. 


## Alternativa flöden

### AF-01: Begäran kan inte behandlas
Vid steg 2 kan begäran inte behandlas.
- Systemet informerar spelaren.
- Spelaren kan försöka igen.

## Postconditions

**Lyckat:** Spelaren har fått tillgång till sina personuppgifter.

**Misslyckat:** Begäran har inte kunnat behandlas.

## Testkriterier
- Spelaren kan initiera en begäran om tillgång till sina personuppgifter.
- Begärda personuppgifter tillhandahålls i ett strukturerat format.

---
