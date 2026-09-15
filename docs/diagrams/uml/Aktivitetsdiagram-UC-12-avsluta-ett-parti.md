# Aktivitetsdiagram – UC-12 Avsluta ett parti

Skillnaden mot UC-11 är värd att se i ett diagram: här utses **ingen** vinnare (FR-10.5), och
statusen sparas innan partiet stängs (UC-12 steg 4). Att webbläsaren stängs är ett eget
alternativflöde — partiet ska gå att återuppta, vilket är samma krav som gör NFR-04.2 mätbart.

```mermaid
flowchart TD
    A([Start]) --> B[Spelaren väljer End Game<br/>FR-10.1]
    B --> C[Systemet begär bekräftelse<br/>FR-10.2]
    C --> D{Bekräftar spelaren?}

    D -- Cancel --> E[Partiet fortsätter som tidigare<br/>AF-01]
    E --> Z([Slut])

    D -- Stänger webbläsaren --> F[Partitillståndet bevaras för återanslutning<br/>AF-03 · NFR-04.2]
    F --> Z

    D -- Ja --> G[Partistatusen sparas: positioner, tur och inställningar]
    G --> H{Kunde statusen sparas?}

    H -- Nej --> I[Felmeddelande, spelaren stannar kvar i partiet<br/>AF-02]
    I --> J{Försöka igen?}
    J -- Ja --> G
    J -- Nej --> E

    H -- Ja --> K[Partiet avslutas med status AVSLUTAT utan vinnare<br/>FR-10.3, FR-10.5 · NFR-08.2]
    K --> L[Sammanfattning visas: antal drag och spelare<br/>FR-10.4]
    L --> M[Spelaren återförs till menyn och motståndaren informeras]
    M --> Z
```

---

**Relaterade UC:** UC-12, UC-11, UC-26, UC-27 · **Krav:** FR-10.1 – FR-10.5, NFR-04.2, NFR-04.6, NFR-08.2 · **Testas av:** AC-12-01 – AC-12-04
