# 2. Funktionella krav

Kraven är formulerade som verifierbara systemkrav ("Systemet ska ...") och härledda ur
use case UC-01 – UC-32 samt UC-NFR-01 – UC-NFR-07. Varje krav ska gå att testa med
minst ett testfall (se `Acceptance-Criterias/`).

**Formregler för denna fil**

- Ett krav = en mening = en testbar sak.
- Inga lösningsförslag (t.ex. "med React"), bara vad systemet ska göra.
- Inga user stories här — de hör hemma i backloggen, inte i kravspecen.

**Om numreringen.** FR-numret är ett grupperingsnummer och sammanfaller inte alltid med numret på
det use case gruppen realiserar — FR-01 realiserar till exempel UC-06. Det är raden
**Realiserar** under varje rubrik som anger kopplingen, inte numret. Numren ändras inte i
efterhand, eftersom testfall och acceptanskriterier redan refererar till dem.

---

## FR-01: Applikationsstart

**Realiserar:** UC-06 Starta spelet

| ID | Krav |
|----|------|
| FR-01.1 | Systemet ska visa en startsida när applikationen öppnas. |
| FR-01.2 | Startsidan ska erbjuda valen "Play vs Computer", "Play with a Friend" och "Game Rules" (NFR-13.1). |
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
| FR-02.4 | Systemet ska tilldela standardnamnet "Player 1" om spelaren inte anger något namn (NFR-13.2). |
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
| FR-03.8 | Om spelaren avbryter bekräftelsen enligt FR-03.7 ska det pågående partiet fortsätta och inget nytt parti ska skapas. |
| FR-03.9 | Om spelaren bekräftar enligt FR-03.7 ska det pågående partiet avslutas innan spelaren fortsätter med konfigurationen av ett nytt parti. |



---

## FR-04: Välja färg

**Realiserar:** UC-04 Välja färg

| ID | Krav |
| --- | --- |
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
| --- | --- |
| FR-05.1 | Systemet ska erbjuda tre svårighetsgrader, benämnda "Easy", "Medium" och "Hard" i gränssnittet (NFR-13.1). |
| FR-05.2 | Systemet ska förvälja Medium. |
| FR-05.3 | Systemet ska visa en kort beskrivning av vad varje svårighetsgrad innebär. |
| FR-05.4 | Systemet ska endast erbjuda val av svårighetsgrad när motståndaren är datorn. |
| FR-05.5 | Systemet ska låsa svårighetsgraden under ett pågående parti. |
| FR-05.6 | Systemet ska komma ihåg senast valda svårighetsgrad till nästa parti. |
| FR-05.7 | Systemet ska starta ett parti på Medium om vald svårighetsgrad inte kan tillämpas. |

---

## FR-06: Spela mot datorn

**Realiserar:** UC-05 Spela mot datorn

| ID | Krav |
| --- | --- |
| FR-06.1 | Systemet ska starta ett parti mot datorn när spelaren valt svårighetsgrad och bekräftat. |
| FR-06.2 | Systemet ska låta datorn göra sitt drag automatiskt när det är datorns tur. |
| FR-06.3 | Systemet ska endast tillåta datorn att placera en sten på en ledig skärningspunkt. |
| FR-06.4 | Systemet ska visa att datorn beräknar sitt drag medan draget tas fram. |
| FR-06.5 | Systemet ska kontrollera efter varje drag, oavsett vem som gjort det, om någon har fem i rad. |
| FR-06.6 | Om datorn inte kan göra ett drag ska systemet visa ett felmeddelande, pausa partiet och låta spelaren välja mellan att försöka igen och att avsluta partiet. |
| FR-06.7 | Systemet ska bevara partitillståndet när ett parti pausas enligt FR-06.6. |
| FR-06.8 | Systemet ska visa resultatet när partiet avslutas. |
| FR-06.9 | Om datorns drag inte kan beräknas inom 3 sekunder ska systemet automatiskt försöka beräkna draget en gång till. Om det andra försöket också misslyckas ska systemet hantera felet enligt FR-06.6. |

---

## FR-07: Bjuda in en vän

**Realiserar:** UC-03 Bjud in en vän

