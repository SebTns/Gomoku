# Sekvensdiagram – UC-02 Gör ett drag, med UC-09

Ett helt varv: spelarens drag, vinstkontroll, datorns svar och partiavslut.

Lagren följer SR-02: klienten är ett React-SPA (SR-02.2), backend exponerar REST och WebSockets
(SR-02.3, SR-02.4) och spellogiken ligger i ett eget domänlager som enligt NFR-09.1 ska gå att
enhetstesta utan webbläsare.

Tidskraven är utsatta på de pilar där de faktiskt mäts. NFR-02.2 mäts i klienten och NFR-02.4 i
domänlagret — de är alltså två olika mätningar trots att båda säger 100 ms.

```mermaid
sequenceDiagram
    participant SP as Spelare
    participant KL as Klient<br/>React SPA
    participant API as Backend<br/>REST / WebSocket
    participant DOM as Spellogik<br/>domänlager

    Note over SP,DOM: Spelarens drag — UC-02 huvudflöde

    SP  ->>  KL  : Klick på skärningspunkt
    KL  -->> SP  : Visuell återkoppling ≤ 100 ms (NFR-02.2)
    KL  ->>  API : draget {rad, kolumn}
    API ->>  DOM : validera(bräde, rad, kolumn)
    DOM -->> API : Giltigt (FR-08.1)
    API ->>  DOM : placera(bräde, rad, kolumn, SVART)
    DOM -->> API : Uppdaterat bräde
    API ->>  DOM : kontrolleraVinst(bräde, sistaDraget)
    DOM -->> API : Ingen femma ≤ 100 ms (NFR-02.4)
    API -->> KL  : Godkänt, turen går till VIT (FR-08.4)

    Note over SP,DOM: Motståndarens svar — UC-09

    API ->>  DOM : beräknaDrag(bräde, svårighetsgrad)
    DOM -->> API : Drag ≤ 3 s (NFR-02.3)
    API ->>  DOM : kontrolleraVinst(bräde, datornsDrag)
    DOM -->> API : Exakt fem i rad — VIT vinner (FR-08.14)
    API -->> KL  : Partiet avslutat (FR-08.9)
    KL  -->> SP  : Resultatvy med markerad vinstrad (FR-08.10)
```

---

**Relaterade UC:** UC-02, UC-09 · **Krav:** FR-08.1 – FR-08.14, NFR-02.2 – NFR-02.4 · **Testas av:** AC-02-01, AC-02-05, AC-09-02
