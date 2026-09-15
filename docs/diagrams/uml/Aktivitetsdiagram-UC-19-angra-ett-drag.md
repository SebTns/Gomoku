# Aktivitetsdiagram – UC-19 Ångra ett drag

Flödet ser enkelt ut, men den avgörande förgreningen är **vilket slags parti** det gäller. Den
lösta motsägelsen i FR-12 sitter här: ångring är tillåten mot datorn och i lokalt parti på samma
enhet, men **inte** i ett online-parti mot en vän (FR-12.3 mot FR-12.7). I ett hot-seat-parti sitter
båda spelarna vid samma skärm och kan se bekräftelsen — i ett online-parti kan motståndaren inte se
vad som händer med brädet, och då är en ångring något helt annat.

Notera också att det som återställs är ett **dragregister**, inte en sten: modellen i
`05-begreppsmodell.md` säger att en placerad sten inte kan tas bort. Det är FR-12.2 som gör
operationen till en registerfråga.

```mermaid
flowchart TD
    A([Start]) --> B{Pågår partiet?}

    B -- Nej --> C[Undo avvisas<br/>AF-03 · FR-12.9]
    C --> Z([Slut])

    B -- Ja --> D{Vilket slags parti?}
    D -- Online mot vän --> E[Undo tillåts inte i online-parti<br/>FR-12.7]
    E --> Z

    D -- Mot datorn eller lokalt --> F{Har spelaren ett eget drag att ångra?}

    F -- Nej --> G[Systemet visar att det inte finns något att ångra<br/>AF-01 · FR-12.8]
    G --> Z

    F -- Motståndarens senaste --> H[Undo begränsas till spelarens eget senaste giltiga drag<br/>AF-02 · FR-12.1, FR-12.5]
    H --> Z

    F -- Ja, eget drag --> I{Lokalt parti på samma enhet?}
    I -- Ja --> J[Bekräftelse begärs, draget påverkar båda spelarna<br/>FR-12.6]
    J --> K{Bekräftar spelaren?}
    K -- Nej --> Z

    K -- Ja --> L
    I -- Nej, mot datorn --> L[Dragregistret backas ett steg och turen återlämnas<br/>FR-12.2, FR-12.4]
    L --> M[Dragräknaren minskas med ett<br/>FR-12.10]
    M --> N[Bekräftelsen visas inom 100 ms<br/>NFR-02.2]
    N --> O[Spelaren kan göra ett nytt drag]
    O --> Z
```

---

**Relaterade UC:** UC-19, UC-02, UC-18 · **Krav:** FR-12.1 – FR-12.10, NFR-02.2 · **Testas av:** AC-19-01 – AC-19-07 (AC-19-07 väntar på gruppbeslut)