| ID | Krav |
| --- | --- |
| FR-07.1 | Systemet ska generera en unik inbjudningslänk när spelaren väljer att spela mot en vän. |
| FR-07.2 | Systemet ska låta spelaren kopiera eller dela inbjudningslänken. |
| FR-07.3 | Systemet ska låta en inbjudan förfalla efter 15 minuter om den inte använts. |
| FR-07.4 | Systemet ska visa ett väntläge för inbjudaren tills motståndaren har anslutit. |
| FR-07.5 | Systemet ska starta partiet automatiskt när båda spelarna har anslutit. |
| FR-07.6 | Systemet ska avvisa en ogiltig eller förfallen inbjudan och förklara varför för den som försöker ansluta. |
| FR-07.7 | Systemet ska låta inbjudaren avbryta en inbjudan innan motståndaren anslutit. |
| FR-07.8 | Systemet ska begränsa varje parti till två spelare och avvisa ytterligare anslutningsförsök. |
| FR-07.9 | Systemet ska visa motståndarens synliga spelarnamn för båda spelarna när partiet startar. |
| FR-07.10 | Systemet ska göra en avbruten inbjudningslänk ogiltig, så att ingen kan ansluta med den. |

---

## FR-08: Göra ett drag

**Realiserar:** UC-02 Gör ett drag

| ID | Krav |
| --- | --- |
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
| FR-08.14 | Systemet ska endast räkna en obruten rad om exakt fem stenar av samma färg som vinst. |
| FR-08.15 | Systemet ska inte utse en vinnare när en obruten rad av samma färg består av sex eller fler stenar (överlinje). |
| FR-08.16 | Systemet ska kontrollera vinstvillkoret i FR-08.14 och FR-08.15 endast utifrån den rad som den senast placerade stenen ingår i. |
| FR-08.17 | Systemet ska registrera tidpunkten för varje drag, så att svarstiden enligt NFR-02.2 och NFR-02.4 kan mätas i efterhand. |

---

## FR-09: Ge upp

**Realiserar:** UC-11 Ge upp

| ID | Krav |
| --- | --- |
| FR-09.1 | Systemet ska låta spelaren ge upp ett pågående parti. |
| FR-09.2 | Systemet ska visa en bekräftelse innan uppgivandet genomförs, eftersom handlingen inte går att ångra. |
| FR-09.3 | Systemet ska registrera uppgivandet och tilldela motståndaren vinsten. |
| FR-09.4 | Systemet ska visa resultatvyn med information om vem som vann och vem som gav upp. |
| FR-09.5 | Systemet ska förhindra att spelaren ger upp om partiet redan är avslutat. |
| FR-09.6 | Om spelaren avbryter bekräftelsen ska uppgivandet inte genomföras och partiet ska fortsätta. |

---

## FR-10: Avsluta ett parti

**Realiserar:** UC-12 Avsluta ett parti

| ID | Krav |
| --- | --- |
| FR-10.1 | Systemet ska låta spelaren avsluta ett pågående parti utan att en vinnare utses. |
| FR-10.2 | Systemet ska visa en bekräftelse innan partiet avslutas. |
| FR-10.3 | Systemet ska ändra partiets status från PÅGÅENDE till AVSLUTAT när spelaren bekräftar. |
| FR-10.4 | Systemet ska visa en sammanfattning av partiet (antal drag och spelare) när det avslutas. |
| FR-10.5 | Systemet ska inte registrera en vinnare eller förlorare när partiet avslutas manuellt. |

---

## FR-11: Spelhistorik

**Realiserar:** UC-17 Spelhistorik

| ID | Krav |
| --- | --- |
| FR-11.1 | Systemet ska visa en lista över spelarens tidigare avslutade partier. |
| FR-11.2 | Systemet ska visa information om varje tidigare parti, inklusive datum, motståndare, brädstorlek, svårighetsgrad och resultat. |
| FR-11.3 | Systemet ska låta spelaren sortera historiken efter datum, resultat eller motståndare. |
| FR-11.4 | Systemet ska låta spelaren öppna ett tidigare parti från historiken för att se dragföljden. |
| FR-11.5 | Systemet ska radera spelhistoriken för gästspelare senast 30 dagar efter att partiet avslutats. *(Kopplat till NFR-07.5)* |

---

## FR-12: Ångra ett drag

**Realiserar:** UC-19 Ångra ett drag

