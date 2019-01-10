# Example 1: Faculty members of a given department 
Returned: individual's URI | organization URI | vcardname URI | First Name | Last Name

```sparql
PREFIX rdf:      <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs:     <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd:      <http://www.w3.org/2001/XMLSchema#>
PREFIX owl:      <http://www.w3.org/2002/07/owl#>
PREFIX swrl:     <http://www.w3.org/2003/11/swrl#>
PREFIX swrlb:    <http://www.w3.org/2003/11/swrlb#>
PREFIX vitro:    <http://vitro.mannlib.cornell.edu/ns/vitro/0.7#>
PREFIX bibo:     <http://purl.org/ontology/bibo/>
PREFIX c4o:      <http://purl.org/spar/c4o/>
PREFIX cito:     <http://purl.org/spar/cito/>
PREFIX event:    <http://purl.org/NET/c4dm/event.owl#>
PREFIX fabio:    <http://purl.org/spar/fabio/>
PREFIX foaf:     <http://xmlns.com/foaf/0.1/>
PREFIX geo:      <http://aims.fao.org/aos/geopolitical.owl#>
PREFIX mcmaster: <https://expertsdev.mcmaster.ca/ontology/mcmaster#>
PREFIX obo:      <http://purl.obolibrary.org/obo/>
PREFIX ocrer:    <http://purl.org/net/OCRe/research.owl#>
PREFIX ocresd:   <http://purl.org/net/OCRe/study_design.owl#>
PREFIX skos:     <http://www.w3.org/2004/02/skos/core#>
PREFIX vcard:    <http://www.w3.org/2006/vcard/ns#>
PREFIX vitro-public: <http://vitro.mannlib.cornell.edu/ns/vitro/public#>
PREFIX vivo:     <http://vivoweb.org/ontology/core#>
PREFIX scires:   <http://vivoweb.org/ontology/scientific-research#>

#
# This example lists all faculty members for a given department - both by URI and name 
#
SELECT ?x ?organization ?z ?fnames ?lnames
WHERE {
  ?x a foaf:Person .
  ?x rdfs:label ?y .
  ?x vivo:relatedBy ?position .
  ?position rdfs:label ?positionLabel .
  ?position vivo:relates ?organization .
  ?organization rdfs:label "Engineering Physics" .
  ?x obo:ARG_2000028 ?tmp .
  ?tmp vcard:hasName ?z .
  ?z vcard:givenName ?fnames .
  ?z vcard:familyName ?lnames .
}
```
# Example 2: Search Example 1 output for a single user by first name
Returned: individual's URI | organization URI | vcardname URI | First Name | Last Name
```sparql
PREFIX rdf:      <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs:     <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd:      <http://www.w3.org/2001/XMLSchema#>
PREFIX owl:      <http://www.w3.org/2002/07/owl#>
PREFIX swrl:     <http://www.w3.org/2003/11/swrl#>
PREFIX swrlb:    <http://www.w3.org/2003/11/swrlb#>
PREFIX vitro:    <http://vitro.mannlib.cornell.edu/ns/vitro/0.7#>
PREFIX bibo:     <http://purl.org/ontology/bibo/>
PREFIX c4o:      <http://purl.org/spar/c4o/>
PREFIX cito:     <http://purl.org/spar/cito/>
PREFIX event:    <http://purl.org/NET/c4dm/event.owl#>
PREFIX fabio:    <http://purl.org/spar/fabio/>
PREFIX foaf:     <http://xmlns.com/foaf/0.1/>
PREFIX geo:      <http://aims.fao.org/aos/geopolitical.owl#>
PREFIX mcmaster: <https://expertsdev.mcmaster.ca/ontology/mcmaster#>
PREFIX obo:      <http://purl.obolibrary.org/obo/>
PREFIX ocrer:    <http://purl.org/net/OCRe/research.owl#>
PREFIX ocresd:   <http://purl.org/net/OCRe/study_design.owl#>
PREFIX skos:     <http://www.w3.org/2004/02/skos/core#>
PREFIX vcard:    <http://www.w3.org/2006/vcard/ns#>
PREFIX vitro-public: <http://vitro.mannlib.cornell.edu/ns/vitro/public#>
PREFIX vivo:     <http://vivoweb.org/ontology/core#>
PREFIX scires:   <http://vivoweb.org/ontology/scientific-research#>

#
# This example lists all faculty members for a given department - both by URI and name 
#
SELECT ?x ?organization ?z ?fnames ?lnames
WHERE {
  ?x a foaf:Person .
  ?x rdfs:label ?y .
  ?x vivo:relatedBy ?position .
  ?position rdfs:label ?positionLabel .
  ?position vivo:relates ?organization .
  ?organization rdfs:label "Engineering Physics" .
  ?x obo:ARG_2000028 ?tmp .
  ?tmp vcard:hasName ?z .
  ?z vcard:givenName ?fnames .
  ?z vcard:familyName ?lnames .
  ?z vcard:givenName "Leyla"
}
```
# Example 3: Search/Filter Example 1 output for a single user by first name
*Using the FILTER function to search*
Returned: individual's URI | organization URI | vcardname URI | First Name | Last Name
```sparql
PREFIX rdf:      <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs:     <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd:      <http://www.w3.org/2001/XMLSchema#>
PREFIX owl:      <http://www.w3.org/2002/07/owl#>
PREFIX swrl:     <http://www.w3.org/2003/11/swrl#>
PREFIX swrlb:    <http://www.w3.org/2003/11/swrlb#>
PREFIX vitro:    <http://vitro.mannlib.cornell.edu/ns/vitro/0.7#>
PREFIX bibo:     <http://purl.org/ontology/bibo/>
PREFIX c4o:      <http://purl.org/spar/c4o/>
PREFIX cito:     <http://purl.org/spar/cito/>
PREFIX event:    <http://purl.org/NET/c4dm/event.owl#>
PREFIX fabio:    <http://purl.org/spar/fabio/>
PREFIX foaf:     <http://xmlns.com/foaf/0.1/>
PREFIX geo:      <http://aims.fao.org/aos/geopolitical.owl#>
PREFIX mcmaster: <https://expertsdev.mcmaster.ca/ontology/mcmaster#>
PREFIX obo:      <http://purl.obolibrary.org/obo/>
PREFIX ocrer:    <http://purl.org/net/OCRe/research.owl#>
PREFIX ocresd:   <http://purl.org/net/OCRe/study_design.owl#>
PREFIX skos:     <http://www.w3.org/2004/02/skos/core#>
PREFIX vcard:    <http://www.w3.org/2006/vcard/ns#>
PREFIX vitro-public: <http://vitro.mannlib.cornell.edu/ns/vitro/public#>
PREFIX vivo:     <http://vivoweb.org/ontology/core#>
PREFIX scires:   <http://vivoweb.org/ontology/scientific-research#>

#
# This example lists all faculty members for a given department - both by URI and name 
#
SELECT ?x ?organization ?z ?fnames ?lnames
WHERE {
  ?x a foaf:Person .
  ?x rdfs:label ?y .
  ?x vivo:relatedBy ?position .
  ?position rdfs:label ?positionLabel .
  ?position vivo:relates ?organization .
  ?organization rdfs:label "Engineering Physics" .
  ?x obo:ARG_2000028 ?tmp .
  ?tmp vcard:hasName ?z .
  ?z vcard:givenName ?fnames .
  ?z vcard:familyName ?lnames .
  FILTER (regex(str(?fnames), "Leyla")) .
}
```
# Example 4: Search/Filter Example 1 output--search both first and last names
*Using the FILTER function to search*
Returned: individual's URI | organization URI | vcardname URI | First Name | Last Name
```sparql
PREFIX rdf:      <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs:     <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd:      <http://www.w3.org/2001/XMLSchema#>
PREFIX owl:      <http://www.w3.org/2002/07/owl#>
PREFIX swrl:     <http://www.w3.org/2003/11/swrl#>
PREFIX swrlb:    <http://www.w3.org/2003/11/swrlb#>
PREFIX vitro:    <http://vitro.mannlib.cornell.edu/ns/vitro/0.7#>
PREFIX bibo:     <http://purl.org/ontology/bibo/>
PREFIX c4o:      <http://purl.org/spar/c4o/>
PREFIX cito:     <http://purl.org/spar/cito/>
PREFIX event:    <http://purl.org/NET/c4dm/event.owl#>
PREFIX fabio:    <http://purl.org/spar/fabio/>
PREFIX foaf:     <http://xmlns.com/foaf/0.1/>
PREFIX geo:      <http://aims.fao.org/aos/geopolitical.owl#>
PREFIX mcmaster: <https://expertsdev.mcmaster.ca/ontology/mcmaster#>
PREFIX obo:      <http://purl.obolibrary.org/obo/>
PREFIX ocrer:    <http://purl.org/net/OCRe/research.owl#>
PREFIX ocresd:   <http://purl.org/net/OCRe/study_design.owl#>
PREFIX skos:     <http://www.w3.org/2004/02/skos/core#>
PREFIX vcard:    <http://www.w3.org/2006/vcard/ns#>
PREFIX vitro-public: <http://vitro.mannlib.cornell.edu/ns/vitro/public#>
PREFIX vivo:     <http://vivoweb.org/ontology/core#>
PREFIX scires:   <http://vivoweb.org/ontology/scientific-research#>

#
# This example lists all faculty members for a given department - both by URI and name 
#
SELECT ?x ?organization ?z ?fnames ?lnames
WHERE {
  ?x a foaf:Person .
  ?x rdfs:label ?y .
  ?x vivo:relatedBy ?position .
  ?position rdfs:label ?positionLabel .
  ?position vivo:relates ?organization .
  ?organization rdfs:label "Engineering Physics" .
  ?x obo:ARG_2000028 ?tmp .
  ?tmp vcard:hasName ?z .
  ?z vcard:givenName ?fnames .
  ?z vcard:familyName ?lnames .
  FILTER (regex(str(?fnames), "Leyla") || regex(str(?lnames), "Leyla")) .
}
```
# Example 5: Search/Filter Example 1 output--search both first and last names using partial strings
*Using the FILTER function to search*
Returned: individual's URI | organization URI | vcardname URI | First Name | Last Name
```sparql
PREFIX rdf:      <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs:     <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd:      <http://www.w3.org/2001/XMLSchema#>
PREFIX owl:      <http://www.w3.org/2002/07/owl#>
PREFIX swrl:     <http://www.w3.org/2003/11/swrl#>
PREFIX swrlb:    <http://www.w3.org/2003/11/swrlb#>
PREFIX vitro:    <http://vitro.mannlib.cornell.edu/ns/vitro/0.7#>
PREFIX bibo:     <http://purl.org/ontology/bibo/>
PREFIX c4o:      <http://purl.org/spar/c4o/>
PREFIX cito:     <http://purl.org/spar/cito/>
PREFIX event:    <http://purl.org/NET/c4dm/event.owl#>
PREFIX fabio:    <http://purl.org/spar/fabio/>
PREFIX foaf:     <http://xmlns.com/foaf/0.1/>
PREFIX geo:      <http://aims.fao.org/aos/geopolitical.owl#>
PREFIX mcmaster: <https://expertsdev.mcmaster.ca/ontology/mcmaster#>
PREFIX obo:      <http://purl.obolibrary.org/obo/>
PREFIX ocrer:    <http://purl.org/net/OCRe/research.owl#>
PREFIX ocresd:   <http://purl.org/net/OCRe/study_design.owl#>
PREFIX skos:     <http://www.w3.org/2004/02/skos/core#>
PREFIX vcard:    <http://www.w3.org/2006/vcard/ns#>
PREFIX vitro-public: <http://vitro.mannlib.cornell.edu/ns/vitro/public#>
PREFIX vivo:     <http://vivoweb.org/ontology/core#>
PREFIX scires:   <http://vivoweb.org/ontology/scientific-research#>

#
# This example lists all faculty members for a given department - both by URI and name 
#
SELECT ?x ?organization ?z ?fnames ?lnames
WHERE {
  ?x a foaf:Person .
  ?x rdfs:label ?y .
  ?x vivo:relatedBy ?position .
  ?position rdfs:label ?positionLabel .
  ?position vivo:relates ?organization .
  ?organization rdfs:label "Engineering Physics" .
  ?x obo:ARG_2000028 ?tmp .
  ?tmp vcard:hasName ?z .
  ?z vcard:givenName ?fnames . 
  ?z vcard:familyName ?lnames .
  FILTER (regex(str(?fnames), "Cas") || regex(str(?lnames), "Cas")) .
}
```
# Example 6: Check an individual's profile to see if they have an uploaded image
```sparql
PREFIX rdf:      <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs:     <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd:      <http://www.w3.org/2001/XMLSchema#>
PREFIX owl:      <http://www.w3.org/2002/07/owl#>
PREFIX swrl:     <http://www.w3.org/2003/11/swrl#>
PREFIX swrlb:    <http://www.w3.org/2003/11/swrlb#>
PREFIX vitro:    <http://vitro.mannlib.cornell.edu/ns/vitro/0.7#>
PREFIX bibo:     <http://purl.org/ontology/bibo/>
PREFIX c4o:      <http://purl.org/spar/c4o/>
PREFIX cito:     <http://purl.org/spar/cito/>
PREFIX event:    <http://purl.org/NET/c4dm/event.owl#>
PREFIX fabio:    <http://purl.org/spar/fabio/>
PREFIX foaf:     <http://xmlns.com/foaf/0.1/>
PREFIX geo:      <http://aims.fao.org/aos/geopolitical.owl#>
PREFIX mcmaster: <https://expertsdev.mcmaster.ca/ontology/mcmaster#>
PREFIX obo:      <http://purl.obolibrary.org/obo/>
PREFIX ocrer:    <http://purl.org/net/OCRe/research.owl#>
PREFIX ocresd:   <http://purl.org/net/OCRe/study_design.owl#>
PREFIX skos:     <http://www.w3.org/2004/02/skos/core#>
PREFIX vcard:    <http://www.w3.org/2006/vcard/ns#>
PREFIX vitro-public: <http://vitro.mannlib.cornell.edu/ns/vitro/public#>
PREFIX vivo:     <http://vivoweb.org/ontology/core#>
PREFIX scires:   <http://vivoweb.org/ontology/scientific-research#>
SELECT ?individualUri ?name ?position ?faculty  ?email ?phone ?imageFile
WHERE
{
  ?individualUri a foaf:Person .
  ?individualUri rdfs:label ?name .
  ?individualUri vivo:relatedBy ?positionUri .
  ?positionUri rdfs:label ?position .
  ?individualUri obo:ARG_2000028 ?vi .
  ?vi vcard:hasEmail ?emailcard .
  ?emailcard vcard:email ?email .
  ?vi vcard:hasTelephone ?tel .
  ?tel vcard:telephone ?phone .
  ?positionUri vivo:relates ?org .
  ?org rdfs:label ?faculty .
  OPTIONAL {
    ?individualUri vitro-public:mainImage ?image .
    ?image vitro-public:filename ?imageFile 
  }
  FILTER(regex(?name, "Leyla")) .
}
```

