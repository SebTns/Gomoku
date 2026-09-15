# Aktivitetsdiagram – UC-05 Spela mot datorn

Hela vägen från startsidan till resultatvyn, med de fyra alternativa flödena som grenar.
Realiserar FR-06.1 – FR-06.9 och FR-08.8.

Tidsgränsen på datorns drag är med som ett eget beslut, inte som en fotnot: FR-06.9 säger att
systemet ska försöka **en gång till** innan felet hanteras, och det syns bara i ett flöde. Det är
samma uppdelning som i sekvensdiagrammet för UC-02, där NFR-02.3 mäts på datorns svar och NFR-02.2
på klientens återkoppling — två olika mätningar trots att båda handlar om tid.

```mermaid
flowchart TD
    A([Start]) --> B[Startsidan visas]
    B --> C[Spelaren väljer Play vs Computer]
    C --> D[Systemet visar svårighetsgraderna]
    D --> E[Spelaren väljer svårighetsgrad]
    E --> F{Kan partiet startas?}

    F -- Nej --> G[Partiet kunde inte startas, spelaren stannar kvar<br/>AF-01 · FR-06.1]
    G --> C

    F -- Ja --> H[Spelplanen visas, svart gör första draget]
    H --> I{Spelarens tur}

    I -- Avbryter --> J[Bekräftelse begärs<br/>AF-04 · FR-10.2]
    J --> K{Bekräftar spelaren?}
    K -- Nej --> I
    K -- Ja --> L[Partiet avslutas utan vinnare<br/>UC-11, UC-12]
    L --> Z([Slut])

    I -- Gör ett drag --> M[Draget utförs på en ledig punkt<br/>UC-02 · FR-08.1]
    M --> N{Avgjorde draget partiet?}

    N -- Ja --> O[Resultatvyn visar vinnare eller oavgjort<br/>FR-06.8, FR-08.14]
    O --> Z

    N -- Nej --> P[Svarsdraget beräknas, spelaren ser att datorn tänker<br/>FR-06.2, FR-06.4]
    P --> Q{Svarade datorn inom 3 sekunder?}

    Q -- Nej --> R[Spelaren informeras om fördröjningen<br/>FR-06.9, NFR-02.3]
    R --> S{Andra försöket lyckas?}
    S -- Ja --> T[Datorns drag registreras<br/>FR-06.3]
    S -- Nej --> U[Partiet pausas och tillståndet bevaras<br/>AF-02 · FR-06.6, FR-06.7]
    U --> V{Försöka igen eller avsluta?}
    V -- Försök igen --> P
    V -- Avsluta --> L

    Q -- Ja --> T
    T --> W{Avgjorde draget partiet?}
    W -- Ja --> O
    W -- Nej --> I
```

---

**Relaterade UC:** UC-05, UC-01, UC-02, UC-08, UC-11 · **Krav:** FR-06.1 – FR-06.9, FR-08.8, NFR-02.3, NFR-04.2, NFR-04.6, NFR-09.3 · **Testas av:** AC-05-01 – AC-05-07
