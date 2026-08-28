# UC-03: Bjud in en vän

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-03 |
| **Namn** | Bjud in en vän |
| **Version** | 1.0 |
| **Primär aktör** | Spelare (inbjudare) |
| **Sekundär aktör** | Vän (inbjuden spelare) |
| **Relaterade FR** | FR-07.1 – FR-07.9 |
| **Relaterade NFR** | NFR-02.5, NFR-02.6, NFR-04.3, NFR-07.2 |

## Beskrivning
Spelaren skapar en inbjudan till ett parti och delar den med en vän, så att de kan spela mot
varandra på var sin enhet.

## Förutsättningar
- Spelaren har öppnat spelet och startsidan visas (UC-06).
- Spelaren har satt ett synligt spelarnamn (UC-07).

## Huvudflöde

1. Spelaren väljer "Spela mot vän" på startsidan.
2. Spelaren konfigurerar partiet: brädstorlek och färgval (→ UC-01, UC-04).
3. Systemet skapar en inbjudan med en unik länk.
4. Systemet visar länken och möjlighet att kopiera eller dela den.
5. Spelaren delar länken med sin vän utanför spelet.
6. Systemet visar ett väntläge för inbjudaren.
7. Vännen öppnar länken.
8. Systemet kontrollerar att inbjudan är giltig.
9. Vännen anger sitt synliga spelarnamn (→ UC-07).
10. Systemet ansluter vännen till partiet.
11. Systemet visar båda spelarnas namn för varandra.
12. Systemet startar partiet och visar spelplanen.
13. Partiet fortsätter med drag i tur och ordning (→ UC-02).

## Alternativa flöden

### AF-01: Inbjudan kan inte skapas
Vid steg 3 misslyckas skapandet av inbjudan.
- Systemet visar ett felmeddelande.
- Ingen inbjudan skapas.
- Spelaren kan försöka igen eller gå tillbaka till startsidan.

### AF-02: Inbjudan har förfallit
Vid steg 8 är inbjudan äldre än 15 minuter.
- Systemet avvisar anslutningen.
- Systemet informerar vännen om att inbjudan inte längre gäller.
- Inbjudaren informeras om att inbjudan förfallit och kan skapa en ny.

### AF-03: Inbjudan är ogiltig
Vid steg 8 matchar länken ingen inbjudan.
- Systemet avvisar anslutningen och förklarar varför.
- Vännen erbjuds att gå till startsidan.

### AF-04: Fler än två försöker ansluta
Vid steg 10 är partiet redan fullt.
- Systemet avvisar anslutningen.
- Den som försökte ansluta informeras om att partiet redan har två spelare.

### AF-05: Inbjudaren avbryter
Under steg 6 väljer inbjudaren att avbryta.
- Systemet ogiltigförklarar inbjudan.
- Inget parti startas.
- Inbjudaren återgår till startsidan.

### AF-06: Motståndaren kopplas från
Under steg 13 tappar en av spelarna anslutningen.
- Systemet upptäcker frånkopplingen och meddelar den kvarvarande spelaren.
- Partitillståndet bevaras och återanslutning är möjlig.

## Postconditions

**Lyckat:** Båda spelarna är anslutna till samma parti och partiet har startat.

**Misslyckat:** Inget parti har startats och båda parter har fått besked om varför.

## Särskilda krav
- Inbjudningslänken ska genereras inom 1 sekund (NFR-02.5).
- Ett drag ska synas hos motståndaren inom 500 ms (NFR-02.6).
- En frånkopplad motståndare ska upptäckas inom 15 sekunder (NFR-04.3).
- Inbjudningskoder ska vara oförutsägbara med minst 128 bitars entropi (NFR-07.2).

## Öppna frågor
- Ska inbjudaren kunna se vem som anslutit innan partiet startar, och kunna avvisa?
- Hur länge ska ett parti hållas vid liv efter att en spelare kopplats från?
