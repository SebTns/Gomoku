# UC-26: Spara parti

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-26 |
| Namn | Spara parti |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet, Databasen |
| Relaterade FR | FR-26.1, FR-26.2, FR-26.3, FR-26.4, FR-26.5, FR-26.6, FR-26.7, FR-26.8, FR-26.9 |
| Relaterade NFR | NFR-04.2, NFR-07.4 |

---

## Beskrivning

Spelaren sparar ett pågående parti så att det kan återupptas senare utan att partiet förloras.

---

## Förutsättningar

- Ett parti pågår.
- Spelaren är inloggad eller har en lokal profil med sparmöjlighet.

---

## Huvudflöde

1. Spelaren väljer "Spara parti".
2. Systemet frågar om spelaren vill spara till kontot, molnet eller en fil för nedladdning.
3. Systemet sparar partitillståndet (positioner, tur, färger, brädstorlek, svårighetsgrad).
4. Systemet visar en bekräftelse på att partiet är sparat.
5. Spelaren kan lämna partiet.

---

## Alternativa flöden

### AF-01: Partiet kan inte sparas
Vid steg 2 misslyckas sparandet.

- Systemet visar ett felmeddelande.
- Spelaren kan försöka igen eller avbryta.

### AF-02: Partiet är redan sparat
Vid steg 1 finns redan ett sparat tillstånd för partiet.

- Systemet frågar om spelaren vill skriva över det tidigare sparade tillståndet.

### AF-03: Partiet är avslutat
Vid steg 1 är partiet redan avslutat.

- Systemet erbjuder att spara partiet till historiken i stället.

### AF-04: Spelaren är inte inloggad (Ladda ner till fil)
Vid steg 1 är spelaren i gästläge.

- Systemet frågar om spelet ska sparas i moln eller fil för nedladdning.

---

## Postconditions

**Lyckat:** Partitillståndet är sparat och kan återupptas (→ UC-27).

**Misslyckat:** Partiet är inte sparat och spelaren har fått information om varför.

---

## Särskilda krav

- Partitillståndet ska bevaras vid sidomladdning eller nätverksavbrott (NFR-04.2).

---

## Öppna frågor

- Ska spelaren kunna spara flera partier samtidigt eller endast ett?
