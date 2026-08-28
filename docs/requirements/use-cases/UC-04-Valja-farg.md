# UC-04: Välja färg

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-04 |
| **Namn** | Välja färg |
| **Version** | 1.0 |
| **Primär aktör** | Spelare |
| **Sekundär aktör** | Motståndare (spelare eller datorn) |
| **Relaterade FR** | FR-04.1 – FR-04.7 |
| **Relaterade NFR** | NFR-06.3 |

## Beskrivning
Spelaren väljer om hen ska spela svart eller vit. Valet avgör vem som börjar, eftersom svart
alltid gör första draget. Flödet ingår som ett delsteg i konfigurationen av ett parti (UC-01).

## Förutsättningar
- Spelaren befinner sig i konfigurationsvyn för ett nytt parti.
- Partiet har inte startat.

## Huvudflöde

1. Systemet visar valen svart och vit, med information om att svart börjar.
2. Spelaren väljer en färg.
3. Systemet tilldelar spelaren den valda färgen.
4. Systemet tilldelar motståndaren den andra färgen.
5. Systemet visar båda spelarnas färger i konfigurationsvyn.
6. När partiet startas låser systemet färgvalet.

## Alternativa flöden

### AF-01: Spelaren gör inget val
Vid steg 2 startar spelaren partiet utan att välja färg.
- Systemet slumpar färg åt spelaren.
- Flödet fortsätter från steg 4.

### AF-02: Båda spelarna vill ha samma färg
Vid steg 3 i ett parti mot en vän har motståndaren redan valt samma färg.
- Systemet ger företräde till den spelare som skapade inbjudan.
- Den andra spelaren informeras och tilldelas den återstående färgen.

### AF-03: Spelaren försöker byta färg under pågående parti
Efter steg 6 försöker spelaren ändra sin färg.
- Systemet avvisar ändringen.
- Systemet informerar om att färgen är låst tills partiet är slut.

## Postconditions

**Lyckat:** Båda spelarna har varsin färg och det framgår vem som börjar.

**Misslyckat:** Färg har inte tilldelats och partiet kan inte startas.

## Särskilda krav
- Svarta och vita stenar ska gå att skilja åt på mer än enbart färg, för spelare med
  nedsatt färgseende (NFR-06.3).

## Öppna frågor
- Ska färgvalet gå att spara som en preferens till nästa parti, som svårighetsgraden i UC-08?
