---
layout: default
title: [Michelangelo architetto a san Lorenzo: quattro problemi aperti]
description: [Cultutal Event]
---

# DESCRIZIONE CON SPARQL
Spiegazione

```js
PREFIX ce: <https://w3id.org/arco/resource/CulturalEvent/>
DESCRIBE ce:15bc9a7db40a4e86fd2d95b53c533124 (b9120f9e4fde2d9803c13dd4f8732093)
}
```

[Result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=PREFIX+ce%3A+%3Chttps%3A%2F%2Fw3id.org%2Farco%2Fresource%2FCulturalEvent%2F%3E%0D%0ADESCRIBE+ce%3A15bc9a7db40a4e86fd2d95b53c533124&format=text%2Fhtml&timeout=0&signal_void=on)


# Large Language Models
## Comparing CHAT GPT and GEMINI
spiegazione


Spiegazione confronto

### CHAT GPT

CONFRONTO

### GEMINI

CONFRONTO

## Check if the entities already exist in the knowledge graph

The LLM created new entities, but what if the these entities already exist in the knowledge graph?

### Question

I wanted to know what cultural entities are involved in the cultural events.

### Purpose

This query aims to identify the cultural entities involved in the cultural event within the ArCo knowledge graph. Specifically I wanted to find out if there's a piece "Cappelle Medicee" in the database.The FILTER clause is utilized to narrow down the results based on a specific condition, searching for entities whose label matches the string "Cappelle Medicee".

```js
PREFIX cis: <http://dati.beniculturali.it/cis/>
PREFIX arco: <https://w3id.org/arco/resource/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?culturalEntity ?CulturalEntityLabel
WHERE {
?culturalevent a cis:CulturalEvent ;
                          cis:involvesCulturalEntity ?culturalEntity .
?culturalEntity rdfs:label ?CulturalEntityLabel
FILTER(REGEX(?CulturalEntityLabel , "Cappelle Medicee","i"))
}
```
[Result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=%0D%0APREFIX+cis%3A+%3Chttp%3A%2F%2Fdati.beniculturali.it%2Fcis%2F%3E%0D%0APREFIX+arco%3A+%3Chttps%3A%2F%2Fw3id.org%2Farco%2Fresource%2F%3E%0D%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0D%0A%0D%0ASELECT+DISTINCT+%3FculturalEntity+%3FCulturalEntityLabel%0D%0AWHERE+%7B%0D%0A%3Fculturalevent+a+cis%3ACulturalEvent+%3B%0D%0A++++++++++++++++++++++++++cis%3AinvolvesCulturalEntity+%3FculturalEntity+.%0D%0A%3FculturalEntity+rdfs%3Alabel+%3FCulturalEntityLabel%0D%0AFILTER%28REGEX%28%3FCulturalEntityLabel+%2C+%22Cappelle+Medicee%22%2C%22i%22%29%29%7D%0D%0A&format=text%2Fhtml&timeout=0&signal_void=on)

### Question

I wanted to know what cultural entities are involved in the cultural events.

### Purpose

This query aims to identify the cultural entities involved in the cultural event within the ArCo knowledge graph. Specifically I wanted to find out if there's a piece "Facciata di San Lorenzo" in the database.The FILTER clause is utilized to narrow down the results based on a specific condition, searching for entities whose label matches the string "Facciata di San Lorenzo".

```js
PREFIX cis: <http://dati.beniculturali.it/cis/>
PREFIX arco: <https://w3id.org/arco/resource/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?culturalEntity ?CulturalEntityLabel
WHERE {
?culturalevent a cis:CulturalEvent ;
                          cis:involvesCulturalEntity ?culturalEntity .
?culturalEntity rdfs:label ?CulturalEntityLabel
FILTER(REGEX(?CulturalEntityLabel , "Facciata di San Lorenzo","i"))
}
```
[Result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=%0D%0APREFIX+cis%3A+%3Chttp%3A%2F%2Fdati.beniculturali.it%2Fcis%2F%3E%0D%0APREFIX+arco%3A+%3Chttps%3A%2F%2Fw3id.org%2Farco%2Fresource%2F%3E%0D%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0D%0A%0D%0ASELECT+DISTINCT+%3FculturalEntity+%3FCulturalEntityLabel%0D%0AWHERE+%7B%0D%0A%3Fculturalevent+a+cis%3ACulturalEvent+%3B%0D%0A++++++++++++++++++++++++++cis%3AinvolvesCulturalEntity+%3FculturalEntity+.%0D%0A%3FculturalEntity+rdfs%3Alabel+%3FCulturalEntityLabel%0D%0AFILTER%28REGEX%28%3FCulturalEntityLabel+%2C+%22Facciata+di+San+Lorenzo%22%2C%22i%22%29%29%7D%0D%0A&format=text%2Fhtml&timeout=0&signal_void=on)

