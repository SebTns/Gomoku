# 02-funktionellakrav
### Denna fil är ej klar detta är en demo version vi måste skriva om alla krav som riktiga krav just nnu står dem som user stories!!!!

## SPELSTART 

- Som spelare vill jag välja spelplanens storlek (t.ex. 15x15 eller 19x19) så att jag kan spela enligt olika standarder.
- Som spelare vill jag kunna starta ett nytt spel så att jag kan börja spela mot en motståndare.
- Som spelare vill jag se vem som spelar svart respektive vitt så att jag vet vem som börjar (svart går alltid först enligt standardreglerna).


## Spelmekanik 

- Som spelare vill jag placera min spelbricka på en ledig ruta genom att klicka/trycka på den så att jag kan göra mitt drag.
- Som spelare vill jag att systemet markerar vems tur det är så att jag inte råkar spela utanför min tur.
- Som spelare vill jag inte kunna placera en bricka på en redan upptagen ruta så att spelets integritet upprätthålls.


## Vinstvillkor

- Som spelare vill jag att spelet automatiskt upptäcker när jag har fem brickor i rad (horisontellt, vertikalt eller diagonalt) så att spelet avgörs korrekt.
- Som spelare vill jag se en tydlig visuell markering av den vinnande raden så att jag förstår varför spelet tog slut.
- Som spelare vill jag att spelet meddelar oavgjort om brädet blir fullt utan att någon fått fem i rad.


## Regler/validering 

- Som spelare vill jag (i vissa varianter) hindras från "förbjudna drag" som dubbla treor för svart, om den regeln används, så att spelet följer officiella tävlingsregler.
- Som ny spelare vill jag kunna läsa en kort regelsammanfattning i spelet så att jag förstår hur man vinner.


## Granssnitt/UX

- Som spelare vill jag kunna ångra mitt senaste drag innan jag bekräftar det så att jag undviker misstag.
- Som spelare vill jag kunna starta om spelet utan att ladda om hela sidan/appen så att jag snabbt kan spela igen.
- Som spelare vill jag se en räknare eller logg över gjorda drag så att jag kan följa spelets förlopp.


## Motstand/flerspellagen

- Som spelare vill jag kunna spela mot en AI-motståndare med olika svårighetsgrader så att jag kan öva på egen hand.
- Som spelare vill jag kunna spela mot en vän lokalt på samma enhet (hot-seat) så att vi kan spela tillsammans utan internet.
- Som spelare vill jag kunna spela online mot en annan spelare i realtid så att jag kan utmana vänner på distans.

# 2. Funktionella krav

Kraven är formulerade som verifierbara systemkrav ("Systemet ska ...") och härledda ur
use case UC-01 – UC-xx. Varje krav ska gå att testa med minst ett testfall.

**Formregler för denna fil**

- Ett krav = en mening = en testbar sak.
- Inga lösningsförslag (t.ex. "med React"), bara vad systemet ska göra.
- Inga user stories här — de hör hemma i backloggen, inte i kravspecen.

---

## FR-01: Applikationsstart

**Realiserar:** UC-06 Starta spelet

| ID | Krav |
|----|------|
| FR-01.1 | Systemet ska visa en startsida när applikationen öppnas. |
| FR-01.2 | Startsidan ska erbjuda valen "Spela mot datorn", "Spela mot vän" och "Visa spelregler". |
| FR-01.3 | Systemet ska vara spelbart utan inloggning (gästläge). |
| FR-01.4 | Om applikationen inte kan laddas ska systemet visa ett felmeddelande med möjlighet att försöka igen. |
| FR-01.5 | Systemet ska visa startsidan inom en (1) navigering från valfri vy i spelet. |

---

## FR-02: Synligt spelarnamn

**Realiserar:** UC-07 Välj ditt synliga spelarnamn

