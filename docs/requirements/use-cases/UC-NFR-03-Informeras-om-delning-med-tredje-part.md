# UC-03: Informeras om delning med tredje part

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-03 |
| **Namn** |Informeras om delning med tredje part|
| **Version** | 1.0 |
| **Primär aktör** |Spelare|
| **Sekundär aktör** |Systemet,Tredjepartsleverantör |
| **Relaterade FR** | |
| **Relaterade NFR** |NFR-11.1, NFR-11.2|
| **GDPR-referens** |Artikel 28, Artikel 46|


## Beskrivning
Spelaren vill kunna få information om hur personuppgifter behandlas av tredje part och om uppgifterna överförs internationellt.
## Förutsättningar
- Personuppgifter behandlas eller delas med en tredje part.

## Huvudflöde

1. Spelaren väljer att läsa information om behandling av personuppgifter.

2. Systemet visar information om tredje parter som behandlar personuppgifter.

3. Systemet beskriver vilken behandling den tredje parten utför.

4. Systemet visar information om eventuell internationell överföring av personuppgifter.

5. Spelaren läser informationen.

## Alternativa flöden

### AF-01: Ingen internationell överföring sker
Vid steg 4 överförs inga personuppgifter internationellt.
- Systemets information visar att ingen sådan överföring sker.

### AF-02: Personuppgifter delas inte med tredje part
Vid steg 2 behandlas inga personuppgifter av tredje part.
- Systemet visar att inga personuppgifter delas med tredje part.
- Spelaren kan fortsätta läsa informationen.


## Postconditions
**Lyckat:** Spelaren har kunnat ta del av information om tredje parts behandling och eventuell internationell överföring.

**Misslyckat:** Informationen har inte kunnat visas.

## Testkriterier
- Spelaren ska kunna se om personuppgifter delas med tredje part.
- Om personuppgifter överförs till ett annat land ska spelaren kunna se information om detta.
- Personuppgifter ska bara överföras till länder där det finns tillräckligt dataskydd.
