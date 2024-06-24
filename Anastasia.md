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

### Question 1 (zero-shot prompting)

**Cultural event:** Exposition de l'art italien de Cimabue à Tiepolo 

**Artist:** Michelangelo Buonarotti 

**Question:** What does this cultural event represent?


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
  
### Question 2 (self-consistency)

**Which artworks are present in the cultural event "Esposizione d’arte italiana da Cimabue a Tiepolo"?**


<table style="text-align: center;">
  <thead>
    <tr>
      <th>CHAT GPT</th>
      <th>GEMINI</th>
  </tr>
  </thead>
  <tbody>
   <tr>
        <td> <p>You’re asking about the artworks in the “Esposizione d’arte italiana da Cimabue a Tiepolo” exhibition. Unfortunately, you’re missing some crucial information to answer your question:</p>
<p>•	Which specific exhibition are you referring to? There have been numerous exhibitions with this title or variations of it. Knowing the exact event is vital to identify the artworks.</p>
<p>•	When and where was the exhibition held? The specific time and place of the exhibition are essential for finding its catalogue and details of the artworks.</p>
<p>To help you find the information you need, please provide:</p>
<p>•	The full and exact title of the exhibition.
•	The year and city where the exhibition took place.</p>
<p>Once you provide this information, I can help you find a list of the artworks displayed.</p>
        </td>
<td>
 <p>The specific artworks in the "Esposizione d’arte italiana da Cimabue a Tiepolo" are unfortunately unknown since it wasn't a permanent exhibition. However, based on the title, we can glean some information:</p>
 <p>•	The timeframe: "Cimabue" refers to a late 13th/early 14th-century artist and "Tiepolo" to an 18th-century artist. So, the exhibition likely focused on Italian art from the late medieval period to the 18th century.</p>
 <p>•	The focus: The title mentions "arte italiana" (Italian art), so it would have showcased paintings, sculptures, and possibly other art forms by prominent Italian artists from that period.</p>
 <p>Here's what we can expect:</p>
 <p>•	It likely featured iconic works by Giotto, a pivotal figure transitioning from medieval to Renaissance styles.</p>
 <p>•	Renaissance masters like Leonardo da Vinci, Raphael, and Donatello would have been well-represented.</p>
 <p>•	The exhibition might have included paintings from the Venetian school by Titian, Tintoretto, and of course, Tiepolo himself.</p>
 <p>If you'd like to explore further, you can try searching for the exhibition catalog (usually a booklet with details on the artworks displayed) if one exists. Look for phrases like "Exposition de l'art italien de Cimabue à Tiepolo catalogue" or "Esposizione d’arte italiana da Cimabue a Tiepolo catalogo".</p>
</td>
 </tr>
  
</tbody>

</table>

**Tell me about the artworks exhibited in "Esposizione d’arte italiana da Cimabue a Tiepolo”**

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
  <p>You’re talking about a very famous exhibition, one of the most important art events of the early 20th century!</p>
  <p>The “Esposizione d’arte italiana da Cimabue a Tiepolo”, held in Rome in 1911, was a massive exhibition that showcased Italian art from the 13th to the 18th centuries. It was a landmark event, not just for its scope, but also for the way it influenced art history.</p>
  <p>While it’s impossible to list every single artwork in the exhibition, here are some highlights and key features:</p>
  <p>Key Points:</p>
  <p>•	Scope: The exhibition covered over 500 years of Italian art, from the proto-Renaissance of Cimabue to the late Baroque of Tiepolo.</p>
  <p>•	Importance: It was a crucial event in the development of art history as a discipline. The exhibition helped establish the chronological and stylistic understanding of Italian art that we still use today.</p>
  <p>•	Influence: The exhibition was also instrumental in the growing appreciation for early Italian art, leading to the establishment of museums and collections dedicated to these periods.</p>