| ID | Krav |
| --- | --- |
| FR-12.1 | Systemet ska låta spelaren ångra sitt senaste giltiga drag. |
| FR-12.2 | Systemet ska återställa brädet till tillståndet innan det senaste draget gjordes. |
| FR-12.3 | Systemet ska tillåta ångring av drag i partier mot datorn och i lokala partier på samma enhet (UC-18). |
| FR-12.4 | Systemet ska återlämna turen till spelaren när ett drag ångras. |
| FR-12.5 | Systemet ska förhindra att spelaren ångrar ett drag om motståndaren redan har gjort sitt nästa drag. |
| FR-12.6 | Systemet ska visa en bekräftelse innan ett drag ångras i ett lokalt parti, eftersom det påverkar båda spelarna vid samma enhet. |
| FR-12.7 | Systemet ska inte tillåta ångring i online-partier mot en vän. |
| FR-12.8 | Om inget drag har gjorts i partiet ska systemet avvisa ångringen och visa att det inte finns något att ångra. |
| FR-12.9 | Systemet ska avvisa ångring av ett drag i ett parti som redan är avslutat. |
| FR-12.10 | Systemet ska minska dragräknaren med ett när ett drag ångras. |

> **Löst motsägelse.** FR-12.3 angav tidigare att ångring endast är tillåten mot datorn, samtidigt
> som FR-12.6 beskrev hur ångring bekräftas i ett parti mot en vän. Kraven uteslöt varandra.
> UC-19:s öppna fråga är avgjord så här: ångring tillåts mot datorn och i lokalt hot-seat-parti,
> där båda spelarna sitter vid samma skärm och kan se bekräftelsen. I online-partier är den inte
> tillåten (FR-12.7), eftersom motståndaren inte kan se vad som händer med brädet.

---

## FR-13: Skapa ett konto

**Realiserar:** UC-21 Skapa ett konto

| ID | Krav |
| --- | --- |
| FR-13.1 | Systemet ska låta spelaren skapa ett konto med en e-postadress och ett lösenord. |
| FR-13.2 | Systemet ska acceptera en giltig e-postadress och ett lösenord som uppfyller säkerhetskraven (t.ex. minst 8 tecken). |
| FR-13.3 | Systemet ska avvisa registrering om e-postadressen redan är registrerad. |
| FR-13.4 | Systemet ska skapa kontot och logga in spelaren automatiskt efter lyckad registrering. |
| FR-13.5 | Systemet ska visa ett felmeddelande om registreringen misslyckas. |

---

## FR-14: Logga in

**Realiserar:** UC-22 Logga in

| ID | Krav |
| --- | --- |
| FR-14.1 | Systemet ska låta spelaren logga in med sitt användarnamn/e-postadress och lösenord. |
| FR-14.2 | Systemet ska skapa en aktiv användarsession när inloggningen är lyckad. |
| FR-14.3 | Systemet ska visa ett felmeddelande när inloggningsuppgifterna är felaktiga. |
| FR-14.4 | Systemet ska förhindra inloggning om kontot är tillfälligt blockerat (FR-29.6). |
| FR-14.5 | Systemet ska visa samma felmeddelande oavsett om e-postadressen eller lösenordet var fel, så att det inte går att avgöra vilka e-postadresser som är registrerade. |
| FR-14.6 | Systemet ska låsa kontot tillfälligt efter fem misslyckade inloggningsförsök i följd. |
| FR-14.7 | Systemet ska ange när ett tillfälligt låst konto kan användas igen. |
| FR-14.8 | Om inloggningen inte kan genomföras på grund av ett tekniskt fel ska systemet visa ett felmeddelande och låta spelaren försöka igen. |

---

## FR-15: Radera ett konto

**Realiserar:** UC-23 Radera ett konto

| ID | Krav |
| --- | --- |
| FR-15.1 | Systemet ska låta en inloggad spelare radera sitt eget konto. |
| FR-15.2 | Systemet ska kräva att spelaren anger sitt lösenord innan kontot raderas, som en säkerhetskontroll. |
| FR-15.3 | Systemet ska visa en tydlig varning om att all data (inklusive spelhistorik och sparade partier) går förlorad vid radering. |
| FR-15.4 | Systemet ska efter bekräftelse radera kontots personuppgifter och anonymisera den data som måste bevaras, enligt FR-30.5 – FR-30.7. |
| FR-15.5 | Systemet ska logga ut spelaren och återgå till startsidan efter att kontot har raderats. |
| FR-15.6 | Om lösenordet enligt FR-15.2 är felaktigt ska systemet avvisa bekräftelsen och låta spelaren försöka igen, utan att kontot raderas. |
| FR-15.7 | Om spelaren avbryter bekräftelsen ska kontot behållas oförändrat. |
| FR-15.8 | Om raderingen inte kan genomföras ska systemet informera spelaren om att kontot finns kvar och låta spelaren försöka igen. |

