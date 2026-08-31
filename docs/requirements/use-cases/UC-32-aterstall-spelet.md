# UC-32: Återställ spelet

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-32 |
| Namn | Återställ spelet |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet, Motståndaren |
| Relaterade FR | FR-03.7, FR-08.13 |
| Relaterade NFR | NFR-08.2 |

---

## Beskrivning

Spelaren återställer ett pågående parti till startläge, så att hen kan börja om utan att avsluta och starta ett nytt parti.

---

## Förutsättningar

- Ett parti pågår.
- Spelaren vill börja om från början.

---

## Huvudflöde

1. Spelaren väljer "Återställ spel".
2. Systemet begär bekräftelse (pågående parti kommer att förloras).
3. Spelaren bekräftar.
4. Systemet rensar brädet.
5. Systemet skapar ett nytt parti med samma konfiguration (brädstorlek, motståndare, svårighetsgrad, färger).
6. Systemet visar det tomma brädet och att svart börjar.
7. Motståndaren informeras om återställningen.

---

## Alternativa flöden

### AF-01: Spelaren ångrar sig
Vid steg 3 väljer spelaren "Avbryt".

- Partiet fortsätter oförändrat.

### AF-02: Partiet är redan avslutat
Vid steg 1 är partiet avslutat.

- Systemet hänvisar till "Spela igen" (→ UC-13) i stället.

---

## Postconditions

**Lyckat:** Brädet är återställt och ett nytt parti med samma konfiguration har startat.

**Misslyckat:** Partiet fortsätter oförändrat.

---

## Särskilda krav

- Ett parti ska aldrig hamna i ett tillstånd där ingen kan göra ett giltigt drag (NFR-08.2).

---

## Öppna frågor

- Ska återställning vara möjlig mot online-motståndare, eller endast mot datorn och lokalt?
