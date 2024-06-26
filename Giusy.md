---
layout: default
title: [Michelangelo architetto a San Lorenzo: quattro problemi aperti]
description: [Cultutal Event]
---
<span style="font-family: 'Century Gothic'; font-size: 30px; color: black;">Michelangelo architetto a San Lorenzo: quattro problemi aperti</span>

<span style="font-family: 'Century Gothic'; font-size: 20px; color: black;">CulturalEvent</span>

![image about Basilica di San Lorenzo](https://www.guidaturisticaperfirenze.com/wp-content/uploads/2020/11/i-luoghi-medicei-basilica-di-san-lorenzo.jpg)

**Description of the Event**

An Exhibition on the Unresolved Issues of Buonarroti's Work.

The exhibition focuses on four key moments:

1. The identification of an intervention, probably by Giuliano da Sangallo, in relation to Michelangelo's work in the architectural realization of the New Sacristy and the interpretation of its interior space as a unique synthesis of architecture and sculpture;

2. The complex, endless story of the staircase for the vestibule of the Laurentian Library, including the description of a lesser-known intervention by Tribolo;

3. The interpretation of Michelangelo's extraordinary drawings for the mysterious and never-realized triangular-plan "secret library";

4. Finally, the creation of the Tribune of the Relics and the identification of the boundary between Michelangelo's intervention and the decorative elements of the pre-existing 15th-century counter-facade of the basilica.

Centered around Michelangelo's drawings from the Casa Buonarroti, the exhibition also features works from prestigious Italian and international institutions. It utilizes computer support through three-dimensional models and digital elaborations to clarify the issues related to each theme and to highlight the extent of Michelangelo's intervention in one of the world's most famous and visited art spaces.



# SPARQL QUERY

I wanted to begin by retrieving all the information about my event and decided to use the SPARQL DESCRIBE query:

**Purpose of the Query**

The SPARQL DESCRIBE query aims to retrieve a detailed description of a specific resource within a dataset. In this case, the resource is a cultural event identified by the URI "ce:15bc9a7db40a4e86fd2d95b53c533124"

```js
PREFIX ce: <https://w3id.org/arco/resource/CulturalEvent/>
DESCRIBE ce:15bc9a7db40a4e86fd2d95b53c533124
```

The query seeks to discover all the information available about the cultural event with the given identifier.

[Result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=PREFIX+ce%3A+%3Chttps%3A%2F%2Fw3id.org%2Farco%2Fresource%2FCulturalEvent%2F%3E%0D%0ADESCRIBE+ce%3A15bc9a7db40a4e86fd2d95b53c533124&format=text%2Fhtml&timeout=0&signal_void=on)

# Large Language Models

## Comparing CHAT GPT and GEMINI

After gathering all the information, the next steps involve enriching the data and utilizing Large Language Models (LLMs) for further analysis. For this comparison, I will employ two models: CHAT GPT and GEMINI.

### Question 1

*Cultural Property: Basilica di San Lorenzo (Firenze)*

*Author: Michelangelo Buonarroti*

*Q: which artworks of Michelangelo Buonarroti are located in the Basilica di San Lorenzo in Florence?*  

Here I used *Zero-shot Prompting*. This technique involves asking the model to perform a task without providing any examples. It relies on the model's pre-trained knowledge.

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

Here I used *Few-shot prompting*. In this approach, I provided a few examples of the task within the prompt to help the model understand the context and desired output.
Gave him a prompt. 

Give me as a result just a list and nothing more.
Example:

1) "Mona Lisa" by Leonardo da Vinci

2) "Starry Night" by Vincent van Gogh

3) "The Last Supper" by Leonardo da Vinci 

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
        <p> 1. The Medici Chapels (Cappelle Medicee) </p>
        <p> 2. Tomb of Lorenzo de' Medici (Duke of Urbino) </p>
        <p> 3. Tomb of Giuliano de' Medici (Duke of Nemours) </p>
        <p> 4. The Laurentian Library (Biblioteca Laurenziana) </p>

    </td>   
    <td>
      <p> Based on the description, the main topics regarding Michelangelo's work at the Basilica di San Lorenzo are: </p>