> **Löst motsägelse.** FR-15.4 angav tidigare att *all* data raderas permanent. Det motsäger
> FR-30.7, NFR-12.5 och NFR-12.6, som säger att drag, partier och samtyckesregister bevaras i
> anonymiserad form — samtyckesregistren i minst 3 år enligt SR-03.4. Två dokument gav två svar
> på vad "radera kontot" betyder. GDPR-kraven gäller: personuppgifterna raderas, den bevarade
> datan anonymiseras. Varningstexten i FR-15.3 måste säga samma sak, annars lovar gränssnittet
> något systemet inte gör.

---

## FR-16: Lägg till inloggningsmetod

**Realiserar:** UC-24 Lägg till inloggningsmetod

| ID | Krav |
| --- | --- |
| FR-16.1 | Systemet ska låta en inloggad spelare lägga till en ny inloggningsmetod (t.ex. social inloggning) till sitt befintliga konto. |
| FR-16.2 | Systemet ska verifiera att den nya metoden inte redan är kopplad till ett annat konto. |
| FR-16.3 | Systemet ska kräva att spelaren bekräftar sitt nuvarande lösenord innan en ny metod läggs till. |
| FR-16.4 | Systemet ska uppdatera kontot med den nya inloggningsmetoden och visa en bekräftelse med samtliga kopplade metoder. |
| FR-16.5 | Om metoden redan är kopplad till spelarens eget konto ska systemet informera spelaren och inte lägga till den igen. |
| FR-16.6 | Om den externa identitetsleverantören nekar kopplingen ska systemet informera spelaren och lämna kontots befintliga metoder oförändrade. |
| FR-16.7 | Om spelaren avbryter flödet hos den externa leverantören ska ingen metod läggas till. |

---

## FR-17: Starta sparat parti

**Realiserar:** UC-27 Starta sparat parti

| ID | Krav |
| --- | --- |
| FR-17.1 | Systemet ska visa en lista över spelarens sparade partier. |
| FR-17.2 | Systemet ska låta spelaren välja ett sparat parti för att återuppta det. |
| FR-17.3 | Systemet ska återställa brädet, turtillståndet och alla andra partiparametrar (som svårighetsgrad) när partiet startas. |
| FR-17.4 | Systemet ska låta spelaren importera en nedladdad datafil för att starta ett sparat parti. |
| FR-17.5 | Systemet ska visa ett felmeddelande om det sparade partiet inte kan laddas (t.ex. korrupt fil). |

---

## FR-18: Ändra kontoinställningar

**Realiserar:** UC-30 Ändra kontoinställningar

| ID | Krav |
| --- | --- |
| FR-18.1 | Systemet ska låta en inloggad spelare visa och ändra sin profilinformation (t.ex. synligt spelarnamn, e-postadress). |
| FR-18.2 | Systemet ska validera att den nya informationen är giltig innan den sparas. |
| FR-18.3 | Systemet ska uppdatera kontot och visa en bekräftelse när ändringarna har sparats. |
| FR-18.4 | Systemet ska visa ett felmeddelande om ändringen inte kan genomföras. |

---

## FR-19: Byta lösenord

**Realiserar:** UC-31 Byta lösenord

| ID | Krav |
| --- | --- |
| FR-19.1 | Systemet ska låta en inloggad spelare byta sitt lösenord. |
| FR-19.2 | Systemet ska kräva att spelaren anger sitt nuvarande lösenord för verifiering. |
| FR-19.3 | Systemet ska kontrollera att det nya lösenordet uppfyller säkerhetskraven (t.ex. minst 8 tecken). |
| FR-19.4 | Systemet ska spara det nya lösenordet och visa en bekräftelse. |
| FR-19.5 | Systemet ska visa ett felmeddelande om det nuvarande lösenordet är felaktigt eller om det nya lösenordet inte uppfyller kraven. |

---

## FR-20: Oavgjort

**Realiserar:** UC-14 Oavgjort

