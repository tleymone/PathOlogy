# PathOlogy

UTC project to create an onthology around diseases, done in 2021.

## Objectif de l'Ontologie
Cette ontologie aura pour but de rassembler les connaissances autour de l'imagerie médicale afin de proposer, à un client qui renseigne des caractéristiques sur une image médicale qu'il a analysé et des données sur ce l'état de santé du patient.

## Cadre de l'Ontologie
On s'intéressera pour notre ontologie aux scanners pulmonaires, c'est à dire à la recherche de blessures, des maladies pulmonaires comme la tuberculose ou des tumeurs par un scanner.

## Contexte/Exemples 
On cherche donc à connaître les variantes anatomiques et/ou pathologiques après analyse d'une imagerie médicale. On peut donc répondre a ces questions :  
- J'ai un scanner avec une certaine tache opaque dans mon poumons droit, quelle peut être la pathologie ?
- J'ai un scanner normal avec un patient qui a mal à son thorax, qu'est ce que ça pourrait être ?

## A faire :  



## Interrogation :  
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>  
PREFIX owl: <http://www.w3.org/2002/07/owl#>  
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>  
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>  
PREFIX : <http://www.semanticweb.org/thomas/ontologies/2021/11/untitled-ontology-3#>  
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>  


### Quelles sont les parties du poumon ?  

SELECT ?x  
	WHERE {   
  ?x :faitPartieDe ?y .  
  ?y rdfs:label "poumon"  
}  

### Quelles sont les pathologies listées dans l’ontologie ?  

SELECT ?pathologie  
	WHERE {   
   ?pathologie a ?x .  
   ?x rdfs:subClassOf ?y .  
   ?y rdfs:label "pathologie"   
}  

### Quelles sont les pathologies qui ont pour symptômes de la fièvre ?  

SELECT ?pathologie  
	WHERE {   
   ?pathologie a ?x .  
   ?x rdfs:subClassOf ?y .  
   ?y rdfs:label "pathologie" .  
    ?pathologie :aPourSymptômes ?sym .  
    ?sym rdfs:label "fièvre"  
}  

### Quelles sont les pathologies qui ont pour symptômes de la fièvre et de la toux ?  

SELECT ?pathologie  
	WHERE {   
   ?pathologie a ?x .  
   ?x rdfs:subClassOf ?y .  
   ?y rdfs:label "pathologie" .  
    ?pathologie :aPourSymptômes ?sym1 .  
    ?pathologie :aPourSymptômes ?sym2 .  
   ?sym1 rdfs:label "fièvre" .  
    ?sym2 a :Toux  
}  

### Quelles sont les pathologies qui sont situées dans la plèvre, avec des nodules et de la fatigue ?  

SELECT DISTINCT ?pathologie  
	WHERE {   
   ?pathologie a ?x .  
   ?x rdfs:subClassOf ?y .  
   ?y rdfs:label "pathologie" .  
    ?pathologie :estSituéDans ?loc .  
    ?loc rdfs:label "plèvre" .  
    ?pathologie :aPourSymptômes ?sym1 .  
    ?pathologie :aPourSymptômes ?sym2 .  
   ?sym1 rdfs:label "fatigue" .  
    ?sym2 rdfs:label "nodule"  
}  



## Sources :
https://disease-ontology.org/  
https://www.loterre.fr/skosmos/TSP/fr/  
https://meshb.nlm.nih.gov/treeView  
https://uts.nlm.nih.gov/uts/umls/home  
https://bioportal.bioontology.org/ontologies/TOP-MENELAS/?p=mappings  
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4485195/  
http://bioportal.lirmm.fr/  
https://www.e-cancer.fr/Patients-et-proches/Les-cancers/Tumeurs-du-cerveau/Les-tumeurs-du-cerveau/Types-de-tumeurs  

http://www.sfls.aei.fr/ckfinder/userfiles/files/Formations/JourneesNationales/2015/presentations/J-CHARLET.pdf  
https://intd.cnam.fr/medias/fichier/charlet__1180706017965.pdf
