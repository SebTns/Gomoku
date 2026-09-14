# UC-NFR-07: Spelaren får återkoppling efter en handling

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-NFR-07 |
| **Namn** | Spelaren får återkoppling efter handling |
| **Version** | 1.1 |
| **Primär aktör** | Spelare |
| **Sekundär aktör** | — |
| **Relaterade FR** | FR-08.2, FR-08.5, FR-08.6, FR-08.7, FR-08.10, FR-04.7, FR-06.4 |
| **Relaterade NFR** | NFR-02.2, NFR-02.5, NFR-02.7, NFR-06.1 – NFR-06.3, NFR-04.1 |
| **Relaterade AC** | AC-02-01, AC-02-03, AC-02-05 |

## Beskrivning
Spelaren vill få tydlig återkoppling på vad som hänt efter varje handling, så att det aldrig är
oklart om ett drag gick igenom, vems tur det är eller varför en handling avvisades.

## Förutsättningar
- Spelaren har startat ett parti.
- Spelaren har utfört en handling som systemet kan svara på.

## Huvudflöde

1. Spelaren startar ett parti mot datorn.
2. Systemet visar vilken färg spelaren har och vem som börjar (FR-04.7).
3. Spelaren gör sitt drag.
4. Systemet markerar den placerade stenen och uppdaterar dragräknaren (FR-08.5, FR-08.7).
5. Systemet visar att det är datorns tur.
6. Systemet visar att datorn beräknar sitt drag (FR-06.4).
7. Systemet visar datorns drag och lämnar tillbaka turen till spelaren (FR-08.6).
8. Flödet upprepas tills partiet avgörs.
9. Systemet visar resultatet och markerar den avgörande raden (FR-08.10).

## Alternativa flöden

### AF-01: Spelaren väljer en upptagen punkt
Vid steg 3 väljer spelaren en punkt där det redan ligger en sten.
- Systemet ger återkoppling om att punkten är upptagen (FR-08.2).
- Turen ligger kvar hos spelaren.
- Spelaren kan välja en annan punkt.

### AF-02: Spelaren försöker spela utanför sin tur
Vid steg 3 är det inte spelarens tur.
- Systemet ger återkoppling om att det inte är spelarens tur.
- Brädet är oförändrat.

### AF-03: Ett fel uppstår
Vid valfritt steg misslyckas en systemåtgärd.
- Systemet visar ett felmeddelande på engelska som beskriver vad som hänt och nästa steg
  (NFR-04.1).
- Spelaren har minst en väg vidare (NFR-04.6).

## Postconditions

**Lyckat:** Systemet har gett tydlig och korrekt återkoppling som gör det möjligt för spelaren att
förstå resultatet av sina handlingar.

**Misslyckat:** Systemet har inte presenterat någon återkoppling, eller presenterat återkoppling
som är otydlig, felaktig eller inte stämmer med systemets aktuella tillstånd.

## Särskilda krav
- Återkoppling ska visas inom 100 ms från klick eller tryck (NFR-02.2).
- Återkopplingen ska inte enbart bygga på färg (NFR-06.3), så att den fungerar för färgblinda
  spelare.
- Kontrasten mellan text och bakgrund ska vara minst 4,5:1 (NFR-06.2).
- Systemet ska uppfylla WCAG 2.1 nivå AA (NFR-06.1).

## Öppna frågor
- Ska systemet begära en bekräftelse på varje drag innan det genomförs? Tidigare version av denna
  fil beskrev ett sådant flöde ("Systemet frågar ifall det draget är det som spelaren är nöjd
  med"), men det motsäger UC-02 där draget genomförs direkt och `00-begreppslista.md` som säger
  att en placerad sten är permanent. Antingen skrivs UC-02 om eller så stryks bekräftelsesteget.
  Som det står nu gäller UC-02.
- Ska återkoppling också ges via skärmläsare, och i så fall med vilken formulering? NFR-06.1
  kräver det indirekt men ingen text är bestämd.
