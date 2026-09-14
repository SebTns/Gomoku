[← Tillbaka till README](../../README.md)

# 10. Reflektioner

> **Den här filen är en disposition, inte en text.** Reflektionerna är den del av inlämningen som
> betygsätts individuellt och som ska bygga på din egen journal i avsnitt 09. Rubrikerna och
> frågorna nedan är strukturen; innehållet måste vara ditt.
>
> Mallen ber uttryckligen om **förändrade antaganden, motsägelser och upptäckter** — inte om en
> sammanfattning av vad som gjordes. En reflektion som beskriver arbetsgången svarar på fel fråga.

---

## 10.1 Antaganden som visade sig felaktiga

Vad trodde du om systemet i vecka 1 som inte stämde i vecka 5? Vad fick dig att ändra dig?

*Underlag i journalen: raderna "Vad vi ändrade som redan var skrivet".*

## 10.2 Motsägelser i kraven

Under arbetet hittades ett antal motsägelser. Välj de som säger något, och skriv om vad de
berodde på — inte bara vad de var.

| Motsägelse | Var | Hur den löstes |
|---|---|---|
| Vinstvillkoret: exakt fem eller fem-eller-fler? | UC-02 öppen fråga mot `00-begreppslista.md` | Begreppslistan är normerande. FR-08.14, FR-08.15, AC-02-06 och AC-02-06b. |
| Svarstid: 0,33 sekunder eller 100 ms? | AC-02 mot NFR-02.2 | Kravet gäller framför acceptanskriteriet. |
| Är spelarnamnet en personuppgift? | NFR-03.3 mot `00-begreppslista.md` | Begreppslistan säger ja. NFR-03.3 delades i .3, .6 och .7. |
| Ångra: bara mot datorn, eller också mot vän? | FR-12.3 mot FR-12.6 | Kraven uteslöt varandra. Löst med FR-12.7. |
| Radering: all data, eller anonymiserad? | FR-15.4 mot FR-30.7 och NFR-12.5 | GDPR-kraven gäller. FR-15.4 skrevs om. |
| Spårbarhet som pekade fel | UC-NFR-04 hänvisade till UC-18, UC-NFR-07, UC-NFR-09 | Numren kom från lärarens referensrepo. Rättade. |
| Engelska eller svenska felmeddelanden? | SR-04.3 mot NFR-04.1 | Löst — engelska gäller. Regeln var bara ett antagande och är nu skriven som NFR-13. |

Frågan att svara på: *varför* uppstod de? Flera av dem har samma orsak — vilken?

Den sista av dem är värd en egen tanke. Motsägelsen såg ut att vara en detalj — vilket språk
felmeddelanden skrivs på — men när den skulle lösas visade det sig att **språkregeln aldrig hade
varit ett krav**. Den stod som SR-04.3, ett antagande, och antaganden testas inte. NFR-04.1 var
det enda stället regeln fick praktisk verkan, och det täckte bara felmeddelanden — inte
knapptexter, regeltext, cookie-texter eller e-post.

Ett antagande som inget krav bygger vidare på är osynligt tills något motsäger det. Det är
motsatsen till problemet i 10.3: där pekade spårbarheten fel, här fanns den inte alls.

### Ett fel i ett testfall, inte i ett krav

Det första utkastet av AC-02-06 beskrev ett brädläge som inte kan existera: *fem stenar i rad som
redan är blockerad i båda ändar, så att femman inte utlöst vinst*. Men fem i rad **är** en vinst —
blockerade ändar spelar roll för hotbilden i spelet, inte för vinstvillkoret. Uppställningen
förutsatte alltså ett parti som redan var avgjort.

Felet upptäcktes av en gruppmedlem vid genomläsning, inte av något verktyg. Kravet (FR-08.15) var
hela tiden rätt; det var testfallet som beskrev fel väg dit.

Det korrekta brädläget är att en **lucka fylls**: två grupper av samma färg på samma linje med en
ledig punkt emellan, där ingen grupp är fem lång. Det är det enda sätt en överlinje kan uppstå,
eftersom en rad som byggs en sten i taget avgör partiet redan vid fem.

Reflektionen värd att dra: ett testfall kan vara logiskt omöjligt utan att något syns. Det
kompilerar inte, det körs inte, och en granskning som bara kontrollerar att kravnumret stämmer
hittar det aldrig. Den maskinella kontrollen av kravreferenser hade godkänt kriteriet —
alla FR-nummer i det fanns och pekade rätt. Spårbarhet säger att kravet är kopplat till ett test.
Den säger ingenting om att testet är möjligt att köra.

## 10.3 Upptäckter

Vad blev synligt först när något ritades eller skrevs ned, som inte syntes i texten?

Exempel som finns dokumenterade:

- Aktivitetsdiagrammet för UC-02 gick inte att rita med ett Ja/Nej-beslut. Förgreningen tvingade
  fram frågan *hur lång är raden*, och därmed AF-06.
- Use case-översikten gjorde tre överlappande sätt att starta ett parti synliga (UC-01, UC-06,
  UC-13). I filerna syntes det inte.
- UC-28 och UC-29 möts i samma modereringsärende men refererar aldrig till varandra.
- Dataskyddsombudet stod som aktör utan att äga något användningsfall, trots att UC-NFR-04
  eskalerar till det.

## 10.4 Krav som inte går att verifiera fullt ut

Sammanställningen finns i `08-use-cases-och-test-cases.md` 8.5. Reflektionen är en annan sak:
vad betyder det för kvalitetsarbetet att ett krav är verifierbart i teorin men inte i en pipeline?

Tre fall värda att skriva om:

- **NFR-12.4** — att raderade uppgifter inte ska kunna återskapas är ett negativt påstående. Det
  går att falsifiera, inte att bevisa.
- **NFR-05.2 och SR-03.2** — 12 månader respektive 30 dagar. Simulerad tid verifierar logiken,
  inte att produktionsjobbet kör.
- **NFR-06.6** — två minuter för en ny spelare. Testbart, men bara med människor.

## 10.5 Är det kvalitet? Är det krav?

*Fredagsleverabel 13, utpekad som VG-krav.*

Gå igenom kraven du arbetat med och svara systematiskt på två frågor per krav:

1. **Vem förväntar sig detta resultat, och varför?** En stakeholder är en namngiven källa till
   förväntade resultat. Står den namngiven någonstans?
2. **Hur observerar man skillnaden mellan rätt och fel?** Om svaret är "det gör man inte" är det
   inte ett krav — kursens definition säger att ett krav är en förväntan som är testbar.

Kursens definitioner som checklista:

> Kvalitet är när det förväntade resultatet inträffar.
> Ett krav är en förväntan som är testbar. Om den inte är testbar är det inte ett krav.
> En stakeholder är en namngiven källa till förväntade resultat.
> En aktör är en konsument av förväntade resultat.
> En testare är en namngiven stakeholder för kvalitet.

Definitionen av aktör användes redan som rättesnöre: "Systemet" stod som aktör i 25
användningsfall och ströks, eftersom systemet inte konsumerar något resultat.

## 10.6 Vad jag skulle gjort annorlunda

Inte en artighetsfras. Vad i arbetsordningen skapade det merarbete som beskrivs i 10.2?

---

## Att ta bort innan inlämning

Den här rutan, och alla rubriker du inte skrivit under.
