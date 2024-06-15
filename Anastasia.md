---
title: [Exposition de l'art italien de Cimabue à Tiepolo]
description: [Cultutal Event]
---
**Research in SPARQL**

In order to ask the question "What are the cultural events associated with the artist "Michelangelo Buonarroti" in Rome?" I used the following query:
```js
PREFIX cis: <http://dati.beniculturali.it/cis/>
PREFIX clv: <https://w3id.org/italia/onto/CLV/>
PREFIX a-cd: <https://w3id.org/arco/ontology/context-description/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
SELECT DISTINCT ?culturalevent ?eventlabel ?author ?authorlabel ?place
WHERE{
?culturalevent a cis:CulturalEvent ;
 rdfs:label ?eventlabel .
?culturalevent cis:involvesCulturalEntity ?culturalEntity .
?culturalEntity a-cd:hasAuthor ?author .
?author rdfs:label ?authorlabel
FILTER(REGEX(?authorlabel, "Buonarroti Michelangelo" , "i"))
?place a cis:GeographicalFeature ;
rdfs:label "Roma"}
```
[result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=PREFIX+cis%3A+%3Chttp%3A%2F%2Fdati.beniculturali.it%2Fcis%2F%3E%0D%0APREFIX+clv%3A+%3Chttps%3A%2F%2Fw3id.org%2Fitalia%2Fonto%2FCLV%2F%3E%0D%0APREFIX+a-cd%3A+%3Chttps%3A%2F%2Fw3id.org%2Farco%2Fontology%2Fcontext-description%2F%3E%0D%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0D%0APREFIX+rdf%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0D%0ASELECT+DISTINCT+%3Fculturalevent+%3Feventlabel+%3Fauthor+%3Fauthorlabel+%3Fplace%0D%0AWHERE%0D%0A%7B%0D%0A%3Fculturalevent+a+cis%3ACulturalEvent+%3B%0D%0A+rdfs%3Alabel+%3Feventlabel+.%0D%0A%3Fculturalevent+cis%3AinvolvesCulturalEntity+%3FculturalEntity+.%0D%0A%3FculturalEntity+a-cd%3AhasAuthor+%3Fauthor+.%0D%0A%3Fauthor+rdfs%3Alabel+%3Fauthorlabel%0D%0AFILTER%28REGEX%28%3Fauthorlabel%2C+%22Buonarroti+Michelangelo%22+%2C+%22i%22%29%29%0D%0A%3Fplace+a+cis%3AGeographicalFeature+%3B%0D%0Ardfs%3Alabel+%22Roma%22%7D+%0D%0A&format=text%2Fhtml&timeout=0&signal_void=on)
I chose to research [this event](https://dati.beniculturali.it/lodview-arco/resource/CulturalEvent/49e9140e7d94d2049c1eeb6582c51e01.html)
```js
PREFIX ce: <https://w3id.org/arco/resource/CulturalEvent/>
DESCRIBE ce:49e9140e7d94d2049c1eeb6582c51e01
```
[result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=PREFIX+ce%3A+%3Chttps%3A%2F%2Fw3id.org%2Farco%2Fresource%2FCulturalEvent%2F%3E%0D%0ADESCRIBE+ce%3A49e9140e7d94d2049c1eeb6582c51e01%0D%0A&format=text%2Fhtml&timeout=0&signal_void=on)

```js
CONSTRUCT { 
?culturalevent a cis:CulturalEvent ;
rdfs:label "Exposition de l'art italien de Cimabue à Tiepolo"}
WHERE  { 
?culturalevent a cis:CulturalEvent ;
rdfs:label "Exposition de l'art italien de Cimabue à Tiepolo"}
```
[result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=PREFIX+cis%3A+%3Chttp%3A%2F%2Fdati.beniculturali.it%2Fcis%2F%3E%0D%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E+%0D%0A%0D%0ACONSTRUCT+%7B+%0D%0A%3Fculturalevent+a+cis%3ACulturalEvent+%3B%0D%0Ardfs%3Alabel+%22Exposition+de+l%27art+italien+de+Cimabue+à+Tiepolo%22%7D%0D%0AWHERE++%7B+%0D%0A%3Fculturalevent+a+cis%3ACulturalEvent+%3B%0D%0Ardfs%3Alabel+%22Exposition+de+l%27art+italien+de+Cimabue+à+Tiepolo%22%7D%0D%0A%0D%0A&format=text%2Fhtml&timeout=0&signal_void=on)

**Research using Large Language Models**

|   Question        |   ChatGPT        |   Gemini |
|   :-------------   |   :------------------   |   :------   |
|   Cultural event: Exposition de l'art italien de Cimabue à Tiepolo 
Artist: Michelangelo Buonarotti 
Q: What does this cultural event represent?   |   ,,,   |   mmk   |

Next, I check if the artworks found by the AI are in ArCo.

_artwork 1_
```js
PREFIX cis: <http://dati.beniculturali.it/cis/>
PREFIX arco: <https://w3id.org/arco/resource/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?culturalEntity ?CulturalEntityLabel
WHERE {
?culturalevent a cis:CulturalEvent ;
                          cis:involvesCulturalEntity ?culturalEntity .
?culturalEntity a-cd:hasAuthor ?author .
?author rdfs:label ?authorlabel
FILTER(REGEX(?authorlabel, "Buonarroti Michelangelo" , "i"))
?culturalEntity rdfs:label ?CulturalEntityLabel
FILTER(REGEX(?CulturalEntityLabel , "David","i"))}
```
[result](https://dati.beniculturali.it/lodview-arco/resource/HistoricOrArtisticProperty/0900286607.html)

_artwork 2_
```js
PREFIX cis: <http://dati.beniculturali.it/cis/>
PREFIX arco: <https://w3id.org/arco/resource/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?culturalEntity ?CulturalEntityLabel
WHERE {
?culturalevent a cis:CulturalEvent ;
                          cis:involvesCulturalEntity ?culturalEntity .
?culturalEntity a-cd:hasAuthor ?author .
?author rdfs:label ?authorlabel
FILTER(REGEX(?authorlabel, "Buonarroti Michelangelo" , "i"))
?culturalEntity rdfs:label ?CulturalEntityLabel
FILTER(REGEX(?CulturalEntityLabel , " Pietà ","i"))}
```
This artwork wasn't found in ArCo

**Triple connecting the entity to an existing subject**

_artwork 1_

https://dati.beniculturali.it/lodview-arco/resource/CulturalEvent/49e9140e7d94d2049c1eeb6582c51e01.html cis:involvesCulturalEntity https://dati.beniculturali.it/lodview-arco/resource/HistoricOrArtisticProperty/0900286607.html

_artwork 2_

https://dati.beniculturali.it/lodview-arco/resource/CulturalEvent/49e9140e7d94d2049c1eeb6582c51e01.html cis:involvesCulturalEntity https://dati.beniculturali.it/lodview-arco/resource/HistoricOrArtisticProperty/Pietà.html

