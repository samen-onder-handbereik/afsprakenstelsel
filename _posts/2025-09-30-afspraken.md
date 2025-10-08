---
title: Afspraken
author: lg
date: 2025-09-29
category: Jekyll
layout: post
---

Technische afspraken
-------------

> ##### Concept
{: .block-danger }

Deze afspraken zijn van toepassing voor de deelnemers aan het afsprakenstelsel. Ze zijn gericht op het realiseren van een gedistribueerd stelsel met zo min mogelijk afhankelijkheden en koppelingen. De technische afspraken zijn onderverdeeld in drie categorieën: Algemeen, Semantiek gerelateerd, Gebeurtenissen gerelateerd en REST API gerelateerd.

### Algemeen
1. Er is sprake van gefedereerde gedistribueerde systemen, waarbij monolithische centralistische concepten worden vervangen door oplossingen die gekenmerkt worden door het terugdringen van afhankelijkheden.
2. Er worden alleen centrale gedeelde (keten)voorzieningen gerealiseerd als dat nodig is.

### Semantiek gerelateerd
3. Binnen het Jeugd, Zorg en Veiligheiddomein wordt het Metamodel voor Informatiemodellering (MIM) gehanteerd en beheerd als kader voor het opstellen van informatiemodellen.


### Gebeurtenissen gerelateerd
4. Voor het verzamelen, opslaan en distribueren van grote hoeveelheden gebeurtenisgegevens (events) is een centrale Event Hub nodig binnen het Stelsel. Een Event Hub is een gedistribueerd streamingplatform dat wordt gebruikt voor het verwerken en beheren van realtime datastreams (van gebeurtenissen/notificaties).
5. Er wordt een Ketenindex gerealiseerd, die customer journeys of ‘tijdlijnen’ mogelijk maakt. Omdat relevante gebeurtenissen gevonden kunnen worden, kunnen deze op een tijdlijn worden geplaatst. Het kunnen volgen (track en trace) van personen, objecten en concepten (en procesgangen) maakt integrale beelden mogelijk. Omdat het een verwijzing betreft kan eventueel een verdiepingsvraag worden gesteld.
6. Events (gebeurtenissen) ten behoeve van onder andere de ketenindex (en daarmee tijdslijnen) slaan we op in een centrale Event Store. Een Event Store is een gespecialiseerde database die gebeurtenissen (events) opslaat in een onveranderlijke, chronologische volgorde. Deze biedt daarmee een volledige historische weergave van alle veranderingen.
7. De Event Store maakt net als de Event Hub deel uit van CORV2.
8. De Event Store levert naast customer journeys of ‘tijdlijnen’ ook ondersteuning ten behoeve van data lineage / data provenance.
9. Binnen CORV2 hanteren we CQRS (Command Query Responsibility Segregation), oftewel het scheiden van het schrijf- en lees-datamodel.
10. Voor gebeurtenissen-uitwisseling in CORV2 context hanteren we een ontkoppelde variant via een REST API layer (API Proxy) om een toestand of gebeurtenis op te vragen, dus een pull model (en niet het native publish-subscribe model, waarbij producenten events publiceren en consumenten deze events kunnen consumeren via native interfaces).
11. Binnen de keten hanteren we een gestandaardiseerd Event Datamodel.

### REST API gerelateerd
12. REST API calls binnen de keten verlopen decentraal, dus direct tussen partijen zonder tussenkomst van een centrale component. Als centrale component is slechts een API Catalog beschikbaar, deze is om API’s vindbaar te maken en daarmee ondersteunend van aard.
13. REST API’s verbonden aan Samenwerkfuncties en Samenwerkpatronen volgen de specificaties daarvan.


### Toelichting CQRS:
CQRS (Command Query Responsibility Segregation) is een architecturaal patroon dat lees- en schrijfoperaties in een systeem scheidt. Het belangrijkste principe is dat methoden die de status van een systeem wijzigen (commands en events) gescheiden worden van methoden die data opvragen (queries).