| ID | Krav |
|----|------|
| FR-02.1 | Systemet ska låta spelaren ange ett synligt spelarnamn innan ett parti startas. |
| FR-02.2 | Systemet ska acceptera namn på 2–20 tecken bestående av bokstäver, siffror, bindestreck och understreck. |
| FR-02.3 | Systemet ska avvisa namn som bryter mot FR-02.2 och visa vilken regel som inte uppfylls. |
| FR-02.4 | Systemet ska tilldela ett standardnamn ("Spelare 1") om spelaren inte anger något namn. |
| FR-02.5 | Systemet ska visa spelarens namn i turindikatorn och i resultatvyn. |
| FR-02.6 | Systemet ska spara senast använda namn lokalt och föreslå det vid nästa besök. |
| FR-02.7 | Systemet ska inte tillåta namnbyte under ett pågående parti. |

---

## FR-03: Starta nytt parti

**Realiserar:** UC-01 Starta nytt parti

| ID | Krav |
|----|------|
| FR-03.1 | Systemet ska låta spelaren starta ett nytt parti från startsidan. |
| FR-03.2 | Systemet ska visa en konfigurationsvy med brädstorlek (15×15 som standard, 19×19 som alternativ), motståndartyp och färgval. |
| FR-03.3 | Systemet ska skapa ett parti med status `PÅGÅENDE` när spelaren bekräftar konfigurationen. |
| FR-03.4 | Systemet ska rendera ett tomt bräde av vald storlek och visa vem som gör första draget. |
| FR-03.5 | Systemet ska låta spelaren avbryta konfigurationen utan att något parti skapas. |
| FR-03.6 | Om partiet inte kan startas ska systemet visa ett felmeddelande och behålla spelaren i konfigurationsvyn. |
| FR-03.7 | Systemet ska begära bekräftelse innan ett pågående parti överges till förmån för ett nytt. |

---

## FR-04: Välja färg

**Realiserar:** UC-04 Välja färg

| ID | Krav |
|----|------|
| FR-04.1 | Systemet ska låta spelaren välja svart eller vit före partistart. |
| FR-04.2 | Systemet ska automatiskt tilldela motståndaren den färg som inte valdes. |
| FR-04.3 | Systemet ska låta svart göra första draget i varje parti. |
| FR-04.4 | Systemet ska slumpa färg om spelaren inte gör något aktivt val. |
| FR-04.5 | I ett parti mot en vän ska systemet lösa upp konflikten när båda spelarna vill ha samma färg, genom att den som bjöd in väljer först. |
| FR-04.6 | Systemet ska låsa färgvalet när partiet har startat. |
| FR-04.7 | Systemet ska visa vilken färg spelaren har innan första draget görs. |

---

## FR-05: Välja svårighetsgrad

**Realiserar:** UC-08 Välj svårighetsgrad

| ID | Krav |
|----|------|
| FR-05.1 | Systemet ska erbjuda tre svårighetsgrader: Lätt, Medel och Svår. |
| FR-05.2 | Systemet ska förvälja Medel. |
| FR-05.3 | Systemet ska visa en kort beskrivning av vad varje svårighetsgrad innebär. |
| FR-05.4 | Systemet ska endast erbjuda val av svårighetsgrad när motståndaren är datorn. |
| FR-05.5 | Systemet ska låsa svårighetsgraden under ett pågående parti. |
| FR-05.6 | Systemet ska komma ihåg senast valda svårighetsgrad till nästa parti. |
| FR-05.7 | Systemet ska starta ett parti på Medel om vald svårighetsgrad inte kan tillämpas. |

---

## FR-06: Spela mot datorn

**Realiserar:** UC-05 Spela mot datorn

| ID | Krav |
|----|------|
| FR-06.1 | Systemet ska starta ett parti mot datorn när spelaren valt svårighetsgrad och bekräftat. |
| FR-06.2 | Systemet ska låta datorn göra sitt drag automatiskt när det är datorns tur. |
| FR-06.3 | Systemet ska endast tillåta datorn att placera en sten på en ledig skärningspunkt. |
| FR-06.4 | Systemet ska visa att datorn beräknar sitt drag medan draget tas fram. |
| FR-06.5 | Systemet ska kontrollera efter varje drag, oavsett vem som gjort det, om någon har fem i rad. |
| FR-06.6 | Om datorn inte kan göra ett drag ska systemet visa ett felmeddelande, pausa partiet och låta spelaren välja mellan att försöka igen och att avsluta partiet. |
| FR-06.7 | Systemet ska bevara partitillståndet när ett parti pausas enligt FR-06.6. |
| FR-06.8 | Systemet ska visa resultatet när partiet avslutas. |

