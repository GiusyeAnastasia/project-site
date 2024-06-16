---
layout: default
title: [Michelangelo architetto a san Lorenzo: quattro problemi aperti]
description: [Cultutal Event]
---
<span style="font-family: 'Lucida Sans'; font-size: 40px; color: blue;">Michelangelo architetto a san Lorenzo: quattro problemi aperti</span>
<span style="font-family: 'Lucida Sans'; font-size: 25px; color: blue;">CulturalEvent</span>
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
After gathering all the information, the next steps involve enriching the data and utilizing Large Language Models (LLMs) for further analysis. For this comparison, I will employ two models: CHAT GPT and GEMINI.

### Question 1
*<p>Cultural Property: Basilica di San Lorenzo (Firenze)</p>*
*<p>Author: Michelangelo Buonarroti</p>*
*<p>Q: which artworks of Michelangelo Buonarroti are located in the Basilica di San Lorenzo in Florence?</p>*    

<table style="text-align: center;">
  <thead>
    <tr>
      <th>CHAT GPT</th>
      <th>GEMINI</th>
  </tr>
  </thead>
  <tbody>
   <tr>
        <td> <p>Michelangelo Buonarroti contributed several significant artworks to the Basilica di San Lorenzo in Florence. These include:</p>
<p>The Medici Chapels (Cappelle Medicee): Michelangelo designed and partially executed the sculptures and architectural elements for the New Sacristy (Sagrestia Nuova), which houses the tombs of several members of the Medici family.</p>
<p>Key works include:</p>
<p>Tomb of Lorenzo de' Medici (Duke of Urbino): Featuring the statues "Dusk" and "Dawn" flanking the central figure of Lorenzo.</p>
<p>Tomb of Giuliano de' Medici (Duke of Nemours): Featuring the statues "Night" and "Day" flanking the central figure of Giuliano.</p>
<p>The Laurentian Library (Biblioteca Laurenziana): While not a traditional artwork, Michelangelo designed the architecture and decorative elements of this library attached to the basilica. It is renowned for its innovative stair design and interior space.</p>
<p>These works reflect Michelangelo's mastery in sculpture and architecture and are key attractions in the Basilica di San Lorenzo, showcasing his deep connection with the Medici family and their patronage.</p>
        </td>
   
    <td>
    <p> While Michelangelo did have plans for the Basilica di San Lorenzo, none of his final works are actually on the facade or in the main body of the church. Here's what he was involved in:</p>
    <p> •	The New Sacristy (Sagrestia Nuova): This is where Michelangelo's most famous contributions reside. He designed the entire space and sculpted the magnificent tombs of Giuliano de' Medici and Lorenzo de' Medici.</p>
    <p> •	The Facade: Michelangelo never finished the facade, but he did create several designs that can be seen at the Casa Buonarroti museum in Florence [Michelangelo's Model for the Facade of San Lorenzo]. </p>
    <p> • Hidden Sketches: There are rumors of hidden sketches by Michelangelo in a chamber beneath the Basilica, but these are not accessible to the public.</p>
    </td> 
  </tr>
</tbody>
</table>

### Question 2

*Can you extract exactly what the main topics are based on this description?*

<table style="text-align: center;">
  <thead>
    <tr>
      <th>CHAT GPT</th>
      <th>GEMINI</th>
  </tr>
  </thead>
  <tbody>
   <tr>
   
    <td>
        <p> Based on the description provided, the main topics are: </p>
        <p> The Medici Chapels (Cappelle Medicee)</p>
        <p> Tomb of Lorenzo de' Medici (Duke of Urbino)</p>
        <p> Statues: "Dusk" and "Dawn"</p>
        <p> Tomb of Giuliano de' Medici (Duke of Nemours</p>
        <p> Statues: "Night" and "Day"</p>
        <p> The Laurentian Library (Biblioteca Laurenziana)</p>
        <p> Architecture and decorative elements</p>
        <p> Innovative stair design and interior space.</p>
    </td>   
    <td>
        <p> Based on the description, the main topics regarding Michelangelo's work at the Basilica di San Lorenzo are: </p>
        <p> 1.	The New Sacristy (Sagrestia Nuova): This is the key area where Michelangelo's completed works are found. He designed the entire space and created the famous tombs. </p>
        <p> 2.	Unfulfilled Designs: While Michelangelo had a vision for the facade, his designs were never implemented. You can learn more about them at a separate museum. </p>
        <p> 3.	Unconfirmed Sketches: There's a possibility of hidden sketches by Michelangelo, but they are inaccessible and their existence remains unverified.</p>
    </td> 
  </tr>
</tbody>
</table>

### Question 3
   *Could you transform this description into RDF format and use Arco ontology?*

 <table style="text-align: center;">
  <thead>
    <tr>
      <th>CHAT GPT</th>
      <th>GEMINI</th>
  </tr>
  </thead>
  <tbody>
  <tr> 
    <td>
      <p>@prefix arco: <https://w3id.org/arco/ontology/core/> .</p>
      <p>@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .</p>
      <p>@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .</p>
      <p>@prefix foaf: <http://xmlns.com/foaf/0.1/> .</p>
      <p>@prefix dcterms: <http://purl.org/dc/terms/> .</p>
      <p>@prefix ex: <http://example.org/> .</p>
      <p># Basilica di San Lorenzo</p>
      <p>ex:Basilica_di_San_Lorenzo rdf:type arco:CulturalProperty ;</p>
          <p>rdfs:label "Basilica di San Lorenzo" ;</p>
          <p>dcterms:creator ex:Michelangelo_Buonarroti .</p>
      <p># New Sacristy (Sagrestia Nuova)</p>
          <p>ex:New_Sacristy rdf:type arco:CulturalPropertyPart ;</p>
              <p>rdfs:label "New Sacristy" ;</p>
              <p>dcterms:isPartOf ex:Basilica_di_San_Lorenzo .</p>
      <p># Tomb of Lorenzo de' Medici</p>
            <p>ex:Tomb_of_Lorenzo_de_Medici rdf:type arco:CulturalPropertyPart ;</p>
            <p>rdfs:label "Tomb of Lorenzo de' Medici" ;</p>
            <p>dcterms:isPartOf ex:New_Sacristy .</p>
      <p># Statues Dawn (Aurora) and Dusk (Crepuscolo)</p>
           <p>ex:Dawn rdf:type arco:CulturalProperty ;</p>
           <p>rdfs:label "Dawn (Aurora)" ;</p>
             <p>dcterms:creator ex:Michelangelo_Buonarroti ;</p>
              <p>dcterms:isPartOf ex:Tomb_of_Lorenzo_de_Medici .</p>
      <p>ex:Dusk rdf:type arco:CulturalProperty ;</p>
            <p>rdfs:label "Dusk (Crepuscolo)" ;</p>
            <p>dcterms:creator ex:Michelangelo_Buonarroti ;</p>
            <p>dcterms:isPartOf ex:Tomb_of_Lorenzo_de_Medici .</p>
      <p># Tomb of Giuliano de' Medici</p>
            <p>ex:Tomb_of_Giuliano_de_Medici rdf:type arco:CulturalPropertyPart ;</p>
            <p>rdfs:label "Tomb of Giuliano de' Medici" ;</p>
               <p>dcterms:isPartOf ex:New_Sacristy .</p>
      <p># Statues Night (Notte) and Day (Giorno)</p>
             <p>ex:Night rdf:type arco:CulturalProperty ;</p>
            <p>rdfs:label "Night (Notte)" ;</p>
                 <p>dcterms:creator ex:Michelangelo_Buonarroti ;</p>
                  <p>dcterms:isPartOf ex:Tomb_of_Giuliano_de_Medici .</p>
      <p>ex:Day rdf:type arco:CulturalProperty ;</p>
            <p>rdfs:label "Day (Giorno)" ;</p>
            <p>dcterms:creator ex:Michelangelo_Buonarroti ;</p>
            <p>dcterms:isPartOf ex:Tomb_of_Giuliano_de_Medici .</p>
      <p># Medici Madonna</p>
           <p>ex:Medici_Madonna rdf:type arco:CulturalProperty ;</p>
             <p>rdfs:label "Medici Madonna" ;</p>
             <p>dcterms:creator ex:Michelangelo_Buonarroti ;</p>
            <p>dcterms:isPartOf ex:New_Sacristy .</p>
      <p># Laurentian Library (Biblioteca Medicea Laurenziana)</p>
           <p>ex:Laurentian_Library rdf:type arco:CulturalProperty ;</p>
                 <p>rdfs:label "Laurentian Library" ;</p>
                 <p>dcterms:creator ex:Michelangelo_Buonarroti ;</p>
                 <p>dcterms:isPartOf ex:Basilica_di_San_Lorenzo .</p>
      <p># Michelangelo Buonarroti</p>
            <p>ex:Michelangelo_Buonarroti rdf:type foaf:Person ;</p>
            <p>foaf:name "Michelangelo Buonarroti".</p>
         </td>
  
  <td>
    <p> rdf:RDF</p>
   <p>xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"</p>
   <p>xmlns:arco="http://purl.org/arco/core#"</p>
   <p>xmlns:schema="http://schema.org/"</p>
   <p>arco:Place rdf:about="http://example.org/basilica-san-lorenzo"</p>
   <p>arco:name Basilica di San Lorenzo arco:name</p>
   <p>arco:location schema:addressLocality="Firenze"</p>
   <p>arco:Place</p>
   <p>arco:Person rdf:about="http://example.org/michelangelo"</p>
   <p>arco:name Michelangelo Buonarroti arco:name</p>
   <p>arco:Person</p>
   <p>arco:ArchitecturalFeature rdf:about="http://example.org/new-sacristy"</p>
     <p>arco:name The New Sacristy (Sagrestia Nuova) arco:name</p>
     <p>arco:location arco:isPartOf="http://example.org/basilica-san-lorenzo"</p> 
     <p>arco:hasCreator arco:agent="http://example.org/michelangelo"</p>
   <p>arco:ArchitecturalFeature</p>
   <p>arco:ManMadeObject rdf:about="http://example.org/medici-tombs"</p>
     <p>arco:name Tombs of Giuliano de' Medici and Lorenzo de' Medici arco:name</p>
     <p>arco:type arco:Tomb </p>
     <p>arco:creator arco:agent="http://example.org/michelangelo" </p>
   <p>arco:location arco:isPartOf="http://example.org/new-sacristy" </p>
   <p>arco:ManMadeObject</p>
   <p>arco:ConceptualObject rdf:about="http://example.org/facade-design"</p>
     <p>arco:name Facade Design for Basilica di San Lorenzo</arco:name</p>
     <p>arco:creator arco:agent="http://example.org/michelangelo" </p>
     <p>arco:isRealizedBy arco:resource="http://example.org/casa-buonarroti"</p> 
 <p>arco:ConceptualObject</p>
 <p>arco:Place rdf:about="http://example.org/casa-buonarroti"</p>
   <p>arco:name Casa Buonarroti Museum arco:name</p>
   <p>arco:location schema:addressLocality="Firenze" /</p>
   <p>arco:Place</p>
   <p>arco:ConceptualObject rdf:about="http://example.org/hidden-sketches"</p>
 <p>arco:name Hidden Sketches by Michelangelo arco:name</p>
 <p>arco:creator arco:agent="http://example.org/michelangelo" </p>
    <p>arco:location arco:isPartOf="http://example.org/basilica-san-lorenzo" </p>
    <p>arco:hasVerificationStatus arco:VerificationStatus="Unverified" </p>
   <p>arco:ConceptualObject</p>
  <p>rdf:RDF</p>
  </td>
</tr>
</tbody>
</table>
















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