| ID | Krav |
| --- | --- |
| FR-20.1 | Systemet ska kontrollera efter varje giltigt drag om spelplanen är full. |
| FR-20.2 | Om spelplanen är full och ingen spelare har fått fem i rad ska systemet avsluta partiet som oavgjort. |
| FR-20.3 | Systemet ska visa i resultatvyn att partiet slutade oavgjort. |
| FR-20.4 | När partiet har avslutats som oavgjort ska systemet förhindra ytterligare drag. |
| FR-20.5 | Om det sista draget fyller spelplanen och samtidigt skapar fem i rad ska systemet registrera resultatet som vinst och inte som oavgjort. |

---

## FR-21: Spela lokalt på samma enhet

**Realiserar:** UC-18 Spela multiplayer lokalt

| ID | Krav |
| --- | --- |
| FR-21.1 | Systemet ska erbjuda ett lokalt läge där två spelare turas om vid samma enhet. |
| FR-21.2 | Systemet ska låta båda spelarna ange var sitt synliga spelarnamn innan partiet startar. |
| FR-21.3 | Systemet ska visa båda spelarnas namn och färg i turindikatorn under hela partiet. |
| FR-21.4 | Systemet ska växla turen mellan de två spelarna på samma enhet efter varje giltigt drag. |
| FR-21.5 | Systemet ska genomföra ett lokalt parti utan nätverksanslutning. |
| FR-21.6 | Systemet ska inte generera någon inbjudningslänk i lokalt läge. |
| FR-21.7 | Systemet ska begränsa ett lokalt parti till exakt två spelare. |

---

## FR-22: Visa spelregler

**Realiserar:** UC-20 Visa spelregler

| ID | Krav |
| --- | --- |
| FR-22.1 | Systemet ska visa en regelsammanfattning när spelaren väljer "Game Rules". |
| FR-22.2 | Regelsammanfattningen ska beskriva spelets mål, hur ett drag görs, vinstvillkoret och när partiet blir oavgjort, på engelska (NFR-13.2). |
| FR-22.3 | Regelsammanfattningen ska ange att vinstvillkoret är exakt fem i rad och att sex eller fler i rad inte är en vinst (SR-01.3). |
| FR-22.4 | Systemet ska återföra spelaren till den vy hen kom ifrån när reglerna stängs. |
| FR-22.5 | Systemet ska gå vidare till konfigurationsvyn om spelaren väljer att starta ett parti direkt från regelvyn. |
| FR-22.6 | Om regelsammanfattningen inte kan laddas ska systemet visa ett felmeddelande med möjlighet att försöka igen. |
| FR-22.7 | Regelsammanfattningen ska vara åtkomlig både från startsidan och från ett pågående parti, utan att partiet påverkas. |

---

## FR-23: Återställ spelet

**Realiserar:** UC-32 Återställ spelet

| ID | Krav |
| --- | --- |
| FR-23.1 | Systemet ska låta spelaren återställa ett pågående parti till ett tomt bräde. |
| FR-23.2 | Systemet ska begära en bekräftelse innan återställningen genomförs, eftersom den inte går att ångra. |
| FR-23.3 | Systemet ska behålla partiets konfiguration — brädstorlek, färger, motståndartyp och svårighetsgrad — vid en återställning. |
| FR-23.4 | Systemet ska nollställa dragräknaren och dragregistret när partiet återställs. |
| FR-23.5 | Systemet ska ge första draget till svart efter en återställning (FR-04.3). |
| FR-23.6 | Systemet ska kräva båda spelarnas samtycke innan ett parti mot en vän återställs. |
| FR-23.7 | Systemet ska inte tillåta återställning av ett avslutat parti. |
| FR-23.8 | Om spelaren avbryter bekräftelsen ska partiet fortsätta oförändrat. |

---

## FR-24: Samtycke till cookies

**Realiserar:** UC-NFR-01 Ge samtycke till cookie  
**Kopplade begränsningar:** SR-02.7, SR-03.1

| ID | Krav |
| --- | --- |
| FR-24.1 | Systemet ska visa ett cookie-meddelande vid gästanvändarens första besök, innan några icke-nödvändiga cookies laddas. |
| FR-24.2 | Meddelandet ska förklara vilka cookies som används och för vilket ändamål. |
| FR-24.3 | Systemet ska erbjuda valen "Accept All", "Accept Necessary" och egna val. |
| FR-24.4 | Systemet ska spara gästanvändarens val med tidpunkt och den version av informationen som visades. |
| FR-24.5 | Systemet ska endast ladda cookies som omfattas av det sparade valet. |
| FR-24.6 | Systemet ska behandla ett stängt meddelande utan aktivt val som ett nekande av icke-nödvändiga cookies. |
| FR-24.7 | Systemet ska inte visa meddelandet igen så länge ett sparat val finns. |
| FR-24.8 | Systemet ska erbjuda "Cookie Settings" där ett tidigare val kan ändras eller återkallas. |
| FR-24.9 | Systemet ska göra det lika enkelt att återkalla ett samtycke som att lämna det. |

