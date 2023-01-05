# Card Game with German Cities

Open Data

## Data Selection

- City name
- City population
- City image of shape
- City image of 1 sight
- Space: 
- Sky: Percentage of white xmas
- Air: Number of airfields and heliports -> as little symbols
- Car: length of freeways (count Kilometerpunkte BAB)
- Bike or public transportation:
- People:
- Nature: ? Waldfläche ?
- Ground:

## Wikidata

List of all cities in Germany with a minimum of 100.000 people. Show an image and Regionalschlüssel.

- [Download result as SPARQL](https://query.wikidata.org/sparql?query=%23defaultView%3AImageGrid%0ASELECT%20DISTINCT%20%3Fitem%20%3FitemLabel%20%3Fpopulation%20%3Frs%20%3Fnamed%20%3Fimage%20%3Fflag%20WHERE%20%7B%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22de%22.%20%7D%0A%20%20%7B%0A%20%20%20%20SELECT%20DISTINCT%20%3Fitem%20WHERE%20%7B%0A%20%20%20%20%20%20%3Fitem%20p%3AP1082%2Fpsv%3AP1082%2Fwikibase%3AquantityAmount%20%3Fpopulation_.%0A%20%20%20%20%20%20%3Fitem%20wdt%3AP31%2Fwdt%3AP279*%20wd%3AQ515%20.%0A%20%20%20%20%20%20%3Fitem%20wdt%3AP17%2Fwdt%3AP279*%20wd%3AQ183%20.%0A%20%20%20%20%20%20FILTER(%3Fpopulation_%20%3E%20%22100000%22%5E%5Exsd%3Adecimal)%0A%20%20%20%20%7D%0A%20%20%20%20LIMIT%20100%0A%20%20%7D%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP1082%20%3Fpopulation%20%7D%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP1388%20%3Frs%20%7D%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP18%20%3Fimage%20%7D%0A%23%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP41%20%3Fflag%20%7D%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP138%20%3Fnamed%20%7D%0A%7D%0AORDER%20BY%20DESC(%3Fpopulation))
- [Show query](https://w.wiki/6BqR)
- [Show result](https://w.wiki/6BqT)

```
#defaultView:ImageGrid
SELECT DISTINCT ?item ?itemLabel ?population ?rs ?named ?image ?flag WHERE {
  SERVICE wikibase:label { bd:serviceParam wikibase:language "de". }
  {
    SELECT DISTINCT ?item WHERE {
      ?item p:P1082/psv:P1082/wikibase:quantityAmount ?population_.
      ?item wdt:P31/wdt:P279* wd:Q515 .
      ?item wdt:P17/wdt:P279* wd:Q183 .
      FILTER(?population_ > "100000"^^xsd:decimal)
    }
    LIMIT 100
  }
  OPTIONAL { ?item wdt:P1082 ?population }
  OPTIONAL { ?item wdt:P1388 ?rs }
  OPTIONAL { ?item wdt:P18 ?image }
#  OPTIONAL { ?item wdt:P41 ?flag }
  OPTIONAL { ?item wdt:P138 ?named }
}
ORDER BY DESC(?population)
```

## Data Sources

- WFS Points Of Interest Open
  - https://www.mcloud.de/web/guest/suche/-/results/filter/relevance/spatial%3A5%252E295%2C54%252E952%2C14%252E611%2C47%252E100/10/detail/461731F5-62B1-45A9-8E7E-BF6AF93E3EFA
  - Downloaddienst Points of Interests (POI) für Bundesbehörden für das Gebiet der Bundesrepublik Deutschland. Der Dienst stellt die POI Themen Flughäfen, Grenzübergänge, Hubschrauberlandeplätze, Kilometrierungen BAB und Seehäfen für das Gebiet der Bundesrepublik Deutschland bereit.
  - Datenlizenz Deutschland – Namensnennung – Version 2.0 (Veränderungen, Bearbeitungen, neue Gestaltungen oder sonstige Abwandlungen sind mit einem Veränderungshinweis im Quellenvermerk zu versehen.)
  - Quellenvermerk und Veränderungshinweis sind wie folgt zu gestalten.
    - Bei der Darstellung auf einer Webseite ist der Quellenvermerk mit der URL "http://www.bkg.bund.de" zu verlinken.
    - © Bundesamt für Kartographie und Geodäsie (Jahr), Datenquellen: https://sg.geodatenzentrum.de/web_public/Datenquellen_POI-Open.pdf
- Deutschlandatlas Erreichbarkeit des öffentlichen Verkehrs (Haltestellen)
  - https://www.mcloud.de/web/guest/suche/-/results/filter/relevance/spatial%3A5%252E295%2C54%252E952%2C14%252E611%2C47%252E100/10/detail/1177532A-E7EF-45B5-9C39-AC2E2886019D
- Mulitmodale Erreichbarkeiten größter deutscher Städte
  - https://www.mcloud.de/web/guest/suche/-/results/filter/relevance/spatial%3A5%252E295%2C54%252E952%2C14%252E611%2C47%252E100/8/detail/28d4072d-f5d4-47a0-9c36-b157d59196fb
- Basisdaten der Hauptverkehrsstraßen zur strategischen Lärmkartierung entsprechend der EU-Umgebungslärmrichtlinie 2002/49/EG - 2017 (Datensatz)
  - https://www.mcloud.de/web/guest/suche/-/results/filter/relevance/spatial%3A5%252E295%2C54%252E952%2C14%252E611%2C47%252E100/8/detail/3239ea0f-52c9-434a-a4d3-e2ae020d2f3f
- Ballungsraumstatistik
  - https://www.mcloud.de/web/guest/suche/-/results/filter/relevance/spatial%3A5%252E295%2C54%252E952%2C14%252E611%2C47%252E100/5/detail/dce2e345-9226-4d43-8422-832117e51aca
- ManMadeObject-DE
  - https://www.mcloud.de/web/guest/suche/-/results/filter/relevance/spatial%3A5%252E295%2C54%252E952%2C14%252E611%2C47%252E100/2/detail/4e22da46-9481-4855-8267-5511f65672b3
- Daten von Pegeln an oberirdischen Gewässern-DE
  - https://www.mcloud.de/web/guest/suche/-/results/filter/relevance/spatial%3A5%252E295%2C54%252E952%2C14%252E611%2C47%252E100/2/detail/cf3ad7b9-8346-4408-addd-b208282c4a1b
- WMS - Bundeswasserstraßen der WSV (BWaStr) - ITZBund
  - https://www.mcloud.de/web/guest/suche/-/results/filter/relevance/spatial%3A5%252E295%2C54%252E952%2C14%252E611%2C47%252E100/0/detail/dfd91e39-f477-40fb-b158-d92c3e99e86f
- Verkehrsnetz der Bundeswasserstraßen (VerkNet BWaStr)
  - https://www.mcloud.de/web/guest/suche/-/results/filter/relevance/spatial%3A5%252E295%2C54%252E952%2C14%252E611%2C47%252E100/0/detail/e56955e5-69ea-40dd-8bcb-664a12faa516
- Landcover classification map of Germany 2019 based on Sentinel-2 data
  - https://www.mcloud.de/web/guest/suche/-/results/filter/relevance/spatial%3A5%252E295%2C54%252E952%2C14%252E611%2C47%252E100/1/detail/36512b46-f3aa-4aa4-8281-7584ec46c813
- Baumkataster Bundeseisenbahnvermögen (BEV)
  - https://www.mcloud.de/web/guest/suche/-/results/filter/relevance/spatial%3A5%252E295%2C54%252E952%2C14%252E611%2C47%252E100/0/detail/691202bd-cb41-47c7-a402-cb1d7fe280d7

Other sources

- https://interaktiv.waz.de/schnee-an-weihnachten/
