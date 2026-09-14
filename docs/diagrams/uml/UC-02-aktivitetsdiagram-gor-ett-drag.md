# Aktivitetsdiagram – UC-02 Gör ett drag

Huvudflödet med samtliga sex alternativflöden som grenar. Realiserar FR-08.1 – FR-08.17.

Förgreningen efter en lyckad registrering frågar **hur lång raden är**, inte om det finns fem i
rad. Det är nödvändigt: ett Ja/Nej-beslut har inget svar för en rad på sex stenar, och det är
just den skillnaden FR-08.14 och FR-08.15 gör. Se AC-02-05 och AC-02-06.

```mermaid
flowchart TD
    A([Start]) --> B[Systemet visar vems tur det är]
    B --> C[/Spelaren väljer en skärningspunkt/]
    C --> D{Är det spelarens tur?}

    D -- Nej --> E[Draget avvisas, brädet oförändrat<br/>AF-02 · FR-08.3]
    E --> B

    D -- Ja --> F{Är punkten ledig?}
    F -- Nej --> G[Återkoppling: punkten upptagen<br/>AF-01 · FR-08.2]
    G --> C

    F -- Ja --> H[Stenen placeras och markeras<br/>FR-08.1, FR-08.5]
    H --> I[Draget registreras med position, färg,<br/>nummer och tidpunkt<br/>FR-08.12, FR-08.17]
    I --> J{Lyckades registreringen?}

    J -- Nej --> K[Brädet återställs, felmeddelande visas<br/>AF-05]
    K --> C

    J -- Ja --> L{Hur lång är raden genom<br/>den senast placerade stenen?}

    L -- Exakt fem --> M[Partiet avslutas, vinnare utses,<br/>raden markeras<br/>AF-03 · FR-08.9, FR-08.14]
    M --> Z([Slut])

    L -- Sex eller fler --> N[Ingen vinst — överlinje<br/>AF-06 · FR-08.15]
    N --> O

    L -- Kortare än fem --> O{Är brädet fullt?}
    O -- Ja --> P[Partiet avslutas som oavgjort<br/>AF-04 · FR-08.11, FR-20.2]
    P --> Z

    O -- Nej --> Q[Turen lämnas över till motståndaren<br/>FR-08.4]
    Q --> B
```

---

**Relaterat UC:** UC-02 · **Krav:** FR-08.1 – FR-08.17, NFR-02.2, NFR-02.4 · **Testas av:** AC-02-01 – AC-02-09
