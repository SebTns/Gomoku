# UC-07: Välj ditt synliga spelarnamn

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-07 |
| **Namn** | Välj ditt synliga spelarnamn |
| **Version** | 1.0 |
| **Primär aktör** | Spelare |
| **Sekundär aktör** | – |
| **Relaterade FR** | FR-02.1 – FR-02.7 |
| **Relaterade NFR** | NFR-07.3, NFR-07.4 |

## Beskrivning
Spelaren väljer det namn som visas för motståndaren och i spelets resultatvy, så att partiet
går att följa utan konto eller inloggning.

## Förutsättningar
- Spelaren har öppnat spelet (UC-06).
- Inget parti är pågående.

## Huvudflöde

1. Spelaren väljer att ändra sitt spelarnamn.
2. Systemet visar ett fält med det senast använda namnet ifyllt, eller standardnamnet "Spelare 1".
3. Spelaren skriver in önskat namn.
4. Systemet validerar namnet mot reglerna: 2–20 tecken, endast bokstäver, siffror, bindestreck och understreck.
5. Spelaren bekräftar.
6. Systemet sparar namnet lokalt.
7. Systemet visar namnet i gränssnittet.

## Alternativa flöden

### AF-01: Namnet uppfyller inte reglerna
Vid steg 4 bryter namnet mot valideringsreglerna.
- Systemet visar vilken regel som inte uppfylls.
- Namnet sparas inte.
- Spelaren kan skriva om namnet och försöka igen.

### AF-02: Spelaren anger inget namn
Vid steg 3 lämnar spelaren fältet tomt och bekräftar.
- Systemet tilldelar standardnamnet "Spelare 1".
- Flödet fortsätter från steg 6.

### AF-03: Spelaren avbryter
Vid steg 5 väljer spelaren att avbryta.
- Systemet behåller det tidigare namnet.
- Ingen ändring sparas.

## Postconditions

**Lyckat:** Spelarens synliga namn är satt och visas i gränssnittet.

**Misslyckat:** Namnet är oförändrat och spelaren vet varför ändringen inte gick igenom.

## Särskilda krav
- Namnet ska saneras så att skript inte kan köras hos andra spelare (NFR-07.3).
- Inga andra personuppgifter än det synliga namnet får samlas in i gästläge (NFR-07.4).

## Öppna frågor
- Ska två spelare i samma parti kunna ha identiska namn, eller ska systemet lägga till en siffra?
