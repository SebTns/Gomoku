# Aktivitetsdiagram – UC-11 Ge upp

Ett kort flöde, men det innehåller två saker som är lätta att rita bort: att partiet kan vara
**redan avslutat** när knappen trycks, och att bekräftelsen går att ångra utan att något
registreras. FR-09.6 gör den andra till ett eget flöde — "Cancel" är inte samma sak som "inget
hände".

```mermaid
flowchart TD
    A([Start]) --> B{Är partiet fortfarande pågående?}

    B -- Nej --> C[Resign avvisas och resultatvyn visas<br/>AF-02 · FR-09.5]
    C --> Z([Slut])

    B -- Ja --> D[Spelaren väljer Resign<br/>FR-09.1]
    D --> E[Systemet begär bekräftelse, handlingen går inte att ångra<br/>FR-09.2]
    E --> F{Bekräftar spelaren?}

    F -- Cancel --> G[Partiet fortsätter oförändrat, inget registreras<br/>AF-01 · FR-09.6]
    G --> Z

    F -- Ja --> H[Partiet avslutas med status AVSLUTAT<br/>FR-10.3]
    H --> I[Förlust registreras för spelaren, vinst för motståndaren<br/>FR-09.3 · SR-01.5]
    I --> J[Resultatvyn visar vem som vann och vem som gav upp<br/>FR-09.4]
    J --> K[Ytterligare drag förhindras, väg vidare finns<br/>NFR-04.6]
    K --> Z
```

---

**Relaterade UC:** UC-11 · **Krav:** FR-09.1 – FR-09.6, FR-10.3, SR-01.5, NFR-04.1, NFR-04.6 · **Testas av:** AC-11-01 – AC-11-03
