# UC-NFR-06: Responstid efter handlning 

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-NFR-06 |
| **Namn** |Systemets responstid efter Spelares handling  |
| **Version** | 1.0 |
| **Primär aktör** |Systemet |
| **Sekundär aktör** |Spelare |
| **Relaterade FR** | |
| **Relaterade NFR** | NFR-02.1 - NFR-02.7|

## Beskrivning
En till två meningar om vad aktören vill uppnå. Inga tekniska lösningar.
Systemet ska ge en responstid enligt krav som finns 

## Förutsättningar
- Vad som måste gälla innan flödet st.
- Spelaren befinner sig i ett pågående parti 
- Spelplanen är tillgänglig för spelaren
- Det är spelarens tur att göra ett drag
- Spelet är aktivt och ej avslutat

## Huvudflöde

1. Aktören gör något.
2. Systemet svarar med något.
3. ...

1. Spelaren väljer en ledig skärningspunkt på spelplanen
2. Systemet regristrear spelarens handling 
3. Systemet uppdaterar planen och visar resultatet av handlingen inom angiven responstid
4. Systemet byter tur till nästa spelare.

## Alternativa flöden
i
### AF-01: Kort namn på avvikelsen
Vid steg N inträffar X.
- Systemet gör Y.
- Aktören kan Z.

1.Vid steg 1 väljer spelaren en upptagen skärningspunkt
- Systemet avvisar handlingen inom angiven responstid
- Systemet behåller sedan spelarens tur 

1. Vid steg 1 försöker spelaren placera en sten när det inte är spelarens tur 
- Suystemet kommer att avvisa handlingen inom angiven responstid 
- Systemet behåller aktuell spelordning

## Postconditions

**Lyckat:** Systemet har behandlat spelarens handlingar inom den angivna responstiden och uppdaterat spelet

**Misslyckat:** Systemet har ej reagerat inom dem angivna responstiderna xor uppdaterat spelets state

## Särskilda krav
- Systemets responstid efter en spelarhandling ska uppfylla NFR-02.1 - NFR-02.7

## Öppna frågor
- Vilken exakt tid ska gälla för varje spelarhandling 
- Från vilken tidpunkt ska responstiden börja mätas
- Ska samma responstid gälla för både giltiga och ogiltiga handlingar 

---

**Skrivregler**

- Numrera stegen. Ett steg = en handling.
- Växla mellan aktör och system i stegen, så att det syns vem som gör vad.
- Varje alternativt flöde ska ange vilket steg i huvudflödet det bryter från.
- Skriv inte in lösningar ("en knapp i React"), skriv beteende ("spelaren väljer").
- Fyll alltid i Relaterade FR och NFR — det är de som gör spårbarhetsmatrisen möjlig.

