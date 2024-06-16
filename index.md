---
title: [MICHELANGELO BUONARROTI] 
description: [between Rome and Florence.]
---
This WebSite is made by...

[Giusy Cadili](./Giusy.html) 

[Anastasia Serdiuk](./Anastasia.html)



![Michelangelo Buonarroti](https://hips.hearstapps.com/hmg-prod/images/portrait-of-michelangelo-buonarroti-early-17th-cen-found-in-news-photo-1664961873.jpg?crop=1xw:0.79688xh;center,top&resize=640:*)

Michelangelo Buonarroti, known simply as Michelangelo, was an Italian painter, sculptor, architect, and poet. Nicknamed the Divine Artist, he was a leading figure of the Italian Renaissance and was recognized by his contemporaries as one of the greatest artists of all time. Born in Florence and died in Rome.

## Objectives

Through the use of the ArCo knowledge base and large language models, this project aims to explore the cultural events and works of the Italian artist Michelangelo Buonarroti. It particularly focuses on two of the cities where the artist created most of his works, Rome and Florence.

## Methodology

To achieve these objectives, we adopted a structured methodology:

1) Initial Exploration: We began by exploring the ArCo knowledge graph to identify relevant topics and concepts.

2) Query Formulation: Based on our initial exploration, we formulated SPARQL Queries to extract specific data related to cultural events about Michelangelo Buonarroti in the cities of Rome and Florence.

3) LLM Integration: We integrated and compared two Large Language Models (LLMs) such as ChatGPT and Gemini to retrieve additional information and provide context, further enriching the knowledge graph.


# Step 1

First we make sure that the artist "Michelangelo Buonarroti" is present in the ArCo database.

```js
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX cpv: <https://w3id.org/italia/onto/CPV/>

ASK
WHERE
{
?subject a cpv:Person;
                 rdfs:label ?label

FILTER(REGEX(?label ,"Buonarroti Michelangelo","i"))
}
```
[Result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=PREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0D%0APREFIX+rdf%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0D%0APREFIX+cpv%3A+%3Chttps%3A%2F%2Fw3id.org%2Fitalia%2Fonto%2FCPV%2F%3E%0D%0A%0D%0AASK%0D%0AWHERE%0D%0A%7B%0D%0A%3Fsubject+a+cpv%3APerson%3B%0D%0A+++++++++++++++++rdfs%3Alabel+%3Flabel%0D%0A%0D%0AFILTER%28REGEX%28%3Flabel+%2C%22Buonarroti+Michelangelo%22%2C%22i%22%29%29%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&signal_void=on).

Once determined the presence of this relevant data, we can procede with more detailed queries.

# Step 2

What are the cultural events associated with the artist "Michelangelo Buonarroti"?

This query aims to retrieve cultural events associated with a specific artist, providing insights into the specific events ordered by event name and, if indicated, the year of each event.

```js
PREFIX cis: <http://dati.beniculturali.it/cis/>
PREFIX a-cd: <https://w3id.org/arco/ontology/context-description/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX ti: <https://w3id.org/italia/onto/TI/>

SELECT DISTINCT ?culturalevent ?eventlabel ?author ?authorlabel ?year
WHERE
{
?culturalevent a cis:CulturalEvent ;
                        rdfs:label ?eventlabel.
?culturalevent cis:involvesCulturalEntity ?culturalEntity .
?culturalEntity a-cd:hasAuthor ?author .
?author rdfs:label ?authorlabel

FILTER(REGEX(?authorlabel, "Buonarroti Michelangelo" , "i"))
OPTIONAL {?culturalevent ti:time ?year}
}
ORDER BY ASC (?eventlabel)
LIMIT 100
```
[Result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=PREFIX+cis%3A+%3Chttp%3A%2F%2Fdati.beniculturali.it%2Fcis%2F%3E%0D%0APREFIX+a-cd%3A+%3Chttps%3A%2F%2Fw3id.org%2Farco%2Fontology%2Fcontext-description%2F%3E%0D%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0D%0APREFIX+rdf%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0D%0APREFIX+ti%3A+%3Chttps%3A%2F%2Fw3id.org%2Fitalia%2Fonto%2FTI%2F%3E%0D%0A%0D%0ASELECT+DISTINCT+%3Fculturalevent+%3Feventlabel+%3Fauthor+%3Fauthorlabel+%3Fyear%0D%0AWHERE%0D%0A%7B%0D%0A%3Fculturalevent+a+cis%3ACulturalEvent+%3B%0D%0A++++++++++++++++++++++++rdfs%3Alabel+%3Feventlabel.%0D%0A%3Fculturalevent+cis%3AinvolvesCulturalEntity+%3FculturalEntity+.%0D%0A%3FculturalEntity+a-cd%3AhasAuthor+%3Fauthor+.%0D%0A%3Fauthor+rdfs%3Alabel+%3Fauthorlabel%0D%0A%0D%0AFILTER%28REGEX%28%3Fauthorlabel%2C+%22Buonarroti+Michelangelo%22+%2C+%22i%22%29%29%0D%0AOPTIONAL+%7B%3Fculturalevent+ti%3Atime+%3Fyear%7D%0D%0A%7D%0D%0AORDER+BY+ASC+%28%3Feventlabel%29%0D%0ALIMIT+100&format=text%2Fhtml&timeout=0&signal_void=on).

