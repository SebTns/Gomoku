# UC-19: Ångra ett drag

| Fält | Värde |
| ---- | ----- |
| Use Case ID | UC-19 |
| Namn | Ångra ett drag |
| Version | 1.0 |
| Primär aktör | Spelare |
| Sekundär aktör | Systemet |
| Relaterade FR | FR-12.1, FR-12.2, FR-12.3, FR-12.4, FR-12.5, FR-12.6 |
| Relaterade NFR | NFR-02.2 |

---

## Beskrivning

Spelaren ångrar sitt senaste drag så att brädet och turen återställs till läget före draget.

---

## Förutsättningar

- Ett parti pågår.
- Spelaren har gjort minst ett drag i partiet.

---

## Huvudflöde

1. Spelaren väljer "Ångra".
2. Systemet återställer det senaste draget (stenen tas bort).
3. Systemet återställer turen till spelaren.
4. Systemet uppdaterar dragräknaren.
5. Spelaren kan göra ett nytt drag.

---

## Alternativa flöden

### AF-01: Det finns inget drag att ångra
Vid steg 1 har spelaren inte gjort något drag.

- Systemet avvisar "Ångra" och visar att det inte finns något att ångra.

### AF-02: Det är motståndarens drag att ångra
Vid steg 1 är det motståndarens senaste drag som skulle ångras.

- Systemet begränsar ångra till spelarens egna senaste drag, eller frågar om motståndarens drag också ska ångras (beroende på läge).

### AF-03: Partiet är avslutat
Vid steg 1 är partiet redan avslutat.

- Systemet avvisar "Ångra".

---

## Postconditions

**Lyckat:** Det senaste draget är borttaget och spelaren kan göra om draget.

**Misslyckat:** Inget ändras och spelaren har fått information om varför.

---

## Särskilda krav

- Visuell återkoppling på ångringen ska visas inom 100 ms (NFR-02.2).

---

## Öppna frågor

- Ska ångra vara tillgängligt i online-partier mot vän, eller endast mot datorn och lokalt?
- Ska spelaren kunna ångra flera drag i följd?