---

## FR-27: Tillgång till personuppgifter

**Realiserar:** UC-NFR-02 Begära tillgång till personuppgifter  
**Kopplade begränsningar:** SR-03.1, SR-03.2

| ID | Krav |
| --- | --- |
| FR-27.1 | Systemet ska låta en registrerad spelare begära en kopia av sina personuppgifter. |
| FR-27.2 | Systemet ska verifiera att begäran kommer från den registrerade spelaren själv. |
| FR-27.3 | Systemet ska registrera begäran med ett unikt begärande-ID, typ (ÅTKOMST), status och tidpunkt. |
| FR-27.4 | Systemet ska samla in samtliga personuppgifter som finns om spelaren. |
| FR-27.5 | Systemet ska tillhandahålla uppgifterna i ett strukturerat, maskinläsbart format. |
| FR-27.6 | Systemet ska besvara begäran inom 30 dagar (SR-03.2). |
| FR-27.7 | Om begäran inte kan behandlas ska systemet informera spelaren om orsaken och låta spelaren försöka igen. |
| FR-27.8 | Systemet ska inte lämna ut personuppgifter som rör en annan person i samma export. |

---

## FR-31: Information om behandling hos tredje part

**Realiserar:** UC-NFR-03 Informeras om delning med tredje part  
**Kopplade begränsningar:** SR-03.1, SR-03.3

| ID | Krav |
| --- | --- |
| FR-31.1 | Systemet ska visa vilka tredje parter som behandlar personuppgifter för systemets räkning. |
| FR-31.2 | Systemet ska beskriva vilken behandling varje tredje part utför. |
| FR-31.3 | Systemet ska ange om personuppgifter överförs till ett land utanför EES. |
| FR-31.4 | Vid en sådan överföring ska systemet ange vilka skyddsåtgärder som gäller. |
| FR-31.5 | Systemet ska visa att ingen överföring sker, när ingen överföring sker. |
| FR-31.6 | Systemet ska visa att inga personuppgifter delas med tredje part, när ingen delning sker. |
| FR-31.7 | Informationen ska vara nåbar utan att spelaren behöver logga in. |

---

## FR-25: Välj inloggningsmetod

**Realiserar:** UC-25 Välj inloggningsmetod

| ID | Krav |
| --- | --- |
| FR-25.1 | Systemet ska visa en lista över tillgängliga inloggningsmetoder på inloggningssidan. |
| FR-25.2 | Systemet ska låta spelaren välja en specifik inloggningsmetod genom att välja den. |
| FR-25.3 | Systemet ska dirigera spelaren till det specifika inloggningsflödet för den valda metoden (kopplat till UC-22 och UC-24). |
| FR-25.4 | Systemet ska visa ett tydligt felmeddelande och låta spelaren välja en annan metod eller avsluta om en vald inloggningsmetod är otillgänglig. |
| FR-25.5 | Systemet ska skapa en aktiv användarsession när inloggningen via vald metod är slutförd. |

---

## FR-26: Spara Parti
**Realiserar:** UC-26 Spara parti

| ID | Krav |
| --- | --- |
| FR-26.1 | Systemet ska låta spelaren spara ett pågående parti. |
| FR-26.2 | Systemet ska spara hela partitillståndet, inklusive stenarnas positioner, vems tur det är, spelarnas valda värg, brädstorlek och svårighetsgrad. |
| FR-26.3 | Systemet ska spara partitillståndet kopplat till den inloggade spelarens konto. |
| FR-26.4 | Systemet ska erbjuda alternativen "exportera till nedladdningsbar fil" eller "spara i webbläsarens lokala lagring" när spelaren inte är inloggad. |
| FR-26.5 | Systemet ska visa en bekräftelse för spelaren när partiet har sparats. |
| FR-26.6 | Systemet ska tillåta spelaren att skriva över ett tidigare sparat parti om spelaren bekräftar detta. |
| FR-26.7 | Systemet ska visa ett felmeddelande och fråga om spelaren vill försöka igen om sparningen misslyckas. |
| FR-26.8 | Systemet ska endast tillåta sparande av ett parti som har status pågående. |
| FR-26.9 | Systemet ska automatiskt spara partitillståndet vid sidomladdning eller tillfälligt nätverksavbrott. |

