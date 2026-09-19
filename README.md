BioDivOnto (Biodiversity Ontology)
Data Collected from the Okavango Region of Botswana
An OWL ontology that links community livelihoods, climate information and prediction, and biological indicators in one shared vocabulary. It is intended to help researchers, developers and practitioners describe, integrate and query data on how climate variability, biodiversity and human activity interact at the level of households and villages.
Status: in active development. Terms, names and axioms may change between versions.
Overview
Climate change, biodiversity loss and rural livelihoods are usually studied with separate datasets and separate vocabularies. This ontology provides a common structure for:
•	describing the assets, activities and vulnerabilities that make up a livelihood (crop farming, livestock rearing, natural resource harvesting, off-farm work);
•	recording human–wildlife conflict, such as predator livestock loss and wildlife crop damage, together with the management responses to them;
•	representing climate information services: weather tracking, spatial representation, dissemination, tailoring and user interfaces;
•	documenting the climate prediction workflow: data, features, targets, pre-processing, prediction models, evaluation metrics and validation methods;
•	capturing community perceptions and indigenous knowledge alongside measured climate data.
Structure
The ontology has four top-level modules.
Module	What it covers	Example subclasses
livelihoods	Livelihood assets and capitals, activities, adaptive capacity, vulnerability, institutions and stakeholders	humanCapital, socialCapital, naturalCapital, physicalCapital, financialCapital, cropFarming, livestockRearing, vulnerabilityContext, indigenousKnowledge
climateInformation	Climate and hazard information, its spatial context and how it reaches users	weatherTracking, hydrosphere, realm, spatialRepresentation, dissemination, tailoring, userInterface, droughtImpact, wildlifeCropDamage, predatorLivestockLoss
climatePredictors	Data-driven forecasting, community climate perceptions and monitoring	data, features, target, preProcessing, predictionModel, evaluationMetrics, validationMethods, forecasting, climateChangePerception
biologicalIndicators	Biological and environmental entities that indicate ecosystem state	habitat, environmentalFeature, environmentalProcess, phenomena, substance, entity
At a glance
Element	Count
Classes	82
Object properties	38 (19 inverse pairs)
Datatype properties	283
Individuals	0
Object properties connect concepts within and across modules, for example livelihoods consistOf humanActivity, climatePredictors predicts forecasting, biologicalIndicators indicates environmentalProcess and climateInformation isPresentedThrough userInterface. Most object properties have a declared inverse, and some carry characteristics such as functional or asymmetric.
Datatype properties hold the measurable attributes of each concept, such as identifiers, names, dates, counts (for example livestock head counts), scores and model performance values. Ranges are mostly xsd:string, with xsd:float, xsd:integer and xsd:dateTime where a numeric or temporal value is needed.
Files
File	Description
Biodiversity.rdf	The ontology in RDF/XML
README.md	This file
LICENSE / LICENSE-NOTE.md	License text and reuse guidance
Getting started
Ontology IRI
http://www.semanticweb.org/tshepisolm/ontologies/2026/5/BioDivOnto
Terms use the namespace <ontology IRI>#, for example ... BioDivOnto #livelihoods.
Open in Protégé
1.	Download Biodiversity.rdf.
2.	In Protégé, choose File → Open and select the file.
Load in Python (rdflib)
from rdflib import Graph

g = Graph()
g.parse("Biodiversity.rdf", format="xml")
print(len(g), "triples")
Query with SPARQL
List everything under the livelihoods module:
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX bio:  <http://www.semanticweb.org/tshepisolm/ontologies/2026/5/ BioDivOnto #>

SELECT ?class ?comment
WHERE {
  ?class rdfs:subClassOf bio:livelihoods .
  OPTIONAL { ?class rdfs:comment ?comment }
}
ORDER BY ?class
List the datatype properties defined for livelihoods and their ranges:
PREFIX owl:  <http://www.w3.org/2002/07/owl#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX bio:  <http://www.semanticweb.org/tshepisolm/ontologies/2026/5/ BioDivOnto #>

SELECT ?property ?range
WHERE {
  ?property a owl:DatatypeProperty ;
            rdfs:domain bio:livelihoods ;
            rdfs:range  ?range .
}
ORDER BY ?property
Reuse in your own ontology
Import the ontology, or reuse individual classes and properties by their IRIs. The default IRI above may not resolve online, so point your import at the file itself, for example the raw GitHub URL of Biodiversity.rdf.
Conventions
•	Classes, object properties and datatype properties are named in lowerCamelCase (adaptiveCapacity, hasComponent, activityName).
•	Identifier properties end in Id (activityId, habitatId).
•	Object properties are declared in inverse pairs (consistOf / consists, predicts / predictedBy).
•	Terms carry an rdfs:label and, where defined, an rdfs:comment giving a plain-language definition.
Quality checks
The ontology is evaluated with the OOPS! (OntOlogy Pitfall Scanner!) pitfall scanner, and identified pitfalls are addressed between versions.
Roadmap
•	[ ] Add definitions (rdfs:comment) for all remaining classes
•	[ ] Add individuals and example data for [study area / dataset]
•	[ ] Publish a stable, resolvable ontology IRI
•	[ ] Add mappings to existing vocabularies such as [e.g. ENVO, SOSA/SSN, DwC]
How to cite
If you use this ontology in your work, please cite it as:
Dr Tshepiso L. Mokgetse. (2026). BioDivOnto (Version 1) [OWL ontology]. GitHub. https://github.com/tmokgetse/BioDivOnto.git
Contributing
Issues and pull requests are welcome. If you propose new terms, please follow the naming conventions above, include a label and a definition, and, where possible, run the updated file through OOPS! before submitting.
License
This ontology is released under the Creative Commons Attribution 4.0 International (CC BY 4.0) license. You may share and adapt it, including for commercial use, as long as you give appropriate credit, link to the license and indicate any changes. See LICENSE-NOTE.md for suggested attribution wording.
Contact
Dr Tshepiso L. Mokgetse, Botswana School of Business Sciences · tmokgetse@gmail.com