<p> 1.The New Sacristy (Sagrestia Nuova)This is where Michelangelo's most famous contributions reside. He designed the entire space and sculpted the magnificent tombs of Giuliano de' Medici and Lorenzo de' Medici.</p>
<p> 2.The FacadeMichelangelo never finished the facade, but he did create several designs that can be seen at the Casa Buonarroti museum in Florence [Michelangelo's Model for the Facade of San Lorenzo].</p>
<p> 3.Hidden SketchesThere are rumors of hidden sketches by Michelangelo in a chamber beneath the Basilica, but these are not accessible to the public.</p>
<p> </p>

*While the response contained extensive information I decided to use Prompt Chaining technique. First, I asked to retrieve the main topics from the description, then I asked it to make a list out of those main and the result was following:*
<p> </p>
<p>Sure, here is a list of the main topics:</p>
  
<p> Main Topics </p>
<p> The New Sacristy (Sagrestia Nuova) </p>
<p> The Facade </p>
<p> Hidden Sketches </p>


    </td> 
  </tr>
</tbody>
</table>

### Question 3
   
   *Could you transform this description into RDF format and use Arco ontology?*

For this part I decided to use another prompting technique, *Chain-of-Thought Prompting*, This technique involves breaking down the reasoning process into a sequence of steps, guiding the model to follow a logical path to arrive at the answer.

Example: "To understand SPARQL, follow these steps: 1) SPARQL is a query language used to retrieve data stored in RDF format. 2) It allows users to write queries using patterns of triples. 3) By using keywords like OPTIONAL, FILTER, and UNION, SPARQL can perform complex searches. 4)Example - as an example I gave the LLMs some working SPARQL queries. 
 
 The results are as follows: 


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
   <p> SELECT DISTINCT ?culturalHeritage ?heritageLabel ?location ?locationLabel ?creator ?creatorLabel</p>
<p> WHERE</p>
<p> {</p>
  <p>  # Basilica di San Lorenzo</p>
   <p>  ?basilica rdf:type a-l:ArchitecturalStructure ;</p>
            <p>   rdfs:label "Basilica di San Lorenzo" .</p>

  <p>   # The Medici Chapels</p>
   <p>  ?mediciChapels rdf:type a-cd:CulturalHeritage ;</p>
                  <p>  rdfs:label "The Medici Chapels (Cappelle Medicee)" ;</p>
                  <p>  a-cd:isPartOf ?basilica ;</p>
                  <p>  a-cd:hasAuthor ?creator .</p>

   <p> # Tomb of Lorenzo de' Medici (Duke of Urbino)</p>
   <p>  ?tombLorenzo rdf:type a-cd:CulturalHeritage ;</p>
                 <p> rdfs:label "Tomb of Lorenzo de' Medici (Duke of Urbino)" ;</p>
                <p>  a-cd:isPartOf ?mediciChapels .</p>

   <p>  # Statues for Tomb of Lorenzo de' Medici</p>
    <p> ?statueDusk rdf:type a-cd:CulturalHeritage ;</p>
               <p>  rdfs:label "Dusk" ;</p>
              <p>   a-cd:isPartOf ?tombLorenzo .</p>
   <p>  ?statueDawn rdf:type a-cd:CulturalHeritage ;</p>
               <p>  rdfs:label "Dawn" ;</p>
               <p>  a-cd:isPartOf ?tombLorenzo .</p>

   <p>  # Tomb of Giuliano de' Medici (Duke of Nemours)</p>
   <p>  ?tombGiuliano rdf:type a-cd:CulturalHeritage ;</p>
               <p> rdfs:label "Tomb of Giuliano de' Medici (Duke of Nemours)" ;</p>
                <p> a-cd:isPartOf ?mediciChapels .</p>

   <p>  # Statues for Tomb of Giuliano de' Medici</p>
   <p>  ?statueNight rdf:type a-cd:CulturalHeritage ;</p>
                <p>  rdfs:label "Night" ;</p>
                <p>  a-cd:isPartOf ?tombGiuliano .</p>
   <p>  ?statueDay rdf:type a-cd:CulturalHeritage ;</p>
              <p>  rdfs:label "Day" ;</p>
              <p>  a-cd:isPartOf ?tombGiuliano .</p>

    <p> # The Laurentian Library</p>
    <p> ?library rdf:type a-l:ArchitecturalStructure ;</p>
            <p>  rdfs:label "The Laurentian Library (Biblioteca Laurenziana)" ;</p>
            <p>  a-cd:isPartOf ?basilica ;</p>
            <p>  a-cd:hasAuthor ?creator .</p>

   <p> # Michelangelo Buonarroti</p>
    <p> ?creator rdf:type a-cd:Person ;</p>
             <p> rdfs:label ?creatorLabel .</p>

    <p> FILTER(REGEX(?creatorLabel, "Buonarroti Michelangelo" , "i")) </p>
<p> } </p>


         </td>
  
  <td>
   <p> rdf:RDF xmlns:arco="http://purl.oclc.org/arco/ rdf:about="http://example.org/basilica-san-lorenzo" </p>
  <p> arco:has_work_of_art </p>
    <p> arco:Work_of_Art rdf:about="http://example.org/sagrestia-nuova" </p>
     <p>  arco:creator rdf:resource="http://example.org/michelangelo"/ </p>
      <p> arco:titleSagrestia Nuova /arco:title </p>
     <p>  arco:type_of_work Space /arco:type_of_work /arco:Work_of_Art </p>
  <p> arco:has_work_of_art </p>
  <p> arco:has_work_of_art </p>
    <p> arco:Work_of_Art rdf:about="http://example.org/giuliano-de-medici-tomb" </p>
      <p> arco:creator rdf:resource="http://example.org/michelangelo"/ </p>
      <p> arco:title Tomb of Giuliano de' Medici arco:title </p>
      <p> arco:type_of_work Tomb /arco:type_of_work </p>
    <p> arco:Work_of_Art </p>
 <p>  arco:has_work_of_art </p>
 <p>  arco:has_work_of_art </p>
   <p>  arco:Work_of_Art rdf:about="http://example.org/lorenzo-de-medici-tomb" </p>
      <p> arco:creator rdf:resource="http://example.org/michelangelo" </p>
      <p> arco:title Tomb of Lorenzo de' Medici arco:title </p>
      <p> arco:type_of_work Tomb arco:type_of_work </p>
   <p>  arco:Work_of_Art </p>
  <p> arco:has_work_of_art </p>
  <p> arco:has_design </p>
    <p> arco:Design rdf:about="http://example.org/facciata-san-lorenzo" </p>
     <p>  arco:creator rdf:resource="http://example.org/michelangelo" </p>
     <p>  arco:title Facade of San Lorenzo arco:title </p>
     <p>  arco:current_location rdf:resource="http://example.org/casa-buonarroti" </p>
      <p> arco:design_state Incomplete arco:design_state </p>
   <p>  arco:Design </p>
 <p>  arco:has_design </p>
  <p> arco:has_rumored_work_of_art </p>
   <p>  arco:Work_of_Art rdf:about="http://example.org/michelangelo-hidden-sketches" </p>
     <p>  arco:creator rdf:resource="http://example.org/michelangelo" </p>
     <p>  arco:title Hidden Sketches arco:title </p>
     <p>  arco:type_of_work Sketch arco:type_of_work </p>
     <p>  arco:accessibility Not publicly accessible arco:accessibility </p>
   <p>  arco:Work_of_Art </p>
 <p>  arco:has_rumored_work_of_art </p>
<p> rdf:RDF </p>

  </td>
</tr>
</tbody>
</table>


## Comparison between the LLMs "CHAT GPT" and "GEMINI"

The information provided by ChatGPT regarding the questions asked is clearer and more comprehensive compared to Gemini. Additionally, the Query created by ChatGPT, despite the use of several Promting Techniques, appear more detailed and easier to implement. Gemini seems to have missed the essence of the questions, and the Query generated by this LL model present many syntax errors.

# Check if the entities already exist in the knowledge graph

The LLM created new entities, but what if the these entities already exist in the knowledge graph?

## Question

I wanted to know what cultural entities are involved in the cultural events.

## Purpose

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

## Question

I wanted to know what cultural entities are involved in the cultural events.

## Purpose

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

# Creating new Triples

Considering the absence of data on these artworks in the ArCo database system, we can enrich the ontology with the additional information and make new triples:

## 1
https://w3id.org/arco/resource/CulturalEvent/15bc9a7db40a4e86fd2d95b53c533124 cis:involvesCulturalEntity https://w3id.org/arco/resource/HistoricOrArtisticProperty/CappelleMedicee

## 2
https://w3id.org/arco/resource/CulturalEvent/15bc9a7db40a4e86fd2d95b53c533124 cis:involvesCulturalEntity https://w3id.org/arco/resource/HistoricOrArtisticProperty/FacciataDiSanLorenzo

# Create a Construct

Next, I decided to utilize different information provided by LLM, specifically focusing on "Basilic a di San Lorenzo. Fisrt I made sure that the Church existed in the ArCo database, then I constructed a query to retrieve data related to "Basilica di San Lorenzo".

## Step 1

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

## Step 2

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