---

## FR-07: Bjuda in en vän

**Realiserar:** UC-03 Bjud in en vän

| ID | Krav |
|----|------|
| FR-07.1 | Systemet ska generera en unik inbjudningslänk när spelaren väljer att spela mot en vän. |
| FR-07.2 | Systemet ska låta spelaren kopiera eller dela inbjudningslänken. |
| FR-07.3 | Systemet ska låta en inbjudan förfalla efter 15 minuter om den inte använts. |
| FR-07.4 | Systemet ska visa ett väntläge för inbjudaren tills motståndaren har anslutit. |
| FR-07.5 | Systemet ska starta partiet automatiskt när båda spelarna har anslutit. |
| FR-07.6 | Systemet ska avvisa en ogiltig eller förfallen inbjudan och förklara varför för den som försöker ansluta. |
| FR-07.7 | Systemet ska låta inbjudaren avbryta en inbjudan innan motståndaren anslutit. |
| FR-07.8 | Systemet ska begränsa varje parti till två spelare och avvisa ytterligare anslutningsförsök. |
| FR-07.9 | Systemet ska visa motståndarens synliga spelarnamn för båda spelarna när partiet startar. |

---

## FR-08: Göra ett drag

**Realiserar:** UC-02 Gör ett drag

| ID | Krav |
|----|------|
| FR-08.1 | Systemet ska låta den spelare vars tur det är placera en sten på en ledig skärningspunkt genom klick eller tryck. |
| FR-08.2 | Systemet ska avvisa placering på en upptagen skärningspunkt utan att turen byts. |
| FR-08.3 | Systemet ska avvisa drag från en spelare vars tur det inte är. |
| FR-08.4 | Systemet ska byta tur efter varje giltigt drag. |
| FR-08.5 | Systemet ska markera den senast placerade stenen. |
| FR-08.6 | Systemet ska löpande visa vems tur det är, med spelarnamn och färg. |
| FR-08.7 | Systemet ska visa en dragräknare över antalet gjorda drag. |
| FR-08.8 | Systemet ska efter varje drag kontrollera om fem stenar av samma färg ligger i rad horisontellt, vertikalt eller diagonalt. |
| FR-08.9 | Systemet ska avsluta partiet och utse en vinnare när fem i rad uppstår. |
| FR-08.10 | Systemet ska markera den vinnande raden visuellt. |
| FR-08.11 | Systemet ska förklara partiet oavgjort när brädet är fullt utan att någon fått fem i rad. |
| FR-08.12 | Systemet ska registrera varje drag i ordning med position, färg och dragnummer. |
| FR-08.13 | Systemet ska förhindra fler drag efter att partiet avslutats. |

---

## Ej täckt av UC-01 – UC-08

Följande finns som use case-filer i repot men saknar ännu krav i denna fil. Skriv in dem
när respektive UC är färdigskriven:

| Område | Berörda UC |
|--------|-----------|
| Partiavslut och resultat | UC-11, UC-12, UC-14, UC-15, UC-16 |
| Spelhistorik och sparade partier | UC-17, UC-26, UC-27 |
| Konto och inloggning | UC-21 – UC-25, UC-30, UC-31 |
| Ångra drag, lokal multiplayer, regler, återställning | UC-18, UC-19, UC-20, UC-32 |
| Problemrapportering och moderering | UC-28, UC-29 |

# FR-28: Rapportera ett tekniskt problem

**Realiserar:** UC-28 Rapportera ett tekniskt problem

| ID | Krav |
| --- | --- |
| **FR-28.1** | Systemet ska låta spelaren rapportera ett tekniskt problem som har uppstått i spelet. |
| **FR-28.2** | Systemet ska låta spelaren beskriva vad som hände och vad som gick fel. |
| **FR-28.3** | Systemet ska kontrollera att nödvändig information finns med innan rapporten registreras. |
| **FR-28.4** | Systemet ska registrera problemrapporten för vidare hantering. |
| **FR-28.5** | Systemet ska visa en bekräftelse när problemrapporten har skickats. |
| **FR-28.6** | Om problemrapporten inte kan registreras ska systemet informera spelaren om detta. |
