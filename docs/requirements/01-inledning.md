# Gomoku 
# 1. Introduktion

## 1.1 Syfte

Detta dokument definierar programvarukraven för **Gomoku Web Application** — en online,
webbläsarbaserad implementering av det klassiska japanska strategispelet "Fem i rad" (Gomoku /
Omok). Det fungerar som en auktoritativ referens för utvecklare, testare, designers och
intressenter under hela projektets livscykel.

## 1.2 Omfattning

Systemet gör det möjligt för spelare att:

- Spela Gomoku mot en AI-motståndare eller mot andra registrerade spelare online i realtid
- Hantera en spelarprofil, visa statistik och spåra spelhistorik
- Få tillgång till en global topplista och jämföra rankningar
- Utöva sina rättigheter som registrerad person i enlighet med GDPR

Systemet täcker **inte**: skrivbords-/native-applikationer, turneringsadministration eller betalda
prenumerationsfunktioner.

## 1.3 Definitioner och förkortningar

| Begrepp | Förklaring |
|---------|------------|
| Administratör | En användare som kan hantera rapporter och modereringsärenden i systemet. |
| AI-motståndare | En datorstyrd motståndare som spelaren kan spela mot. |
| FR | Förkortning för Functional Requirement (funktionellt krav). Beskriver vad systemet ska kunna göra. |
| GDPR | EU:s allmänna dataskyddsförordning (EU) 2016/679 som reglerar hur personuppgifter får behandlas. |
| Gomoku | Ett brädspel där målet är att få fem stenar i rad. |
| Gästspelare | En spelare som använder spelet utan att ha ett registrerat konto. |
| NFR | Förkortning för Non-Functional Requirement (icke-funktionellt krav). Beskriver krav på till exempel prestanda, säkerhet och användbarhet. |
| Parti | Ett Gomoku-spel från start tills någon vinner, förlorar eller partiet slutar oavgjort. |
| Spelare | En person som spelar Gomoku, antingen mot datorn eller mot en annan spelare. |
| Spelplan | Området där spelarna placerar sina stenar under ett parti. |
| Sten | En svart eller vit spelpjäs som placeras på spelplanen. |
| UC | Förkortning för Use Case (användningsfall). Beskriver hur en aktör använder systemet för att uppnå ett mål. |

## 1.4 Aktörer

Förkortningarna används i `07-use-cases-overview.md`. Namnen är desamma som i
användningsfallen — vid konflikt gäller `00-begreppslista.md`.

| Aktör | Förk. | Typ | Beskrivning |
|-------|-------|------|-------------|
| Spelare | SP | Primär, människa | Den som spelar ett parti. Samlingsroll för gästanvändare och registrerad spelare; de flesta användningsfall skiljer inte på dem. |
| Gästanvändare | GÄ | Primär, människa | En oautentiserad besökare. Kan spela mot AI:n men har inte åtkomst till historik, rankningar eller sociala funktioner. |
| Registrerad spelare | RS | Primär, människa | En autentiserad användare med en profil. Har åtkomst till alla spellägen, historik, topplista och GDPR-självbetjäningsfunktioner. |
| Motståndare | MO | Primär, människa | Den andra mänskliga spelaren i ett parti, lokalt eller online. |
| Administratör | AD | Primär, människa | Plattformsoperatör som hanterar användarkonton, rapporter och modereringsärenden samt granskar GDPR-efterlevnad. |
| Dataskyddsombud (DPO) | DPO | Primär, människa | Övervakar GDPR-efterlevnad, granskar revisionsloggar, hanterar svar på dataintrång och hanterar eskalerade förfrågningar från registrerade. |
| AI-motståndare | AI | Sekundär, system | Datorstyrd spelare som genererar drag med hjälp av en spelalgoritm. Rankas inte på topplistan. |
| E-posttjänst | EP | Sekundär, extern | Tredjepartsleverantör av transaktionella e-postmeddelanden: verifieringar, lösenordsåterställningar och bekräftelser. |
| Identitetsleverantör | IDP | Sekundär, extern | Extern inloggningstjänst (t.ex. Google) som används vid social inloggning. |
| Tredjepartsleverantör | TP | Sekundär, extern | Databehandlare som behandlar personuppgifter för vår räkning, till exempel en samtyckesbevakad analystjänst. |

**Inte aktörer.** "Systemet" och "Databasen" förekom tidigare som sekundära aktörer i 23
användningsfall. De är interna komponenter, inte aktörer — ingen av dem konsumerar ett resultat
utifrån. Referenserna är borttagna.

## 1.5 Översikt över dokumentstrukturen

| Avsnitt | Innehåll |
|---------|---------|
| 00 – begreppslista | en ordlista specifikt för detta projekt |
| 01 – Inledning | Introduktion till projektet, syfte och omfattning |
| 02 – Funktionella krav | Beskriver vad systemet ska kunna göra |
| 03 – Kompletterande krav | Kompletterande krav, begränsningar och antaganden |
| 04 – Icke-funktionella krav | Krav på bland annat prestanda, kompatibilitet, säkerhet, tillgänglighet och GDPR |
| 05 – Begreppsmodell | Centrala begrepp i systemet och relationerna mellan dem |
| 06 – User Journey | Beskriver användarens flöde och interaktion med systemet |
| 07 – Use Cases Overview | Översikt över systemets användningsfall och aktörer |
| 08 – Use Cases och Test Cases | Koppling mellan användningsfall, krav och testfall |
| 09 – Journal | Dagliga anteckningar om arbetet och vad som har gjorts |
| 10 – Reflektioner | Reflektioner över kravfångsten och hur förståelsen av systemet har förändrats |
| use-cases/ | Beskrivningar av varje användningsfall och dess flöde |
