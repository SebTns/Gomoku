# Om diagrammen i den här mappen

Diagrammen i projektet ligger på två ställen, och det är avsiktligt.

## Var diagrammen bor

| Diagram | Plats | Varför där |
|---------|-------|------------|
| Begreppsmodell | `requirements/05-begreppsmodell.md` | Hör ihop med kravtexten och läses tillsammans med den. |
| User journeys (UJ-01 – UJ-04) | `requirements/06-user-journey.md` | Samma sak — journeyn är en del av avsnittet, inte en bilaga. |
| Use case-diagram | `requirements/07-use-cases-overview.md` | Tio diagram som sorterar användningsfallen på aktör. |
| UML för beteende | `diagrams/uml/` | Fristående diagram som flera användningsfall delar på. |

Mappen `diagrams/journey/` innehåller därför bara den här filen. User journey-diagrammen ligger i
avsnitt 06 eftersom de hör till löptexten.

## Format

Alla diagram är skrivna i **Mermaid** direkt i markdown, inte som bildfiler. Skälet är
spårbarhet: ett diagram som är text hamnar i diffen när någon ändrar det, och går att granska i en
pull request. En exporterad PNG gör ingetdera.

GitHub renderar Mermaid-block automatiskt. Ett diagram som visas som rå kod betyder nästan alltid
att kodblockets avslutande fence (tre backticks) saknas — det felet fanns i `05-begreppsmodell.md` och är rättat.

## Innehåll i `diagrams/uml/`

| Fil | Typ | Realiserar |
|-----|-----|-----------|
| `Bjuda_in_en_van.md` | Aktivitetsdiagram | UC-03 |
| `UC-02-aktivitetsdiagram-gor-ett-drag.md` | Aktivitetsdiagram | UC-02 |
| `UC-02-sekvensdiagram-gor-ett-drag.md` | Sekvensdiagram | UC-02, UC-09 |
| `Tillstandsdiagram-partiets-livscykel.md` | Tillståndsdiagram | Partiets status |
| `Tillstandsdiagram-turordning.md` | Tillståndsdiagram | Turordningen |