---

## FR-28: Rapportera ett tekniskt problem

**Realiserar:** UC-28 Rapportera ett tekniskt problem

| ID | Krav |
| --- | --- |
| FR-28.1 | Systemet ska låta spelaren öppna funktionen "Report a Problem" från spelet. |
| FR-28.2 | Systemet ska låta spelaren beskriva det tekniska problemet i ett fritextfält. |
| FR-28.3 | Systemet ska kräva en beskrivning av problemet innan rapporten kan skickas. |
| FR-28.4 | Om beskrivningen saknas ska systemet informera spelaren om detta och rapporten ska inte registreras. |
| FR-28.5 | Systemet ska registrera en giltig problemrapport för vidare hantering. |
| FR-28.6 | Systemet ska tilldela varje registrerad problemrapport ett unikt rapport-ID. |
| FR-28.7 | Systemet ska visa en bekräftelse när problemrapporten har registrerats. |
| FR-28.8 | Om problemrapporten inte kan registreras ska systemet informera spelaren om detta. |
| FR-28.9 | Efter ett misslyckat försök ska systemet låta spelaren försöka skicka problemrapporten igen. |
| FR-28.10 | Spelaren ska kunna avbryta rapporteringen utan att någon problemrapport registreras. |

## FR-29:Tillfälligt blockera en spelare 
**Realiserar:** UC-29 Tillfälligt blockera en spelare

| ID | Krav |
| --- | --- |
| FR-29.1 | Systemet ska låta administratören välja en spelare som ska blockeras tillfälligt. |
| FR-29.2 | Innan en blockering genomförs ska systemet visa spelarens namn, spelar-ID och det aktuella modereringsärendet. |
| FR-29.3 | Systemet ska låta administratören välja hur länge den tillfälliga blockeringen ska gälla. |
| FR-29.4 | Systemet ska kräva att administratören bekräftar blockeringen innan den genomförs. |
| FR-29.5 | Om administratören avbryter bekräftelsen ska ingen blockering genomföras. |
| FR-29.6 | När blockeringen har bekräftats ska systemet förhindra den blockerade spelaren från att delta i nya partier under den valda blockeringstiden. |
| FR-29.7 | Systemet ska registrera vilken spelare som blockerades, blockeringens starttid, blockeringens sluttid och vilket modereringsärende blockeringen är kopplad till. |
| FR-29.8 | Systemet ska informera administratören när blockeringen har genomförts. |
| FR-29.9 | Om blockeringen inte kan genomföras ska systemet informera administratören om detta och spelaren ska inte registreras som blockerad. |
| FR-29.10 | När blockeringstiden har gått ut ska systemet automatiskt ta bort den tillfälliga blockeringen. |
| FR-29.11 | Systemet ska informera den blockerade spelaren om att en blockering gäller och när den upphör, vid nästa inloggnings- eller spelstartsförsök. |
| FR-29.12 | Systemet ska ange orsakskategorin för blockeringen för den blockerade spelaren, utan att röja vem som har rapporterat. |
| FR-29.13 | Systemet ska låta en blockerad spelare slutföra ett parti som redan pågick när blockeringen trädde i kraft, men inte påbörja något nytt parti. |
| FR-29.14 | Systemet ska låta administratören välja om blockeringen ska omfatta alla spellägen eller endast partier mot andra spelare. |
| FR-29.15 | Systemet ska låta administratören häva en pågående blockering innan blockeringstiden har löpt ut, och registrera hävningen med tidpunkt och administratör. |

---

## FR-30: Begär radering av personuppgifter

**Realiserar:** UC-NFR-04 Begär radering av data  
**Kopplade begränsningar:** SR-03.1, SR-03.2, SR-03.4

