# UC-06: Starta spelet

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-06 |
| **Namn** | Starta spelet |
| **Version** | 1.0 |
| **Primär aktör** | Spelare |
| **Sekundär aktör** | – |
| **Relaterade FR** | FR-01.1, FR-01.2, FR-01.3, FR-01.4, FR-01.5 |
| **Relaterade NFR** | NFR-01.1 – NFR-01.6, NFR-02.1, NFR-06.6 |

## Beskrivning
Spelaren öppnar applikationen och möts av en startsida där spelets olika lägen kan väljas.
Detta use case omfattar att få igång applikationen, inte att starta ett parti (se UC-01).

## Förutsättningar
- Spelaren har en enhet med webbläsare och internetuppkoppling.
- Spelaren känner till adressen till spelet.

## Huvudflöde

1. Spelaren öppnar spelets adress i sin webbläsare.
2. Systemet laddar applikationen.
3. Systemet visar startsidan.
4. Systemet visar valen "Spela mot datorn", "Spela mot vän" och "Visa spelregler".
5. Spelaren väljer ett av alternativen.
6. Systemet går vidare till valt flöde (UC-01, UC-03 eller UC-20).

## Alternativa flöden

### AF-01: Applikationen kan inte laddas
Vid steg 2 misslyckas laddningen.
- Systemet visar ett meddelande om att spelet inte kunde startas.
- Systemet erbjuder spelaren att försöka igen.
- Spelaren stannar kvar tills laddningen lyckas eller spelaren lämnar sidan.

### AF-02: Spelaren har ett pågående parti
Vid steg 3 finns ett sparat, pågående parti.
- Systemet visar även valet "Återuppta parti".
- Väljer spelaren detta återställs partitillståndet och spelaren fortsätter i UC-02.

## Postconditions

**Lyckat:** Startsidan visas och spelaren kan välja ett spelläge.

**Misslyckat:** Startsidan visas inte och spelaren har fått besked om varför.

## Särskilda krav
- Startsidan ska vara färdigrenderad inom 2 sekunder vid 25 Mbit/s (NFR-02.1).
- Startsidan ska fungera på skärmbredder från 360 px (NFR-01.2).

## Öppna frågor
- Ska "Återuppta parti" finnas redan i v1, eller vänta till UC-27 (starta sparat parti)?
