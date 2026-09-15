# Sekvensdiagram – UC-21, UC-22 och UC-25: konto, inloggning och inloggningsmetod

Det här är det enda flödet i systemet med **externa aktörer på andra sidan systemgränsen**:
e-posttjänsten (EP) och identitetsleverantören (IDP). Det gör diagrammet användbart för mer än
ordningen mellan anrop — det visar var personuppgifter lämnar systemet, vilket är precis de
punkter NFR-07.4 och NFR-07.8 sätter gränser för.

Valet av metod (UC-25) står först och är medvetet kort: den leder vidare till UC-22 eller UC-24 och
äger själv ingen inloggningslogik. Felmeddelandet i UC-22 är generiskt av två skäl samtidigt —
FR-14.5 och NFR-07.7 säger samma sak, och det är därför raden är kopplad till båda.

```mermaid
sequenceDiagram
    participant SP as Spelare
    participant KL as Klient<br/>React SPA
    participant API as Backend<br/>REST
    participant DB as Databas<br/>PostgreSQL
    participant EP as E-posttjänst<br/>extern
    participant IDP as Identitetsleverantör<br/>extern

    Note over SP,IDP: UC-25 — välj inloggningsmetod

    SP  ->>  KL  : Öppnar inloggningssidan
    KL  -->> SP  : Visar tillgängliga metoder
    SP  ->>  KL  : Väljer e-post och lösenord
    Note right of KL: Är en metod nere visas det innan valet<br/>AF-01 · FR-25.3

    Note over SP,DB: UC-22 — logga in

    SP  ->>  KL  : Anger e-postadress och lösenord
    KL  ->>  API : Begär inloggning över TLS 1.2 eller senare (NFR-07.1)
    API ->>  DB  : Slår upp kontot
    DB  -->> API : Kontot
    API ->>  API : Verifierar lösenord mot bcrypt-hash (NFR-07.6)

    alt Uppgifterna stämmer
        API ->>  DB  : Skapar en aktiv session (FR-14.2)
        DB  -->> API : Session
        API -->> KL  : Inloggad
        KL  -->> SP  : Vidare till menyn, spelaren är inloggad
    else Fel uppgifter
        API ->>  DB  : Räknar misslyckade försök i följd (FR-14.6)
        API -->> KL  : Generiskt felmeddelande (FR-14.5, NFR-07.7)
        KL  -->> SP  : Försök igen, inget fält pekas ut
    else Kontot är tillfälligt låst
        API -->> KL  : Besked om när kontot kan användas igen (FR-14.7)
    else Tekniskt fel
        API -->> KL  : Felmeddelande med möjlighet att försöka igen (FR-14.8)
    end

    Note over SP,EP: UC-21 — skapa ett konto

    SP  ->>  KL  : Anger synligt namn, e-postadress och lösenord
    KL  ->>  API : Begär registrering
    API ->>  API : Validerar format och lösenordsregler (FR-13.2)

    alt E-postadressen är ledig
        API ->>  DB  : Skapar kontot (FR-13.4)
        API ->>  EP  : Skickar bekräftelse till adressen
        EP  -->> SP  : E-post
        API -->> KL  : Konto skapat, spelaren är inloggad
    else E-postadressen finns redan
        API -->> KL  : Erbjuder inloggning i stället (FR-13.3)
    else Uppgifterna är ogiltiga
        API -->> KL  : Markerar fältet och visar vilken regel som brister (AF-02)
    end

    Note over API,IDP: Social inloggning går via UC-24 — IDP får inte fler uppgifter än kopplingen kräver (NFR-07.8)
```

---

**Relaterade UC:** UC-21, UC-22, UC-24, UC-25, UC-30 · **Krav:** FR-13.1 – FR-13.5, FR-14.1 – FR-14.8, FR-25.1 – FR-25.5, NFR-07.1, NFR-07.4, NFR-07.6 – NFR-07.8 · **Testas av:** AC-21-01 – AC-21-07, AC-22-01 – AC-22-06, AC-25-01 – AC-25-05
