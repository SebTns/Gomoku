# Sekvensdiagram – GDPR: radering av personuppgifter (UC-NFR-05 → UC-NFR-04 → UC-NFR-08)

Hela kedjan i ett diagram: spelaren tar bort sitt konto (UC-NFR-05), raderingen genomförs
(UC-NFR-04) och de fall som inte kan hanteras automatiskt hamnar hos dataskyddsombudet
(UC-NFR-08). Det är det enda flödet i systemet som **inte slutar när användaren är klar** — det
fortsätter i upp till 30 dagar och kan eskalera efteråt.

Två saker syns bara här:

- **Uppdelningen radera/anonymisera.** Användarposten och statistiken raderas, men samtyckesregistret,
  begäranden, drag och partier anonymiseras och bevaras (NFR-12.5, NFR-12.6, SR-03.4). Det är
  skillnaden mellan att uppfylla artikel 17 och att samtidigt kunna visa *att* den uppfyllts.
- **Eskaleringen har en mottagare.** UC-NFR-04 skickar två eskaleringar till dataskyddsombudet
  (AF-01 och AF-02) och UC-NFR-08 är vad som händer på andra sidan. Utan det paret står DPO som
  aktör utan att äga något flöde.

Samma negativa påstående som i NFR-12.4 — att raderade uppgifter inte ska kunna återskapas — går
inte att bevisa i ett diagram eller i ett test. Den verifieras mot fem namngivna sökvägar
(AC-NFR-04-05), och det är en medveten avgränsning.

```mermaid
sequenceDiagram
    participant RS as Registrerad spelare
    participant KL as Klient<br/>React SPA
    participant API as Backend<br/>REST
    participant DB as Databas<br/>PostgreSQL
    participant EP as E-posttjänst<br/>extern
    participant DPO as Dataskyddsombud

    Note over RS,EP: UC-NFR-05 — ta bort konto, självbetjäning

    RS  ->>  KL  : Väljer Delete Account
    KL  -->> RS  : Varning: irreversibelt, radering inom 30 dagar,<br/>historik anonymiseras (FR-15.3, NFR-12.2)
    RS  ->>  KL  : Anger lösenord, steg 1 av 2
    KL  ->>  API : Begär kontoborttagning över TLS 1.2 eller senare (NFR-07.1)
    API ->>  DB  : Verifierar lösenordet och skapar begäran med status PÅGÅENDE
    API ->>  EP  : Skickar tidsbegränsad bekräftelselänk, steg 2 av 2
    EP  -->> RS  : E-post
    RS  ->>  KL  : Klickar på bekräftelselänken
    KL  ->>  API : Bekräftar
    API ->>  DB  : Inaktiverar kontot omedelbart (FR-15.5)
    API ->>  API : Utlöser raderingsprocessen

    Note over API,DB: UC-NFR-04 — raderingen genomförs

    API ->>  DB  : Identifierar spelarens datakategorier
    DB  -->> API : Användarpost, samtyckesregister, begäranden, drag, partier, statistik
    API ->>  DB  : Raderar användarpost och statistik
    API ->>  DB  : Anonymiserar samtycke, begäranden, drag och partier (NFR-12.5, NFR-12.6)

    alt Allt kan genomföras inom 30 dagar
        API ->>  DB  : Status GENOMFÖRD med tidpunkt
        API ->>  EP  : Bekräftelse: raderingen är genomförd (NFR-12.3)
        EP  -->> RS  : E-post
    else Teknisk försening · AF-01
        API ->>  DPO : Eskalering: 30-dagarsgränsen hotas (NFR-12.2, SR-03.2)
        API -->> RS  : Förklaring och nytt datum, status förblir PÅGÅENDE
    else Rättslig lagringsskyldighet · AF-02
        API ->>  DPO : Eskalering: undantag enligt rättslig grund
        API -->> RS  : Besked om vilka uppgifter som bevaras och varför
    end

    Note over DPO,DB: UC-NFR-08 — dataskyddsombudet granskar

    DPO ->>  API : Öppnar eskalerade begäranden, flerfaktorsautentisering (SR-03.3)
    API -->> DPO : Begäran med kvarvarande tid och orsak till eskaleringen
    DPO ->>  API : Registrerar beslutet med rättslig grund och motivering
    API ->>  DB  : Bevarar beslutet anonymiserat i minst 3 år (NFR-12.6, SR-03.4)
    API ->>  EP  : Underrättar den registrerade om utfallet
    EP  -->> RS  : E-post
```

---

**Relaterade UC:** UC-NFR-02, UC-NFR-04, UC-NFR-05, UC-NFR-08, UC-23 · **Krav:** FR-15.1 – FR-15.5, FR-30.1 – FR-30.13, FR-32.1 – FR-32.8, NFR-12.1 – NFR-12.7, NFR-07.1, NFR-07.5, SR-03.1 – SR-03.4 · **Testas av:** AC-NFR-04-01 – AC-NFR-04-09, AC-NFR-08-01 – AC-NFR-08-05