<p>Some Notable Artworks:</p>
<p>•	Cimabue: “Madonna Enthroned” (c. 1280)
•	Giotto: “Ognissanti Madonna” (c. 1300)
•	Duccio: “Maestà” (c. 1308-1311)
•	Masaccio: “The Tribute Money” (c. 1425)
•	Leonardo da Vinci: “Virgin of the Rocks” (c. 1483-1486)
•	Raphael: “The School of Athens” (c. 1509-1511)
•	Michelangelo: “The Last Judgement” (c. 1536-1541)
•	Titian: “Venus of Urbino” (c. 1538)
•	Caravaggio: “The Calling of Saint Matthew” (c. 1600)
•	Bernini: “David” (c. 1623-1624)
•	Tiepolo: “The Triumph of Galatea” (c. 1745-1750)
</p>
<p>Where to Find More Information:</p>
<p>•	Museums: Many of the artworks featured in the 1911 exhibition are now in museums around the world. You can search the collections of these museums online to find images and information about specific works.</p>
<p>•	Art History Books: There are many books written about the history of Italian art, and some of these will mention the “Esposizione d’arte italiana da Cimabue a Tiepolo” exhibition.</p>
<p>•	Academic Databases: Searching academic databases like JSTOR can help you find scholarly articles and theses that discuss the 1911 exhibition and its influence.</p>
<p>I hope this information helps! Let me know if you have any other questions.</p> </td>
<td>
 <p>While I can't give you a definitive list of artworks exhibited in "Esposizione d’arte italiana da Cimabue a Tiepolo" because it wasn't a permanent exhibition, here's what we can infer based on the title and historical context:</p>
 <p>Time Period: The title mentions Cimabue (late 13th/early 14th century) and Tiepolo (18th century). So, the exhibition likely showcased Italian art from the late medieval period to the 18th century.</p>
 <p>Focus on Italian Masters: Looking at "arte italiana" (Italian art), the exhibition would have featured paintings, sculptures, and possibly other art forms by prominent Italian artists from that period.</p>
<p>Possible Artworks:</p>
 <p>•	Early Renaissance: Giotto, a pivotal figure bridging the medieval and Renaissance styles, could have been well-represented with frescoes or paintings.</p>
 <p>•	High Renaissance: Masters like Leonardo da Vinci (Mona Lisa?), Raphael (Sistine Madonna?), and Donatello (David?) would have been strong contenders for inclusion.</p>
 <p>•	Venetian School: Paintings by Titian, Tintoretto, and Tiepolo himself might have been showcased.</p>
 <p>Finding More Information:</p>
 <p>To delve deeper, try searching for the exhibition catalog, a booklet with details on displayed artworks. Look for phrases like "Exposition de l'art italien de Cimabue à Tiepolo catalogue" or "Esposizione d’arte italiana da Cimabue a Tiepolo catalogo".</p>
 <p>Remember, this was a specific exhibition, and the actual artworks displayed might differ from what we've discussed.</p>
</td>
  </tr>
  
</tbody>

</table>


  
**What are the most significant artworks presented?**

    
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
  <p>You’re right to ask! It’s impossible to say definitively which artworks would be the most significant without knowing the specific pieces included in the exhibition “Exposition de l’art italien de Cimabue à Tiepolo.”</p>
  <p>However, we can make some educated guesses based on the artists mentioned and the general timeline:</p>
  <p>From Cimabue to Michelangelo:</p>
  <p>Cimabue’s “Madonna Enthroned” (c. 1280): This iconic painting is considered a pivotal work in the development of Italian painting and is a key example of the transition from Byzantine art to the Italian Gothic style.</p>
  <p>• Giotto’s “Ognissanti Madonna” (c. 1300-1310): Another masterpiece of early Italian painting, Giotto’s work is known for its revolutionary naturalism and three-dimensionality.</p>
  <p>Masaccio’s “The Tribute Money” (c. 1425-1427): A pivotal work of the Early Renaissance, this fresco demonstrates Masaccio’s mastery of perspective and realism.</p>
  <p>•	Michelangelo’s “David” (1501-1504): A monumental sculpture that embodies the ideals of the High Renaissance, “David” is one of the most recognizable artworks in the world.</p>
From Michelangelo to Tiepolo:</p>
<p>•	Raphael’s “The School of Athens” (1509-1511): This fresco is a masterpiece of the High Renaissance, depicting a gathering of philosophers and scientists.</p>
<p>•	Titian’s “Venus of Urbino” (1538): A sensual and evocative portrait, this painting showcases Titian’s mastery of color and composition.</p>
<p>•	Caravaggio’s “The Calling of Saint Matthew” (1600): A groundbreaking work of Baroque painting, “The Calling of Saint Matthew” is known for its dramatic realism and use of chiaroscuro.</p>
<p>•	Tiepolo’s “The Triumph of Chastity” (1750-1753): A masterpiece of Rococo painting, this fresco showcases Tiepolo’s decorative style and mastery of light and color.</p>
<p>Note: This list is not exhaustive. Many other significant works by artists like Leonardo da Vinci, Donatello, Botticelli, and Tintoretto could be included, depending on the exhibition’s specific focus and scope.</p>
<p>To find the most significant artworks, it’s best to look for the official catalogue or website of the exhibition. This will provide detailed information about the featured artists and works.</p>  </td>

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





  
### Question 3 (few-shot prompting)