## Creating new Triples

Considering the absence of data on these artworks in the ArCo database system, we can enrich the ontology with the additional information and make new triples:

### 1
https://w3id.org/arco/resource/CulturalEvent/15bc9a7db40a4e86fd2d95b53c533124 cis:involvesCulturalEntity https://w3id.org/arco/resource/HistoricOrArtisticProperty/CappelleMedicee

### 2
https://w3id.org/arco/resource/CulturalEvent/15bc9a7db40a4e86fd2d95b53c533124 cis:involvesCulturalEntity https://w3id.org/arco/resource/HistoricOrArtisticProperty/FacciataDiSanLorenzo

## Create a Construct

Next, I decided to utilize different information provided by LLM, specifically focusing on "Basilic a di San Lorenzo. Fisrt I made sure that the Church existed in the ArCo database, then I constructed a query to retrieve data related to "Basilica di San Lorenzo".

### Step 1

```js
PREFIX cis: <http://dati.beniculturali.it/cis/>
PREFIX arco: <https://w3id.org/arco/resource/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT ?culturalProperty ?culturalPropertyLabel
WHERE{
  ?culturalProperty a cis:CulturalInstituteOrSite;  
                                rdfs:label ?culturalPropertyLabel  
FILTER(REGEX(?culturalPropertyLabel, "Basilica di San Lorenzo","i"))
}
```
[Result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=PREFIX+cis%3A+%3Chttp%3A%2F%2Fdati.beniculturali.it%2Fcis%2F%3E%0D%0APREFIX+arco%3A+%3Chttps%3A%2F%2Fw3id.org%2Farco%2Fresource%2F%3E%0D%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0D%0A%0D%0ASELECT+%3FculturalProperty+%3FculturalPropertyLabel%0D%0AWHERE%7B%0D%0A++%3FculturalProperty+a+cis%3ACulturalInstituteOrSite%3B++%0D%0A++++++++++++++++++++++++++++++++rdfs%3Alabel+%3FculturalPropertyLabel++%0D%0AFILTER%28REGEX%28%3FculturalPropertyLabel%2C+%22Basilica+di+San+Lorenzo%22%2C%22i%22%29%29%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&signal_void=on)

Once it has been establish the presence of the subject in the ArCo database, I can proceed to the creation of the Construct.

### Step 2

```js
PREFIX cis: <http://dati.beniculturali.it/cis/>
PREFIX arco: <https://w3id.org/arco/resource/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

CONSTRUCT{

?culturalEntity a cis:CulturalInstituteOrSite;
                        rdfs:label "Basilica di San Lorenzo"@it}
WHERE {
?culturalEntity a cis:CulturalInstituteOrSite;
                        rdfs:label "Basilica di San Lorenzo"@it}
```
[Result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=PREFIX+cis%3A+%3Chttp%3A%2F%2Fdati.beniculturali.it%2Fcis%2F%3E%0D%0APREFIX+arco%3A+%3Chttps%3A%2F%2Fw3id.org%2Farco%2Fresource%2F%3E%0D%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0D%0A%0D%0ACONSTRUCT%7B%0D%0A%0D%0A%3FculturalEntity+a+cis%3ACulturalInstituteOrSite%3B%0D%0A++++++++++++++++++++++++rdfs%3Alabel+%22Basilica+di+San+Lorenzo%22%40it%7D%0D%0AWHERE+%7B%0D%0A%3FculturalEntity+a+cis%3ACulturalInstituteOrSite%3B%0D%0A++++++++++++++++++++++++rdfs%3Alabel+%22Basilica+di+San+Lorenzo%22%40it%7D%0D%0A&format=text%2Fhtml&timeout=0&signal_void=on)
[back](./)