# Step 3

What are the cultural events associated with the artist "Michelangelo Buonarroti" in Rome and Florence?

This query collects detailed information about cultural events related to these locations, providing insights into specific events and their geographical context. This data is crucial for understanding the cultural interactions between the artist and the two cities.

```js
PREFIX cis: <http://dati.beniculturali.it/cis/>
PREFIX clv: <https://w3id.org/italia/onto/CLV/>
PREFIX a-cd: <https://w3id.org/arco/ontology/context-description/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

SELECT DISTINCT ?culturalevent ?eventlabel ?author ?authorlabel ?place
WHERE
{
?culturalevent a cis:CulturalEvent ;
                        rdfs:label ?eventlabel .
?culturalevent cis:involvesCulturalEntity ?culturalEntity .
?culturalEntity a-cd:hasAuthor ?author .
?author rdfs:label ?authorlabel
FILTER(REGEX(?authorlabel, "Buonarroti Michelangelo" , "i"))

?place a cis:GeographicalFeature.
{?place rdfs:label "Firenze"}
UNION
{?place rdfs:label "Roma"}
?culturalevent clv:hasSpatialCoverage ?place.
}
```
[Result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=PREFIX+cis%3A+%3Chttp%3A%2F%2Fdati.beniculturali.it%2Fcis%2F%3E%0D%0APREFIX+clv%3A+%3Chttps%3A%2F%2Fw3id.org%2Fitalia%2Fonto%2FCLV%2F%3E%0D%0APREFIX+a-cd%3A+%3Chttps%3A%2F%2Fw3id.org%2Farco%2Fontology%2Fcontext-description%2F%3E%0D%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0D%0APREFIX+rdf%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0D%0A%0D%0ASELECT+DISTINCT+%3Fculturalevent+%3Feventlabel+%3Fauthor+%3Fauthorlabel+%3Fplace%0D%0AWHERE%0D%0A%7B%0D%0A%3Fculturalevent+a+cis%3ACulturalEvent+%3B%0D%0A++++++++++++++++++++++++rdfs%3Alabel+%3Feventlabel+.%0D%0A%3Fculturalevent+cis%3AinvolvesCulturalEntity+%3FculturalEntity+.%0D%0A%3FculturalEntity+a-cd%3AhasAuthor+%3Fauthor+.%0D%0A%3Fauthor+rdfs%3Alabel+%3Fauthorlabel%0D%0AFILTER%28REGEX%28%3Fauthorlabel%2C+%22Buonarroti+Michelangelo%22+%2C+%22i%22%29%29%0D%0A%0D%0A%3Fplace+a+cis%3AGeographicalFeature.%0D%0A%7B%3Fplace+rdfs%3Alabel+%22Firenze%22%7D%0D%0AUNION%0D%0A%7B%3Fplace+rdfs%3Alabel+%22Roma%22%7D%0D%0A%3Fculturalevent+clv%3AhasSpatialCoverage+%3Fplace.%0D%0A%7D%0D%0A%0D%0A&format=text%2Fhtml&timeout=0&signal_void=on)


# Step 4

Given the high number of events, we formulated a query to identify the exact number of events for each city.

How many events about the artist "Michelangelo Buonarroti were organized in Florence and how many in Rome? 

