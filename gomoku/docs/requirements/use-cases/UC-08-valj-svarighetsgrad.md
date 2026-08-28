# UC-08: Välj svårighetsgrad

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-08 |
| **Namn** | Välj svårighetsgrad |
| **Version** | 1.0 |
| **Primär aktör** | Spelare |
| **Sekundär aktör** | Datorn |
| **Relaterade FR** | FR-05.1 – FR-05.7 |
| **Relaterade NFR** | NFR-02.3, NFR-02.7 |

## Beskrivning
Spelaren väljer hur svår datormotståndaren ska vara. Flödet ingår som ett delsteg när ett
parti mot datorn konfigureras (UC-01, UC-05).

## Förutsättningar
- Spelaren har valt datorn som motståndare.
- Partiet har inte startat.

## Huvudflöde

1. Systemet visar svårighetsgraderna Lätt, Medel och Svår, med Medel förvalt.
2. Systemet visar en kort beskrivning av vad varje nivå innebär.
3. Spelaren väljer en svårighetsgrad.
4. Systemet registrerar valet för det kommande partiet.
5. Systemet sparar valet som förval till nästa parti.
6. När partiet startas låser systemet svårighetsgraden.

## Alternativa flöden

### AF-01: Spelaren gör inget val
Vid steg 3 startar spelaren partiet utan att välja.
- Systemet använder Medel.
- Flödet fortsätter från steg 4.

### AF-02: Vald svårighetsgrad kan inte tillämpas
Vid steg 4 kan systemet inte tillämpa den valda nivån.
- Systemet informerar spelaren.
- Systemet startar partiet på Medel.

### AF-03: Motståndaren är en vän
Vid steg 1 är motståndaren en annan spelare.
- Systemet visar inte valet av svårighetsgrad.
- Flödet avslutas utan att någon nivå sätts.

### AF-04: Spelaren försöker byta nivå under pågående parti
Efter steg 6 försöker spelaren ändra svårighetsgraden.
- Systemet avvisar ändringen.
- Systemet informerar om att nivån gäller till partiet är slut.

## Postconditions

**Lyckat:** En svårighetsgrad är satt och används av datorn i partiet.

**Misslyckat:** Ingen nivå har satts, eller partiet startas på Medel efter besked till spelaren.

## Särskilda krav
- Datorns drag ska levereras inom 3 sekunder oavsett vald nivå (NFR-02.3).
- Ett byte av nivå ska synas i gränssnittet inom 300 ms (NFR-02.7).

## Öppna frågor
- Ska nivån gå att ändra mellan partier i en serie utan att gå tillbaka till startsidan?
