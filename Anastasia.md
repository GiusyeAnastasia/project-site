---
layout: default
title: [Esposizione d'arte italiana da Cimabue a Tiepolo]
description: [Cultutal Event]
---

# Esposizione d'arte italiana da Cimabue a Tiepolo​
# Cultutal Event
## Research in SPARQL

### Query 1
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

### Query 2
I produced an RDF graph that contains all the cultural properties, authoroed by Michelangelo Buonarroti which are involved in events located in Rome using the code below.

```js
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX clv: <https://w3id.org/italia/onto/CLV/>
PREFIX cis: <http://dati.beniculturali.it/cis/>
PREFIX a-cd: <https://w3id.org/arco/ontology/context-description/>
PREFIX l0: <https://w3id.org/italia/onto/l0/>
CONSTRUCT {
?place a cis:GeographicalFeature ; l0:name "Roma" .
?event a cis:CulturalEvent ; clv:hasSpatialCoverage ?place ; l0:name ?eventName ;
cis:involvesCulturalEntity ?culturalProperty .
?culturalProperty a-cd:hasAuthor ?author ; l0:name ?title .
?author l0:name ?authorName
}
WHERE {
?place a cis:GeographicalFeature ; rdfs:label "Roma" .
?event a cis:CulturalEvent ; clv:hasSpatialCoverage ?place ; rdfs:label ?eventName ;
cis:involvesCulturalEntity ?culturalProperty .
?culturalProperty a-cd:hasAuthor ?author ; rdfs:label ?title .
?author rdfs:label ?authorName
FILTER(REGEX(?authorName, "Buonarroti Michelangelo", "i"))
}
```
[result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=PREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0D%0APREFIX+clv%3A+%3Chttps%3A%2F%2Fw3id.org%2Fitalia%2Fonto%2FCLV%2F%3E%0D%0APREFIX+cis%3A+%3Chttp%3A%2F%2Fdati.beniculturali.it%2Fcis%2F%3E%0D%0APREFIX+a-cd%3A+%3Chttps%3A%2F%2Fw3id.org%2Farco%2Fontology%2Fcontext-description%2F%3E%0D%0APREFIX+l0%3A+%3Chttps%3A%2F%2Fw3id.org%2Fitalia%2Fonto%2Fl0%2F%3E%0D%0ACONSTRUCT+%7B%0D%0A%3Fplace+a+cis%3AGeographicalFeature+%3B+l0%3Aname+%22Roma%22+.%0D%0A%3Fevent+a+cis%3ACulturalEvent+%3B+clv%3AhasSpatialCoverage+%3Fplace+%3B+l0%3Aname+%3FeventName+%3B%0D%0Acis%3AinvolvesCulturalEntity+%3FculturalProperty+.%0D%0A%3FculturalProperty+a-cd%3AhasAuthor+%3Fauthor+%3B+l0%3Aname+%3Ftitle+.%0D%0A%3Fauthor+l0%3Aname+%3FauthorName%0D%0A%7D%0D%0AWHERE+%7B%0D%0A%3Fplace+a+cis%3AGeographicalFeature+%3B+rdfs%3Alabel+%22Roma%22+.%0D%0A%3Fevent+a+cis%3ACulturalEvent+%3B+clv%3AhasSpatialCoverage+%3Fplace+%3B+rdfs%3Alabel+%3FeventName+%3B%0D%0Acis%3AinvolvesCulturalEntity+%3FculturalProperty+.%0D%0A%3FculturalProperty+a-cd%3AhasAuthor+%3Fauthor+%3B+rdfs%3Alabel+%3Ftitle+.%0D%0A%3Fauthor+rdfs%3Alabel+%3FauthorName%0D%0AFILTER%28REGEX%28%3FauthorName%2C+%22Buonarroti+Michelangelo%22%2C+%22i%22%29%29%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&signal_void=on)

**I chose to research [this event](https://dati.beniculturali.it/lodview-arco/resource/CulturalEvent/49e9140e7d94d2049c1eeb6582c51e01.html)**
```js
PREFIX ce: <https://w3id.org/arco/resource/CulturalEvent/>
DESCRIBE ce:49e9140e7d94d2049c1eeb6582c51e01
```
[result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=PREFIX+ce%3A+%3Chttps%3A%2F%2Fw3id.org%2Farco%2Fresource%2FCulturalEvent%2F%3E%0D%0ADESCRIBE+ce%3A49e9140e7d94d2049c1eeb6582c51e01%0D%0A&format=text%2Fhtml&timeout=0&signal_void=on)


## Research using Large Language Models

After the research in SPARQL, I used Large Language Models (LLMs) in order to get further information on the event. CHAT GPT and GEMINI seem to be the most reliable LLMs. Below are the questions I asked and the answers from the two LLMs.​

### Question 1

*Cultural event: Exposition de l'art italien de Cimabue à Tiepolo *
*Artist: Michelangelo Buonarotti *
*Q: What does this cultural event represent?*


<table style="text-align: center;">
  <thead>
    <tr>
      <th>CHAT GPT</th>
      <th>GEMINI</th>
  </tr>
  </thead>
  <tbody>
   <tr>
        <td> <p>This cultural event, “Exposition de l’art italien de Cimabue à Tiepolo,” represents a comprehensive exhibition of Italian art spanning a significant period from the 13th to the 18th century.</p>
<p>Here’s a breakdown of the elements:</p>
<p>•	Cimabue to Tiepolo: This highlights the chronological scope of the exhibition, showcasing art from the late medieval period (Cimabue) to the Rococo era (Tiepolo).</p>
<p>•	Michelangelo Buonarotti: While the event is not specifically focused on Michelangelo, his inclusion in the list of artists suggests a possible focus on the High Renaissance, a pivotal period in Italian art history.</p>
<p>•	Exposition de l’art italien: This indicates a broad exploration of Italian art, showcasing its diversity and evolution through different styles, techniques, and artistic movements.</p>
<p>The exhibition offers a unique opportunity to:</p>
<p>•	Explore the rich history of Italian art: From the early beginnings of Italian painting to its peak in the Renaissance and its later development through Baroque and Rococo.</p>
        <p>•	Appreciate the artistic genius of Italian masters: Seeing works by renowned artists like Cimabue, Michelangelo, and Tiepolo within a single exhibition allows for a deeper understanding of their individual styles and contributions to art history.</p>
         <p>•	Witness the cultural and societal influences: The exhibition provides insights into the artistic and cultural trends that shaped Italy during those centuries.</p>
         <p>Overall, this cultural event is a significant and enriching experience for anyone interested in Italian art and its historical evolution.</p>
        </td>
 
    <td>
    <p> The cultural event, "Exposition de l'art italien de Cimabue à Tiepolo," while not solely focused on Michelangelo, represents a journey through a significant period in Italian art history. Here's a breakdown:</p>
    <p> •	Cimabue and Tiepolo: These are two important Italian artists. Cimabue (1240-1302) is considered a forerunner of the Renaissance, while Giambattista Tiepolo (1696-1770) is a prominent figure in the late Baroque and Rococo movements.</p>
    <p> •	Scope of the Exhibition: By showcasing works from Cimabue to Tiepolo, the exhibition aimed to highlight the evolution of Italian art from the late medieval period through the Renaissance and Baroque eras. Michelangelo Buonarotti (1475-1564) falls right in the middle of this timeline, during the High Renaissance. </p>
    <p> •	Therefore, the exhibition wasn't solely about Michelangelo, but rather used his work as part of a broader narrative about the development of Italian artistic styles and techniques over several centuries.</p>
<p>•	While Michelangelo wouldn't have been the sole focus, his inclusion in the exhibition would have been significant because he is considered one of the greatest artists of the Italian Renaissance, known for his mastery of painting, sculpture, and architecture.</p> </td> 
    
  </tr>
  
</tbody>

</table>
  
### Question 2

*What are the most significant artworks presented?*


<table style="text-align: center;">
  <thead>
    <tr>
      <th>CHAT GPT</th>
      <th>GEMINI</th>
  </tr>
  </thead>
  <tbody>
   <tr>
        <td> <p>You’re right to ask! It’s impossible to say definitively which artworks would be the most significant without knowing the specific pieces included in the exhibition “Exposition de l’art italien de Cimabue à Tiepolo.”</p>
<p>However, we can make some educated guesses based on the artists mentioned and the general timeline:</p>
<p>From Cimabue to Michelangelo:</p>
<p>•	Cimabue’s “Madonna Enthroned” (c. 1280): This iconic painting is considered a pivotal work in the development of Italian painting and is a key example of the transition from Byzantine art to the Italian Gothic style.</p>
<p>•	Giotto’s “Ognissanti Madonna” (c. 1300-1310): Another masterpiece of early Italian painting, Giotto’s work is known for its revolutionary naturalism and three-dimensionality.</p>
<p>•	Masaccio’s “The Tribute Money” (c. 1425-1427): A pivotal work of the Early Renaissance, this fresco demonstrates Masaccio’s mastery of perspective and realism.</p>
<p>•	Michelangelo’s “David” (1501-1504): A monumental sculpture that embodies the ideals of the High Renaissance, “David” is one of the most recognizable artworks in the world.</p>
From Michelangelo to Tiepolo:</p>
<p>•	Raphael’s “The School of Athens” (1509-1511): This fresco is a masterpiece of the High Renaissance, depicting a gathering of philosophers and scientists.</p>
<p>•	Titian’s “Venus of Urbino” (1538): A sensual and evocative portrait, this painting showcases Titian’s mastery of color and composition.</p>
<p>•	Caravaggio’s “The Calling of Saint Matthew” (1600): A groundbreaking work of Baroque painting, “The Calling of Saint Matthew” is known for its dramatic realism and use of chiaroscuro.</p>
<p>•	Tiepolo’s “The Triumph of Chastity” (1750-1753): A masterpiece of Rococo painting, this fresco showcases Tiepolo’s decorative style and mastery of light and color.</p>
<p>Note: This list is not exhaustive. Many other significant works by artists like Leonardo da Vinci, Donatello, Botticelli, and Tintoretto could be included, depending on the exhibition’s specific focus and scope.</p>
<p>To find the most significant artworks, it’s best to look for the official catalogue or website of the exhibition. This will provide detailed information about the featured artists and works.</p>
        </td>
 
    <td>
    <p> Unfortunately, there isn't a publicly available list detailing every artwork in the "Exposition de l'art italien de Cimabue à Tiepolo." However, based on what we know about the exhibition and the artists it covered, we can assume some of the most significant artworks presented likely included:</p>
<p>Michelangelo Buonarotti: We can't be certain which specific pieces of his were on display, but some of his most renowned works created before 1935 (the year of the exhibition) include:</p>
<p>Sistine Chapel ceiling frescoes (1508-1512)</p>
<p>Pietà (1498-1500) sculpture</p>
<p>David (1501-1504) sculpture</p>
<p>Other Major Artists: The exhibition likely featured significant works from other Italian masters within the timeframe, potentially including:</p>
<p>Sandro Botticelli: The Birth of Venus</p>
<p>Raphael: Madonna della Seggiola</p>
<p>Titian: Venus of Urbino</p>
<p>Caravaggio: Bacchus</p>
<p>These are just a few possibilities, and the actual exhibition might have included many other important pieces.</p>
<p>Here are some suggestions for further research:</p>
<p>Search for online resources about the Petit Palais in Paris, where the exhibition took place. They might have archived information about the specific artworks displayed.</p>
<p>Look for academic papers or articles discussing the exhibition. These might mention some of the key works included.</p>
<p>Search for publications or books on Italian art history from the relevant period (13th to 18th centuries). These might provide context about prominent artworks of the time.</p> </td> 
    
  </tr>
  
</tbody>

</table>
  
### Question 3

*Could you transform this description into RDF format using ArCo ontology?*

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
   <p>@prefix  arCo: <http://purl.org/NET/arCo/> .</p>
<p>@prefix  dc: <http://purl.org/dc/elements/1.1/> .</p>
<p>@prefix  foaf: <http://xmlns.com/foaf/0.1/> .</p>
<p>@prefix  xsd: <http://www.w3.org/2001/XMLSchema#> .</p>

<p><http://example.org/event/italian-art-exhibition> a arCo:Event;</p>
  <p>dc:title "Exposition de l'art italien de Cimabue à Tiepolo" ;</p>
 <p>arCo:hasTopic <http://example.org/topic/italian-art>;</p>
 <p>arCo:hasDuration [ a arCo:Duration ; arCo:hasUnit "century" ; arCo:hasValue "6" ];</p>
 <p>arCo:hasFocus arCo:ArtProduction ;</p>
 <p>arCo:hasTime [ a arCo:Time ; arCo:hasUnit "century" ; arCo:hasValue "13" ];</p>
 <p>arCo:hasTime [ a arCo:Time ; arCo:hasUnit "century" ; arCo:hasValue "18" ];</p>
 <p>arCo:hasCreator <http://example.org/artist/michelangelo>;</p>
  <p>arCo:hasFocus <http://example.org/topic/renaissance>;</p>
  <p>arCo:hasFocus <http://example.org/topic/baroque>;</p>
  <p>arCo:hasFocus <http://example.org/topic/rococo>.</p>

<p><http://example.org/topic/italian-art> a arCo:Topic ;</p>
   <p> dc:title "Italian Art" ;</p>
  <p>  arCo:hasFocus arCo:ArtProduction ;</p>
  <p>  arCo:hasFocus arCo:ArtHistory .</p>

<p><http://example.org/topic/renaissance> a arCo:Topic ;</p>
 <p>   dc:title "Renaissance" ;</p>
 <p>   arCo:hasFocus arCo:ArtProduction .</p>

<p><http://example.org/topic/baroque> a arCo:Topic ;</p>
  <p>  dc:title "Baroque" ;</p>
  <p>  arCo:hasFocus arCo:ArtProduction .</p>

<p><http://example.org/topic/rococo> a arCo:Topic ;</p>
 <p>   dc:title "Rococo" ;</p>
 <p>   arCo:hasFocus arCo:ArtProduction .</p>

<p><http://example.org/artist/michelangelo> a arCo:Agent ;</p>
 <p>   foaf:name "Michelangelo Buonarotti" ;</p>
  <p>  arCo:hasRole arCo:Artist ;</p>
  <p>  arCo:hasFocus arCo:ArtProduction .</p>

<p><http://example.org/artist/ciabue> a arCo:Agent ;</p>
  <p>  foaf:name "Cimabue" ;</p>
  <p>  arCo:hasRole arCo:Artist ;</p>
  <p>  arCo:hasFocus arCo:ArtProduction .</p>

<p><http://example.org/artist/tiepolo> a arCo:Agent ;</p>
<p>    foaf:name "Giovanni Battista Tiepolo" ;</p>
 <p>   arCo:hasRole arCo:Artist ;</p>
  <p>  arCo:hasFocus arCo:ArtProduction .</p>

<p><http://example.org/artwork/madonna-enthroned> a arCo:Artifact ;</p>
 <p>   dc:title "Madonna Enthroned" ;</p>
 <p>  arCo:hasCreator <http://example.org/artist/ciabue> ;</p>
  <p>  arCo:hasTime [ a arCo:Time ; arCo:hasUnit "year" ; arCo:hasValue "1280" ] ;</p>
  <p>   arCo:hasType arCo:Painting .</p>

<p><http://example.org/artwork/david> a arCo:Artifact ;</p>
 <p>   dc:title "David" ;</p>
  <p>  arCo:hasCreator <http://example.org/artist/michelangelo> ;</p>
  <p>  arCo:hasTime [ a arCo:Time ; arCo:hasUnit "year" ; arCo:hasValue "1504" ] ;</p>
   <p> arCo:hasType arCo:Sculpture .</p>

<p><http://example.org/artwork/school-of-athens> a arCo:Artifact ;</p>
 <p>   dc:title "The School of Athens" ;</p>
 <p>   arCo:hasCreator <http://example.org/artist/raphael> ;</p>
  <p>  arCo:hasTime [ a arCo:Time ; arCo:hasUnit "year" ; arCo:hasValue "1511" ] ;</p>
  <p>  arCo:hasType arCo:Painting .</p>

<p><http://example.org/artwork/venus-of-urbino> a arCo:Artifact ;</p>
 <p>   dc:title "Venus of Urbino" ;</p>
  <p>  arCo:hasCreator <http://example.org/artist/titian> ;</p>
  <p>  arCo:hasTime [ a arCo:Time ; arCo:hasUnit "year" ; arCo:hasValue "1538" ] ;</p>
  <p>  arCo:hasType arCo:Painting .

<p><http://example.org/artwork/calling-of-saint-matthew> a arCo:Artifact ;</p>
 <p>   dc:title "The Calling of Saint Matthew" ;</p>
  <p>  arCo:hasCreator <http://example.org/artist/caravaggio> ;</p>
  <p>  arCo:hasTime [ a arCo:Time ; arCo:hasUnit "year" ; arCo:hasValue "1600" ] ;</p>
  <p>  arCo:hasType arCo:Painting .</p>

<p><http://example.org/artwork/triumph-of-chastity> a arCo:Artifact ;</p>
 <p>   dc:title "The Triumph of Chastity" ;</p>
 <p>   arCo:hasCreator <http://example.org/artist/tiepolo> ;</p>
 <p>   arCo:hasTime [ a arCo:Time ; arCo:hasUnit "year" ; arCo:hasValue "1753" ] ;</p>
  <p>  arCo:hasType arCo:Painting .</p>
<p>Explanation:</p>
<p>•	ArCo Ontology: This RDF uses the ArCo ontology (http://purl.org/NET/arCo/) to describe the event, topics, artists, and artworks.</p>
<p>•	Classes: We use classes like arCo:Event, arCo:Topic, arCo:Agent, arCo:Artist, and arCo:Artifact to represent the entities.</p>
<p>•	Properties: We use properties like dc:title, arCo:hasTopic, arCo:hasFocus, arCo:hasTime, arCo:hasCreator, and arCo:hasType to connect the entities and describe their attributes.</p>
<p>•	Individuals: Each entity is represented as an individual with a unique URI. For example, <http://example.org/event/italian-art-exhibition> represents the exhibition.</p>
<p>•	Time: The arCo:hasTime property is used to indicate the time period of the event and the creation time of the artworks.</p>
<p>•	Focus: The arCo:hasFocus property is used to indicate the topics and aspects that the event and artists are focused on.</p>
<p>•	Type: The arCo:hasType property is used to indicate the type of the artwork.</p>
<p>This RDF representation provides a structured and machine-readable description of the exhibition and its key elements. You can use this RDF to:</p>
<p>•	Query and analyze the data.</p>
<p>•	Integrate the data with other knowledge bases.</p>
<p>•	Develop applications that interact with the exhibition data.</p>
<p>This is just a basic example, and you can add more details and properties to enrich the RDF representation based on your specific needs.</p>  </td>

 
    <td>
    <p> Absolutely! Here's the transformed description into RDF format using the ArCo ontology:</p>
<p>XML</p>


<p><rdf:RDF xmlns:arco="http://www.cidoc-crm.org/cidoc-crm/"></p>
        <p> xmlns:xsd="http://www.w3.org/2001/XMLSchema#"</p>
       <p>  xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"></p>

<p>  <arco:E22_Exhibition rdf:about="http://example.org/exposition_art_italien"></p>
  <p>  <arco:P1_is_identified_by></p>
   <p>   <rdf:Literal xml:lang="en"> Exposition de l'art italien de Cimabue à Tiepolo </rdf:Literal> </p>
 <p>   </arco:P1_is_identified_by></p>
 <p>   <arco:P14_consists_of> </p>
  <p>    <arco:E72_Exhibition_Place rdf:about="http://example.org/petit_palais"> </p>
  <p>      <arco:P1_is_identified_by> </p>
  <p>        <rdf:Literal xml:lang="en">Petit Palais</rdf:Literal> </p>
  <p>      </arco:P1_is_identified_by></p>
  <p>    </arco:E72_Exhibition_Place></p>
  <p>    </arco:P14_consists_of></p>
  <p>  <arco:P16_was_in_existence></p>
  <p>    <arco:E52_Time-Period></p>
  <p>      <arco:P82_has_duration></p>
  <p>        <xsd:duration>P1Y</xsd:duration> </arco:P82_has_duration></p>
  <p>      </arco:E52_Time-Period></p>
  <p>  </arco:P16_was_in_existence></p>
  <p>  </arco:E22_Exhibition></p>

 <p> <arco:E21_Person rdf:about="http://example.org/michelangelo"></p>
  <p>  <arco:P1_is_identified_by></p>
  <p>    <rdf:Literal xml:lang="en">Michelangelo Buonarotti</rdf:Literal></p>
  <p>  </arco:P1_is_identified_by></p>
  <p>  <arco:P7_participates_in></p>
  <p>    <arco:E22_Exhibition rdf:about="http://example.org/exposition_art_italien"></p>
   <p>     </arco:E22_Exhibition></p>
 <p>   </arco:P7_participates_in></p>
 <p>   </arco:E21_Person></p>

<p>  </rdf:RDF></p>
<p>Explanation:</p>
<p>•	We define the exhibition as an arco:E22_Exhibition with a URI (http://example.org/exposition_art_italien) and a human-readable <p>title.</p>
<p>•	The location (Petit Palais) is linked as an arco:E72_Exhibition_Place. Add more elements for additional locations.</p>
<p>•	The exhibition duration is a placeholder (P1Y for one year), replace it with the actual duration if known. Specific start and end dates can also be added.</p>
<p>•	We included Michelangelo as an arco:E21_Person participating in the exhibition (linked through arco:P7_participates_in).</p>
<p>•	The comment section highlights the need to replace placeholders with specific artworks described using relevant ArCo classes (e.g., arco:E22_Man-Made_Object).</p>
<p>Note:</p>
<p>•	Replace http://example.org with your actual URIs for the exhibition, location, and person.</p>
<p>•	You can extend this example by adding information about specific artworks presented and their creators.</p>
<p>This is a basic example using the ArCo ontology. It can be further customized to include more details depending on the available information about the exhibition.</p>
</td>
</tr>
</tbody>
</table>       


 
 
   ## Creating new triples
   
**First, I check if the artworks found by the AI are present in ArCo.**

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
**This artwork wasn't found in ArCo**

**After the research in SPARQL, I turned to Large Language Models (LLMs) for further analysis. CHAT GPT and GEMINI seem to be the most reliable LLMs.​**

_artwork 1_

https://dati.beniculturali.it/lodview-arco/resource/CulturalEvent/49e9140e7d94d2049c1eeb6582c51e01.html cis:involvesCulturalEntity https://dati.beniculturali.it/lodview-arco/resource/HistoricOrArtisticProperty/0900286607.html

_artwork 2_

https://dati.beniculturali.it/lodview-arco/resource/CulturalEvent/49e9140e7d94d2049c1eeb6582c51e01.html cis:involvesCulturalEntity https://dati.beniculturali.it/lodview-arco/resource/HistoricOrArtisticProperty/Pietà.html



[back](./)