| ID | Krav |
| --- | --- |
| FR-30.1 | Systemet ska låta en registrerad spelare begära radering av sina personuppgifter. |
| FR-30.2 | Systemet ska verifiera att begäran kommer från den registrerade spelaren själv innan raderingen påbörjas. |
| FR-30.3 | Systemet ska registrera varje raderingsbegäran med ett unikt begärande-ID, typ (RADERING), status och tidpunkt för mottagandet. |
| FR-30.4 | Systemet ska bekräfta för spelaren att begäran är mottagen, och ange senaste datum då raderingen ska vara genomförd. |
| FR-30.5 | Systemet ska identifiera samtliga datakategorier som är kopplade till spelaren innan raderingen genomförs. |
| FR-30.6 | Systemet ska radera personuppgifter som inte omfattas av en lagringsskyldighet. |
| FR-30.7 | Systemet ska anonymisera de poster som måste bevaras (samtyckesregister, begäranden, drag och partier) så att de inte kan kopplas till spelaren. |
| FR-30.8 | Systemet ska sätta begärans status till GENOMFÖRD och registrera tidpunkten när raderingen är klar. |
| FR-30.9 | Systemet ska skicka en bekräftelse på genomförd radering till spelarens registrerade e-postadress, på engelska (NFR-13.2). |
| FR-30.10 | Systemet ska genomföra raderingen inom 30 dagar från det att begäran verifierades (SR-03.2). |
| FR-30.11 | Om raderingen inte kan genomföras inom 30 dagar ska systemet underrätta dataskyddsombudet och informera spelaren om förseningen och ett nytt datum. |
| FR-30.12 | Om en rättslig skyldighet hindrar fullständig radering ska systemet radera övriga uppgifter, informera spelaren om vilka uppgifter som bevaras och på vilken rättslig grund. |
| FR-30.13 | Systemet ska förhindra att raderade eller anonymiserade personuppgifter kan återskapas efter att raderingen har genomförts. |

---

## FR-32: Granskning av eskalerade databegäranden

**Realiserar:** UC-NFR-08 Dataskyddsombudet granskar en raderingsbegäran  
**Kopplade begränsningar:** SR-03.1, SR-03.2, SR-03.3, SR-03.4

| ID | Krav |
| --- | --- |
| FR-32.1 | Systemet ska visa en lista över raderingsbegäranden som eskalerats till dataskyddsombudet. |
| FR-32.2 | Listan ska för varje begäran visa begärande-ID, mottagningsdatum, kvarvarande tid till 30-dagarsgränsen och orsaken till eskaleringen. |
| FR-32.3 | Systemet ska visa vilka datakategorier som är raderade, anonymiserade respektive kvar för en enskild begäran. |
| FR-32.4 | Systemet ska låta dataskyddsombudet registrera ett beslut med rättslig grund och motivering. |
| FR-32.5 | Systemet ska registrera beslutet med tidpunkt och vilket dataskyddsombud som fattade det. |
| FR-32.6 | Systemet ska underrätta den registrerade spelaren om utfallet av granskningen. |
| FR-32.7 | Systemet ska varna dataskyddsombudet när det återstår 5 dagar till 30-dagarsgränsen för en obeslutad begäran. |
| FR-32.8 | Systemet ska markera en begäran som passerat 30-dagarsgränsen utan beslut som försenad, och bevara avvikelsen för efterlevnadsgranskning. |

---

## Täckningsstatus – use case utan krav i denna fil

Kraven ovan täcker UC-01 – UC-14 och UC-17 – UC-32, samt UC-NFR-01 – UC-NFR-04 och UC-NFR-08.
Följande use case finns som filer i repot men saknar ännu krav här. Skriv in dem när
respektive UC är färdigskriven.

| Område | Berörda UC | Status |
|--------|-----------|--------|
| Partiavslut och resultat | UC-15 Förlust, UC-16 Vinst | saknas — täcks indirekt av FR-08.9 och FR-08.14, men behöver egna krav för resultatvyn |
| GDPR – övriga | UC-NFR-05 Ta bort konto | täcks av FR-15 och FR-30; inget eget FR-block |
| Prestanda och återkoppling | UC-NFR-06, UC-NFR-07 | saknas — kraven ligger som NFR-02 |

---

## Bilaga A: User stories (backlog — inte krav)

Materialet nedan är den ursprungliga behovsinsamlingen och ligger kvar som spårbarhet till
var kraven kommer ifrån. **Det är inte kravspecifikation** — formreglerna ovan säger att user
stories hör hemma i backloggen. Varje story ska antingen ha blivit ett `Systemet ska ...`-krav
ovan eller stå kvar här som ett identifierat men ännu inte formulerat behov.

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
