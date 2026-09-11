# Aktivitetsdiagram – Bjuda in en vän

```mermaid
flowchart TD

    A([Start]) --> B[Spelaren väljer att spela med en vän]

    B --> C[Systemet skapar en unik inbjudningslänk]
    C --> D[Spelaren kopierar och delar länken]
    D --> E[Vännen öppnar länken]

    E --> F{Är länken giltig?}

    %% Ogiltig eller utgången länk
    F -- Nej --> G[Systemet visar att länken är ogiltig eller har gått ut]
    G --> H{Vad vill spelaren göra?}

    H -- Avsluta --> Z([Slut])
    H -- Vännen ber om en ny länk --> C

    %% Giltig länk
    F -- Ja --> I{Finns det plats i partiet?}

    %% Partiet är fullt
    I -- Nej --> J[Systemet nekar anslutningen]
    J --> K{Vad vill spelaren göra?}

    K -- Avsluta --> Z
    K --  Vännen ber om en ny länk --> C

    %% Vännen kan ansluta
    I -- Ja --> L[Vännen ansluter till partiet]
    L --> M[Systemet registrerar anslutningen]
    M --> N[Systemet visar båda spelarna]
    N --> O[Partiet startar]

    O --> Z
```
