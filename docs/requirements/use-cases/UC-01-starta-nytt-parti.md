# UC-01: Starta nytt parti

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-01 |
| **Namn** | Starta nytt parti |
| **Version** | 1.0 |
| **Primär aktör** | Spelare |
| **Sekundär aktör** | Datorn (när motståndaren är datorn) |
| **Relaterade FR** | FR-03.1 – FR-03.7 |
| **Relaterade NFR** | NFR-02.1, NFR-02.7, NFR-04.1 |

## Beskrivning
Spelaren konfigurerar och startar ett nytt parti Gomoku. Detta use case täcker konfigurationen
och skapandet av partiet, fram till att spelplanen visas. Själva spelandet sker i UC-02.

## Förutsättningar
- Spelaren har öppnat spelet och startsidan visas (UC-06).

## Huvudflöde

1. Spelaren väljer "Starta nytt parti" på startsidan.
2. Systemet visar konfigurationsvyn med:
   - Brädstorlek: 15×15 (standard) eller 19×19
   - Motståndare: datorn eller en vän
   - Färgval (→ UC-04)
   - Svårighetsgrad, om motståndaren är datorn (→ UC-08)
3. Spelaren gör sina val eller behåller standardvärdena.
4. Spelaren bekräftar med "Starta".
5. Systemet skapar ett parti med status `PÅGÅENDE`.
6. Systemet tilldelar färger enligt spelarens val och ger den andra färgen till motståndaren.
7. Systemet renderar ett tomt bräde av vald storlek.
8. Systemet visar vem som gör första draget. Svart börjar alltid.
9. Partiet fortsätter med drag i tur och ordning (→ UC-02).

## Alternativa flöden

### AF-01: Spelaren avbryter konfigurationen
Vid steg 4 väljer spelaren "Avbryt" eller lämnar vyn.
- Systemet kasserar konfigurationen.
- Inget parti skapas.
- Spelaren återgår till startsidan.

### AF-02: Partiet kan inte skapas
Vid steg 5 misslyckas skapandet av partiet.
- Systemet visar ett felmeddelande om att partiet inte kunde startas.
- Inget parti skapas.
- Spelaren stannar kvar i konfigurationsvyn och kan försöka igen.

### AF-03: Ett parti pågår redan
Vid steg 1 finns ett pågående parti.
- Systemet frågar om spelaren vill överge det pågående partiet.
- Vid ja: det gamla partiet avslutas och flödet fortsätter från steg 2.
- Vid nej: spelaren återgår till det pågående partiet.

## Postconditions

**Lyckat:** Ett parti med status `PÅGÅENDE` finns, brädet visas och det framgår vem som börjar.

**Misslyckat:** Inget parti har skapats och spelaren har fått ett felmeddelande.

## Särskilda krav
- Brädet ska renderas inom 2 sekunder från att "Starta" valts (NFR-02.1).
- Ändringar i konfigurationen ska synas i gränssnittet inom 300 ms (NFR-02.7).

## Öppna frågor
- Ska brädstorleken 19×19 ingå i v1 eller skjutas upp?
- Avgränsning mot UC-13 "Starta ett nytt parti" måste beslutas — se journalen.
