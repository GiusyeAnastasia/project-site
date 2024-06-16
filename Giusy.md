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

<table>
  <tr>
    <th>Question</th>
    <th>CHAT GPT</th>
    <th>GEMINI</th>
  </tr>
  <tr>
    <td>Cultural Property: Basilica di San Lorenzo (Firenze)
Author: Michelangelo Buonarroti
Q: which artworks of Michelangelo Buonarroti are located in the Basilica di San Lorenzo in Florence?</td>
   
    <td>Michelangelo Buonarroti contributed several significant artworks to the Basilica di San Lorenzo in Florence. These include:
The Medici Chapels (Cappelle Medicee): Michelangelo designed and partially executed the sculptures and architectural elements for the New Sacristy (Sagrestia Nuova), which houses the tombs of several members of the Medici family. Key works include:
Tomb of Lorenzo de' Medici (Duke of Urbino): Featuring the statues "Dusk" and "Dawn" flanking the central figure of Lorenzo.
Tomb of Giuliano de' Medici (Duke of Nemours): Featuring the statues "Night" and "Day" flanking the central figure of Giuliano.
The Laurentian Library (Biblioteca Laurenziana): While not a traditional artwork, Michelangelo designed the architecture and decorative elements of this library attached to the basilica. It is renowned for its innovative stair design and interior space.
These works reflect Michelangelo's mastery in sculpture and architecture and are key attractions in the Basilica di San Lorenzo, showcasing his deep connection with the Medici family and their patronage./td>
   
    <td>While Michelangelo did have plans for the Basilica di San Lorenzo, none of his final works are actually on the facade or in the main body of the church. Here's what he was involved in:
•	The New Sacristy (Sagrestia Nuova): This is where Michelangelo's most famous contributions reside. He designed the entire space and sculpted the magnificent tombs of Giuliano de' Medici and Lorenzo de' Medici.
•	The Facade: Michelangelo never finished the facade, but he did create several designs that can be seen at the Casa Buonarroti museum in Florence [Michelangelo's Model for the Facade of San Lorenzo].
Hidden Sketches: There are rumors of hidden sketches by Michelangelo in a chamber beneath the Basilica, but these are not accessible to the public.</td>
 
  </tr>
  <tr>
   
    <td>Can you extract exactly what the main topics are based on this description?</td>
   
    <td>Based on the description provided, the main topics are:
The Medici Chapels (Cappelle Medicee)
Tomb of Lorenzo de' Medici (Duke of Urbino)
Statues: "Dusk" and "Dawn"
Tomb of Giuliano de' Medici (Duke of Nemours)
Statues: "Night" and "Day"
The Laurentian Library (Biblioteca Laurenziana)
Architecture and decorative elements
Innovative stair design and interior space.</td>
   
    <td>Based on the description, the main topics regarding Michelangelo's work at the Basilica di San Lorenzo are:
1.	The New Sacristy (Sagrestia Nuova): This is the key area where Michelangelo's completed works are found. He designed the entire space and created the famous tombs.
2.	Unfulfilled Designs: While Michelangelo had a vision for the facade, his designs were never implemented. You can learn more about them at a separate museum.
3.	Unconfirmed Sketches: There's a possibility of hidden sketches by Michelangelo, but they are inaccessible and their existence remains unverified.</td>
 
  </tr>
  <tr>
  
    <td>Could you transform this description into RDF format and use Arco ontology?</td>
 
 <td>@prefix arco: <https://w3id.org/arco/ontology/core/> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix dcterms: <http://purl.org/dc/terms/> .
@prefix ex: <http://example.org/> .
# Basilica di San Lorenzo
ex:Basilica_di_San_Lorenzo rdf:type arco:CulturalProperty ;
    rdfs:label "Basilica di San Lorenzo" ;
    dcterms:creator ex:Michelangelo_Buonarroti .
# New Sacristy (Sagrestia Nuova)
ex:New_Sacristy rdf:type arco:CulturalPropertyPart ;
    rdfs:label "New Sacristy" ;
    dcterms:isPartOf ex:Basilica_di_San_Lorenzo .
# Tomb of Lorenzo de' Medici
ex:Tomb_of_Lorenzo_de_Medici rdf:type arco:CulturalPropertyPart ;
    rdfs:label "Tomb of Lorenzo de' Medici" ;
    dcterms:isPartOf ex:New_Sacristy .
# Statues Dawn (Aurora) and Dusk (Crepuscolo)
ex:Dawn rdf:type arco:CulturalProperty ;
    rdfs:label "Dawn (Aurora)" ;
    dcterms:creator ex:Michelangelo_Buonarroti ;
    dcterms:isPartOf ex:Tomb_of_Lorenzo_de_Medici .
ex:Dusk rdf:type arco:CulturalProperty ;
    rdfs:label "Dusk (Crepuscolo)" ;
    dcterms:creator ex:Michelangelo_Buonarroti ;
    dcterms:isPartOf ex:Tomb_of_Lorenzo_de_Medici .
# Tomb of Giuliano de' Medici
ex:Tomb_of_Giuliano_de_Medici rdf:type arco:CulturalPropertyPart ;
    rdfs:label "Tomb of Giuliano de' Medici" ;
    dcterms:isPartOf ex:New_Sacristy .
# Statues Night (Notte) and Day (Giorno)
ex:Night rdf:type arco:CulturalProperty ;
    rdfs:label "Night (Notte)" ;
    dcterms:creator ex:Michelangelo_Buonarroti ;
    dcterms:isPartOf ex:Tomb_of_Giuliano_de_Medici .
ex:Day rdf:type arco:CulturalProperty ;
    rdfs:label "Day (Giorno)" ;
    dcterms:creator ex:Michelangelo_Buonarroti ;
    dcterms:isPartOf ex:Tomb_of_Giuliano_de_Medici .
# Medici Madonna
ex:Medici_Madonna rdf:type arco:CulturalProperty ;
    rdfs:label "Medici Madonna" ;
    dcterms:creator ex:Michelangelo_Buonarroti ;
    dcterms:isPartOf ex:New_Sacristy .
# Laurentian Library (Biblioteca Medicea Laurenziana)
ex:Laurentian_Library rdf:type arco:CulturalProperty ;
    rdfs:label "Laurentian Library" ;
    dcterms:creator ex:Michelangelo_Buonarroti ;
    dcterms:isPartOf ex:Basilica_di_San_Lorenzo .
# Michelangelo Buonarroti
ex:Michelangelo_Buonarroti rdf:type foaf:Person ;
    foaf:name "Michelangelo Buonarroti".</td>
  
  <td>rdf:RDF
  xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
  xmlns:arco="http://purl.org/arco/core#"
  xmlns:schema="http://schema.org/"
  arco:Place rdf:about="http://example.org/basilica-san-lorenzo"
  arco:name Basilica di San Lorenzo arco:name
  arco:location schema:addressLocality="Firenze" 
  arco:Place
  arco:Person rdf:about="http://example.org/michelangelo"
  arco:name Michelangelo Buonarroti arco:name
  arco:Person
  arco:ArchitecturalFeature rdf:about="http://example.org/new-sacristy"
    arco:name The New Sacristy (Sagrestia Nuova) arco:name
    arco:location arco:isPartOf="http://example.org/basilica-san-lorenzo" 
    arco:hasCreator arco:agent="http://example.org/michelangelo" 
  arco:ArchitecturalFeature
  arco:ManMadeObject rdf:about="http://example.org/medici-tombs"
    arco:name Tombs of Giuliano de' Medici and Lorenzo de' Medici arco:name
    arco:type arco:Tomb 
    arco:creator arco:agent="http://example.org/michelangelo" 
  arco:location arco:isPartOf="http://example.org/new-sacristy" 
  arco:ManMadeObject
  arco:ConceptualObject rdf:about="http://example.org/facade-design"
    arco:name Facade Design for Basilica di San Lorenzo</arco:name
    arco:creator arco:agent="http://example.org/michelangelo" 
    arco:isRealizedBy arco:resource="http://example.org/casa-buonarroti" 
arco:ConceptualObject
arco:Place rdf:about="http://example.org/casa-buonarroti"
  arco:name Casa Buonarroti Museum arco:name
  arco:location schema:addressLocality="Firenze" /
  arco:Place
  arco:ConceptualObject rdf:about="http://example.org/hidden-sketches"
arco:name Hidden Sketches by Michelangelo arco:name
arco:creator arco:agent="http://example.org/michelangelo" 
   arco:location arco:isPartOf="http://example.org/basilica-san-lorenzo" 
   arco:hasVerificationStatus arco:VerificationStatus="Unverified" 
  arco:ConceptualObject
  rdf:RDF</td>
</tr>
</table>

Spiegazione confronto

##CHAT GPT

CONFRONTO

##GEMINI

CONFRONTO

#Check if the entities already exist in the knowledge graph

The LLM created new entities, but what if the these entities already exist in the knowledge graph?

##Question

I wanted to know what cultural entities are involved in the cultural events.

##Purpose

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

##Question

I wanted to know what cultural entities are involved in the cultural events.

##Purpose

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

#Creating new Triples

Considering the absence of data on these artworks in the ArCo database system, we can enrich the ontology with the additional information and make new triples:

##1
https://w3id.org/arco/resource/CulturalEvent/15bc9a7db40a4e86fd2d95b53c533124 cis:involvesCulturalEntity https://w3id.org/arco/resource/HistoricOrArtisticProperty/CappelleMedicee

##2
https://w3id.org/arco/resource/CulturalEvent/15bc9a7db40a4e86fd2d95b53c533124 cis:involvesCulturalEntity https://w3id.org/arco/resource/HistoricOrArtisticProperty/FacciataDiSanLorenzo

#Create a Construct

Next, I decided to utilize different information provided by LLM, specifically focusing on "Basilic a di San Lorenzo. Fisrt I made sure that the Church existed in the ArCo database, then I constructed a query to retrieve data related to "Basilica di San Lorenzo".

##Step 1

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

##Step 2

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