Example 7. Return all people in VIVO, in the case that you have lost all faculty members
```sparql
PREFIX rdf:      <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs:     <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd:      <http://www.w3.org/2001/XMLSchema#>
PREFIX owl:      <http://www.w3.org/2002/07/owl#>
PREFIX swrl:     <http://www.w3.org/2003/11/swrl#>
PREFIX swrlb:    <http://www.w3.org/2003/11/swrlb#>
PREFIX vitro:    <http://vitro.mannlib.cornell.edu/ns/vitro/0.7#>
PREFIX bibo:     <http://purl.org/ontology/bibo/>
PREFIX c4o:      <http://purl.org/spar/c4o/>
PREFIX cito:     <http://purl.org/spar/cito/>
PREFIX event:    <http://purl.org/NET/c4dm/event.owl#>
PREFIX fabio:    <http://purl.org/spar/fabio/>
PREFIX foaf:     <http://xmlns.com/foaf/0.1/>
PREFIX geo:      <http://aims.fao.org/aos/geopolitical.owl#>
PREFIX mcmaster: <https://expertsdev.mcmaster.ca/ontology/mcmaster#>
PREFIX obo:      <http://purl.obolibrary.org/obo/>
PREFIX ocrer:    <http://purl.org/net/OCRe/research.owl#>
PREFIX ocresd:   <http://purl.org/net/OCRe/study_design.owl#>
PREFIX skos:     <http://www.w3.org/2004/02/skos/core#>
PREFIX vcard:    <http://www.w3.org/2006/vcard/ns#>
PREFIX vitro-public: <http://vitro.mannlib.cornell.edu/ns/vitro/public#>
PREFIX vivo:     <http://vivoweb.org/ontology/core#>
PREFIX scires:   <http://vivoweb.org/ontology/scientific-research#>

SELECT ?x 
WHERE {
	?x a mcmaster:Internal .
    FILTER (!regex(str(?x), "institutional")) .

}
```
