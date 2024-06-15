
title: [MICHELANGELO BUONARROTI] 
description: [between Rome and Florence.]

Text can be **bold**, _italic_, or ~~strikethrough~~.

[Individual Work](./Giusy.html).

There should be whitespace between paragraphs.

There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.

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

# Step 2

What are the cultural events associated with the artist "Michelangelo Buonarroti"?

```js
PREFIX cis: <http://dati.beniculturali.it/cis/>
PREFIX a-cd: <https://w3id.org/arco/ontology/context-description/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>

SELECT DISTINCT ?culturalevent ?eventlabel ?author ?authorlabel
WHERE
{
?culturalevent a cis:CulturalEvent ;
                        rdfs:label ?eventlabel .
?culturalevent cis:involvesCulturalEntity ?culturalEntity .
?culturalEntity a-cd:hasAuthor ?author .
?author rdfs:label ?authorlabel

FILTER(REGEX(?authorlabel, "Buonarroti Michelangelo" , "i"))
}
ORDER BY ASC (?eventlabel)
LIMIT 100
```
[Result](https://dati.cultura.gov.it/sparql?default-graph-uri=&query=PREFIX+cis%3A+%3Chttp%3A%2F%2Fdati.beniculturali.it%2Fcis%2F%3E%0D%0APREFIX+a-cd%3A+%3Chttps%3A%2F%2Fw3id.org%2Farco%2Fontology%2Fcontext-description%2F%3E%0D%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0D%0APREFIX+rdf%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0D%0A%0D%0ASELECT+DISTINCT+%3Fculturalevent+%3Feventlabel+%3Fauthor+%3Fauthorlabel%0D%0AWHERE%0D%0A%7B%0D%0A%3Fculturalevent+a+cis%3ACulturalEvent+%3B%0D%0A++++++++++++++++++++++++rdfs%3Alabel+%3Feventlabel+.%0D%0A%3Fculturalevent+cis%3AinvolvesCulturalEntity+%3FculturalEntity+.%0D%0A%3FculturalEntity+a-cd%3AhasAuthor+%3Fauthor+.%0D%0A%3Fauthor+rdfs%3Alabel+%3Fauthorlabel%0D%0A%0D%0AFILTER%28REGEX%28%3Fauthorlabel%2C+%22Buonarroti+Michelangelo%22+%2C+%22i%22%29%29%0D%0A%7D%0D%0AORDER+BY+ASC+%28%3Feventlabel%29%0D%0ALIMIT+100%0D%0A&format=text%2Fhtml&timeout=0&signal_void=on).

# Step 3

What are the cultural events associated with the artist "Michelangelo Buonarroti" in Rome and Florence?

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

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