**I want you to generate a description of a cultural event in a concise and engaging way.**

**Example:**

**Event:** Venice Biennale

**Description:** Venice Biennale, the oldest and most prestigious cultural institution in the world! This international exhibition, hosted annually by the Biennale Foundation in Venice, Italy, has been promoting new artistic trends and organizing international events in contemporary arts for over a century.

 **Now, write a description for this event: Esposizione d’arte italiana da Cimabue a Tiepolo**

**Event:** Esposizione d’arte italiana da Cimabue a Tiepolo

**Your Description:**

<table>
  <thead>
    <tr>
      <th>CHAT GPT</th>
      <th>GEMINI</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p>A Journey Through Time: “Esposizione d’arte italiana da Cimabue a Tiepolo”</p>
        <p>Step into the heart of Italian art history with “Esposizione d’arte italiana da Cimabue a Tiepolo,” an immersive exhibition showcasing masterpieces from the 13th to the 18th centuries. This captivating journey, featuring iconic works from Cimabue to Tiepolo, traces the evolution of Italian painting through centuries of innovation and artistic brilliance. Prepare to be dazzled by the artistry of renaissance masters and witness the rise of Baroque splendor in this captivating exhibition.</p>
      </td>
      <td>
       <p>Event: Esposizione d’arte italiana da Cimabue a Tiepolo</p>
      <p>Description: Journey through seven centuries of Italian art! This exhibition, though not currently on display, would have showcased a remarkable array of Italian masterpieces, from the groundbreaking works of Cimabue to the Venetian genius of Tiepolo. Explore the evolution of Italian art from the late medieval period to the 18th century and discover the beauty that defined a artistic movement.</p></td>
    </tr>
  </tbody>
</table>

### Question 4 (Chain-of-thought)

**I want you to conduct a comprehensive research summary on Michelangelo Buonarroti, the renowned Italian artist. Please follow these steps:**
**1.	Outline Michelangelo Buonarroti’s life and background:** Summarize his early life, education, personal experiences  and major life events that influenced his artistic journey.
**2.	Analyze Michelangelo Buonarroti’s artistic style and techniques:** Describe the distinctive features of his artworks, the techniques he employed (e.g., color palettes, brushstrokes, subject matter).
**3.	Explore Michelangelo Buonarroti’s artistic legacy:** Discuss his impact on art history, the evolution of his influence on contemporary art and culture, and his enduring popularity as a cultural icon.
**4.	Conclude with a brief summary of Michelangelo Buonarroti’s significance:** Summarize his importance as a painter, sculptor, architect and poet of the High Renaissance


<table>
  <thead>
    <tr>
      <th>CHAT GPT</th>
      <th>GEMINI</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p>Michelangelo Buonarroti: A Titan of the Renaissance</p>
        <p>1. Life and Background:
Michelangelo Buonarroti (1475-1564) was born in Caprese, Italy, into a family of modest means. His talent for art emerged early, and he began his artistic training in Florence under the tutelage of Domenico Ghirlandaio. He later studied sculpture in the Medici gardens, where he was exposed to the art of ancient Rome. Michelangelo’s life was marked by periods of both artistic triumph and personal adversity. He was deeply involved in the political and religious struggles of his time, and his work often reflected these turbulent currents.
</p>
       <p>Key Life Events:</p>
<p>Early Patronage: He was commissioned by Lorenzo de’ Medici, a pivotal event that propelled him into the Florentine artistic scene.</p>
<p>The David: His iconic sculpture of David, completed in 1504, solidified his reputation as a master sculptor.</p>
<p>Sistine Chapel: Michelangelo’s frescoes on the ceiling of the Sistine Chapel in Rome (1508-1512), depicting scenes from the Book of Genesis, stand as a testament to his unparalleled artistic vision.</p>
<p>The Last Judgment: He returned to the Sistine Chapel in 1536 to paint the monumental “Last Judgement” fresco on the altar wall, a powerful and emotive portrayal of the divine judgment.</p>
<p>Architecture: He designed the dome of St. Peter’s Basilica, one of his most significant architectural achievements.
</p>
       <p>2. Artistic Style and Techniques:</p>