CQRS is een belangrijke stap in event-gedreven oplossingen om verschillende redenen:
- Het verbetert de schaalbaarheid door lees- en schrijfworkloads onafhankelijk te kunnen schalen.
- Het maakt optimalisatie mogelijk van datamodellen voor specifieke use cases, met aparte schema's voor lezen en schrijven.
- Het vereenvoudigt de integratie met event sourcing, waarbij alle statuswijzigingen als events worden opgeslagen.
- Het ondersteunt betere prestaties en flexibiliteit in complexe domeinen door gespecialiseerde lees- en schrijfmodellen te gebruiken.
- Het verbetert de beveiliging door de toegang tot schrijfoperaties beter te kunnen controleren.

Als een dergelijke CQRS data bron wordt opgenomen in bijvoorbeeld een NoSQL oplossing als graph ontstaan er meerdere voordelen:
- Verbeterde zoekbaarheid: Gegevens zijn eenvoudiger te vinden door geoptimaliseerde opslag en indexering.
- Flexibele datarelaties: Alternatieve dataformaten zoals NoSQL en graph databases maken het leggen en bevragen van complexe relaties tussen gegevens eenvoudiger.
- Snellere query-uitvoering: Geoptimaliseerde indexering zorgt voor efficiënte zoekopdrachten, inclusief mogelijkheden voor full-text zoeken, fuzzy search en geavanceerde zoekfuncties.
- Kunstmatige intelligentie en machine learning: AI en machine learning kunnen patronen en relaties in grote datasets ontdekken, voorspellingen doen over systeemuitval of prestatieknelpunten, en data-gedreven beslissingen ondersteunen.
- Efficiëntere analyse: Het gebruik van flexibele dataformaten vergemakkelijkt het analyseren en verbinden van gegevens, waardoor diepgaandere inzichten mogelijk zijn.

Toelichting ontkoppeling via REST API, ook voor events:
Gebruik van een API layer / API Proxy ontkoppelt en voorkomt het implementeren van business logica op een centrale plek (dus in CORV2). Het is een generieke best practice geen business logica op een centrale plek te realiseren en zeker niet  binnen een federatieve omgeving. Door een REST API-koppelvlak te implementeren, creëren organisaties een uniforme interface voor het lezen en schrijven van events. Dit bevordert de consistentie in dataverwerking en vereenvoudigt de integratie met diverse systemen en applicaties. Het API-koppelvlak fungeert als een abstractielaag, waardoor onderliggende complexiteiten van event storage en retrieval worden verborgen voor de consumenten van de API. Veelal gaan we uit van een request / response REST API koppelvlak. Een API kan ook een event koppelvlak bezitten. REST API’s kunnen geïntegreerd zijn in Even Brokers. REST API’s kunnen zcih registeren op webhooks om asynchrone notificaties te ontvangen zodat een polling mechanisme niet nodig is.     

### Toelichting Graph database:
Wanneer een graph database wordt gebruikt als event store, ontstaan er enkele unieke voordelen:
- Rijke relaties: Graph databases kunnen complexe relaties tussen events en entiteiten efficiënt modelleren en bevragen.
- Flexibele queries: Het maakt geavanceerde traversals en patroonherkenning mogelijk tussen gerelateerde events.
- Schaalbaarheid: Graph databases presteren goed bij het verwerken van grote hoeveelheden onderling verbonden data.
- Contextbehoud: De graph-structuur helpt bij het behouden van de context rond events.

Toelichting Data lineage / Data provenance:
Data lineage of data provenance is het vastleggen van de volledige levenscyclus van gegevens, van hun oorsprong tot hun huidige staat, en het is belangrijk om verschillende redenen. Ten eerste helpt het bij het verifiëren van de datakwaliteit en betrouwbaarheid door een duidelijke geschiedenis van transformaties te bieden. Daarnaast maakt het de dataverwerking transparant en houdt het gegevensverwerkers verantwoordelijk voor hun acties, wat bijdraagt aan de integriteit van gegevens.