```js
PREFIX cis: <http://dati.beniculturali.it/cis/>
PREFIX clv: <https://w3id.org/italia/onto/CLV/>
PREFIX a-cd: <https://w3id.org/arco/ontology/context-description/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
SELECT COUNT (?culturalevent ) AS ?n
WHERE
{
?culturalevent a cis:CulturalEvent .
?culturalevent cis:involvesCulturalEntity ?culturalEntity .
?culturalEntity a-cd:hasAuthor ?author .
?author rdfs:label ?authorlabel.
?place a cis:GeographicalFeature;
                rdfs:label "Firenze".
?culturalevent clv:hasSpatialCoverage ?place.

FILTER( REGEX(?authorlabel, "Buonarroti Michelangelo" , "i"))
}
```
[Result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=PREFIX+cis%3A+%3Chttp%3A%2F%2Fdati.beniculturali.it%2Fcis%2F%3E%0D%0APREFIX+clv%3A+%3Chttps%3A%2F%2Fw3id.org%2Fitalia%2Fonto%2FCLV%2F%3E%0D%0APREFIX+a-cd%3A+%3Chttps%3A%2F%2Fw3id.org%2Farco%2Fontology%2Fcontext-description%2F%3E%0D%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0D%0APREFIX+rdf%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0D%0ASELECT+COUNT+%28%3Fculturalevent+%29+AS+%3Fn%0D%0AWHERE%0D%0A%7B%0D%0A%3Fculturalevent+a+cis%3ACulturalEvent+.%0D%0A%3Fculturalevent+cis%3AinvolvesCulturalEntity+%3FculturalEntity+.%0D%0A%3FculturalEntity+a-cd%3AhasAuthor+%3Fauthor+.%0D%0A%3Fauthor+rdfs%3Alabel+%3Fauthorlabel.%0D%0A%3Fplace+a+cis%3AGeographicalFeature%3B%0D%0A++++++++++++++++rdfs%3Alabel+%22Firenze%22.%0D%0A%3Fculturalevent+clv%3AhasSpatialCoverage+%3Fplace.%0D%0A%0D%0AFILTER%28+REGEX%28%3Fauthorlabel%2C+%22Buonarroti+Michelangelo%22+%2C+%22i%22%29%29%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&signal_void=on)

```js
PREFIX cis: <http://dati.beniculturali.it/cis/>
PREFIX clv: <https://w3id.org/italia/onto/CLV/>
PREFIX a-cd: <https://w3id.org/arco/ontology/context-description/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
SELECT COUNT (?culturalevent ) AS ?n
WHERE
{
?culturalevent a cis:CulturalEvent .
?culturalevent cis:involvesCulturalEntity ?culturalEntity .
?culturalEntity a-cd:hasAuthor ?author .
?author rdfs:label ?authorlabel.
?place a cis:GeographicalFeature;
                rdfs:label "Roma".
?culturalevent clv:hasSpatialCoverage ?place.

FILTER( REGEX(?authorlabel, "Buonarroti Michelangelo" , "i"))
}
```
[Result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=PREFIX+cis%3A+%3Chttp%3A%2F%2Fdati.beniculturali.it%2Fcis%2F%3E%0D%0APREFIX+clv%3A+%3Chttps%3A%2F%2Fw3id.org%2Fitalia%2Fonto%2FCLV%2F%3E%0D%0APREFIX+a-cd%3A+%3Chttps%3A%2F%2Fw3id.org%2Farco%2Fontology%2Fcontext-description%2F%3E%0D%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0D%0APREFIX+rdf%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0D%0ASELECT+COUNT+%28%3Fculturalevent+%29+AS+%3Fn%0D%0AWHERE%0D%0A%7B%0D%0A%3Fculturalevent+a+cis%3ACulturalEvent+.%0D%0A%3Fculturalevent+cis%3AinvolvesCulturalEntity+%3FculturalEntity+.%0D%0A%3FculturalEntity+a-cd%3AhasAuthor+%3Fauthor+.%0D%0A%3Fauthor+rdfs%3Alabel+%3Fauthorlabel.%0D%0A%3Fplace+a+cis%3AGeographicalFeature%3B%0D%0A++++++++++++++++rdfs%3Alabel+%22Roma%22.%0D%0A%3Fculturalevent+clv%3AhasSpatialCoverage+%3Fplace.%0D%0A%0D%0AFILTER%28+REGEX%28%3Fauthorlabel%2C+%22Buonarroti+Michelangelo%22+%2C+%22i%22%29%29%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&signal_void=on)

After identifying relevant cultural events, each group member chose a specific event for in-depth study. These events will be thoroughly explored, and individual reports will be prepared by each member.

[Check the individual work of Giusy Cadili](./Giusy.html) 

[Check the individual work of Anastasia Serdiuk](./Anastasia.html)


# CHALLENGES 

During the implementation of our project, we faced several challenges:

**Mastering SPARQL Queries**: One major hurdle was learning the complex SPARQL language and syntax to ensure our queries were accurate. This required extensive research and dedicated training sessions to grasp SPARQL’s intricacies and best practices.

**Developing an Engaging Website**: Creating a user-friendly and visually appealing website required a strategic approach. By leveraging modern web development frameworks and responsive design principles, we collaborated on design and content creation.

**Use of Large Language Models (LLMs)**: Our project involved using prompting techniques to motivate, describe, and analyze the differences between outputs of various LLMs. This exploration provided valuable insights into the capabilities and nuances of different language models, enriching our understanding of natural language processing technologies.