<p>Michelangelo’s art is characterized by its grandeur, realism, and emotional intensity. His figures are often depicted in dynamic poses, showcasing a profound understanding of anatomy and a deep appreciation for the human form. He meticulously sculpted his subjects, capturing their inner strength and vulnerability with remarkable precision.
</p>
       <p>Key Features:</p>
<p>Nudes: He often depicted the human body in its raw and natural state, breaking away from the idealized forms of the early Renaissance.</p>
<p>Dynamic Composition: His figures are typically in motion, creating a sense of drama and energy.</p>
<p>Emotional Intensity: His works evoke a wide range of emotions, from awe and wonder to pain and despair.</p>
<p>Chiaroscuro: He expertly used light and shadow to create depth and realism in his works.
</p>
       <p>3. Artistic Legacy:</p>
<p>Michelangelo’s influence on art history is immeasurable. He set new standards for sculpture, painting, and architecture, inspiring generations of artists. His work, from the soaring figures of the Sistine Chapel to the powerful beauty of the Pietà, continues to captivate and inspire audiences around the world.
</p>
       <p>Impact on Contemporary Art and Culture:</p>
<p>Michelangelo’s influence is visible in the art of the Baroque period and beyond. He is frequently cited as a major influence by artists across diverse genres, including painters, sculptors, and architects. His powerful images and iconic figures have become ingrained in our cultural consciousness, appearing in everything from literature and film to music and fashion.
</p>
       <p>4. Significance as a Renaissance Master:</p>
<p>Michelangelo Buonarroti stands as one of the greatest artists of the High Renaissance. He was a master of multiple disciplines, excelling in sculpture, painting, architecture, and poetry. His work embodies the spirit of the Renaissance, a period characterized by a renewed interest in classical learning and artistic innovation.</p>
<p>In conclusion, Michelangelo’s genius transcended the boundaries of artistic expression, leaving an indelible mark on art history and culture. His legacy continues to inspire and captivate, reminding us of the enduring power of human creativity.
</p>
      </td>
      <td><p>Michelangelo Buonarroti: A Renaissance Titan</p>
      <p>1. Life and Background</p>
<p>Michelangelo Buonarroti (1475-1564) was born into a prominent Florentine family. Though apprenticed to a painter, his true passion resided in sculpting. Early exposure to classical art in Florence deeply influenced his artistic vision. He secured patronage from powerful families like the Medici, shaping his career trajectory. Personal experiences, including the political turmoil of his time, are often reflected in the intensity and religious themes found in his work.
</p>
       <p>2. Artistic Style and Techniques</p>
<p> Michelangelo's artistic style is characterized by a mastery of human anatomy and a profound understanding of form. His figures are powerful and dynamic, often imbued with a sense of drama and emotional depth. He was a meticulous draftsman, his works showcasing a precise and detailed approach. As a sculptor, he favored marble, meticulously carving figures that seem to burst from the stone. His paintings, most famously the Sistine Chapel ceiling, utilize vibrant colors and dramatic lighting to create a sense of awe and grandeur. Biblical narratives and themes of mortality are recurring subjects in both his sculptures and paintings.
</p>
       <p>3. Artistic Legacy</p>
       <p>Michelangelo's influence on art history is unparalleled. He is considered one of the defining figures of the High Renaissance, along with Leonardo da Vinci and Raphael. His mastery of multiple disciplines – sculpture, painting, and architecture – established him as a true artistic genius. His influence on subsequent generations of artists is undeniable, with his techniques and approach to anatomy being studied and emulated for centuries. Michelangelo's impact extends beyond the visual arts, his work inspiring writers and musicians alike. His enduring popularity stems from the timeless beauty, profound emotions, and technical virtuosity embodied in his creations.</p>
       <p>4. Significance: A Master of Many Arts</p>
       <p>Michelangelo's significance lies in his unparalleled contributions to the visual arts. He is considered one of the greatest sculptors of all time, with works like David and Pieta becoming enduring symbols of human form and emotion. As a painter, the Sistine Chapel ceiling remains a landmark achievement in Western art. His architectural designs for the St. Peter's Basilica in Rome solidified his reputation as a true Renaissance man, excelling in multiple artistic disciplines. Michelangelo's life and work continue to inspire artists, scholars, and the general public, solidifying his place as a cornerstone of Western cultural heritage.</p>
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
