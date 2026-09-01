# UC-XX: Namn på use case

| Fält | Värde |
|------|-------|
| **Use Case ID** | UC-XX |
| **Namn** | |
| **Version** | 1.0 |
| **Primär aktör** | |
| **Sekundär aktör** | |
| **Relaterade FR** | |
| **Relaterade NFR** | |

## Beskrivning
En till två meningar om vad aktören vill uppnå. Inga tekniska lösningar.

## Förutsättningar
- Vad som måste gälla innan flödet startar.

## Huvudflöde

1. Aktören gör något.
2. Systemet svarar med något.
3. ...

## Alternativa flöden

### AF-01: Kort namn på avvikelsen
Vid steg N inträffar X.
- Systemet gör Y.
- Aktören kan Z.

## Postconditions

**Lyckat:** Vad som gäller när flödet gått igenom.

**Misslyckat:** Vad som gäller när flödet avbrutits.

## Särskilda krav
- Hänvisningar till NFR som gäller specifikt här.

## Öppna frågor
- Sådant gruppen inte beslutat ännu.

---

**Skrivregler**

- Numrera stegen. Ett steg = en handling.
- Växla mellan aktör och system i stegen, så att det syns vem som gör vad.
- Varje alternativt flöde ska ange vilket steg i huvudflödet det bryter från.
- Skriv inte in lösningar ("en knapp i React"), skriv beteende ("spelaren väljer").
- Fyll alltid i Relaterade FR och NFR — det är de som gör spårbarhetsmatrisen möjlig.