Bovendien ondersteunt data lineage organisaties bij het voldoen aan wettelijke en industriële standaarden door de nauwkeurigheid en legitimiteit van gegevens te waarborgen. Het stelt ontwikkelaars en data-analisten ook in staat om de oorsprong en transformatie van gegevens te traceren, waardoor fouten efficiënt kunnen worden opgespoord en gecorrigeerd. Dit proces helpt verder bij het opbouwen van vertrouwen in de gegevens door de herkomst en authenticiteit ervan te bevestigen. Tot slot bevordert data lineage de reproduceerbaarheid van onderzoeksresultaten door een gedetailleerde trail van gegevensbewerkingen te bieden. Hierdoor kunnen organisaties de integriteit van hun gegevens waarborgen, besluitvorming ondersteunen en voldoen aan steeds strengere eisen op het gebied van gegevensbeheer en privacy.

Event stores passen goed bij data lineage of data provenance om verschillende redenen:
- Chronologische vastlegging: Event stores leggen gebeurtenissen chronologisch vast, wat perfect aansluit bij het traceren van de herkomst en transformatie van data over tijd.
- Onveranderlijke geschiedenis: Events worden opgeslagen in een onveranderlijk formaat, waardoor een betrouwbare en volledige historische weergave van alle datawijzigingen behouden blijft.
- Gedetailleerde tracking: Elke datawijziging wordt als een afzonderlijk event opgeslagen, wat een zeer gedetailleerd inzicht geeft in hoe data is getransformeerd en verplaatst.
- Reconstructie van toestanden: Door events sequentieel af te spelen, kan de toestand van data op elk willekeurig moment in de geschiedenis worden gereconstrueerd.
- Foutcorrectie en audittrail: Event stores bieden mechanismen voor foutcorrectie zonder de originele events te wijzigen, wat cruciaal is voor nauwkeurige data lineage.
- Flexibiliteit in analyse: De eventgebaseerde structuur maakt het gemakkelijk om complexe queries uit te voeren en datastromen te analyseren, wat essentieel is voor data provenance.

### Toelichting Event Datamodel:
Het is essentieel dat er een gestandaardiseerd keten Event Datamodel toegepast wordt en dat model wordt beheerd. Standaardisatie van het event data model biedt verschillende voordelen voor organisaties die event sourcing toepassen.

Ten eerste zorgt een gestandaardiseerd event datamodel voor consistentie en interoperabiliteit binnen en tussen systemen. Dit maakt het gemakkelijker om events uit te wisselen, te verwerken en te interpreteren, ongeacht waar ze zijn gegenereerd of worden gebruikt. Standaardisatie bevordert ook de schaalbaarheid en flexibiliteit van event-gebaseerde systemen, omdat nieuwe componenten of diensten eenvoudiger kunnen worden geïntegreerd wanneer ze een gemeenschappelijk datamodel volgen.

Daarnaast is het juiste beheer van het event data model cruciaal voor de langetermijnwaarde en bruikbaarheid van de opgeslagen events. Events zijn immers de onveranderlijke feiten die de basis vormen van het systeem. Een goed beheerd datamodel zorgt ervoor dat events begrijpelijk en bruikbaar blijven, zelfs als de systemen en processen eromheen evolueren. Dit is vooral belangrijk omdat events vaak worden gebruikt om de volledige geschiedenis van een systeem te reconstrueren of om complexe analyses uit te voeren.

Het beheer van het event data model moet rekening houden met de dynamische aard van bedrijfsprocessen en datarelaties. Entiteiten en hun relaties kunnen veranderen over tijd, en het datamodel moet flexibel genoeg zijn om deze veranderingen te accommoderen zonder de integriteit van historische data te compromitteren. Dit vereist een zorgvuldige aanpak van datamanagement, waarbij veranderingen in het model worden gedocumenteerd en backward compatibility wordt gewaarborgd.

Door een gestandaardiseerd en goed beheerd event data model te hanteren, kunnen organisaties de volle potentie van event sourcing benutten. Het stelt hen in staat om betrouwbare audit trails te maintainen, complexe analyses uit te voeren, en systemen te bouwen die robuust en aanpasbaar zijn aan veranderende zakelijke behoeften.
