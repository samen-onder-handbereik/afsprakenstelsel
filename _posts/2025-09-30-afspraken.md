---
title: Afspraken
author: lg
date: 2025-09-29
category: Jekyll
layout: post
---

Realisatie afspraken
-------------

> ##### Concept
{: .block-danger }

Niet alle beschreven functionaliteiten en technische voorzieningen kunnen tegelijk gerealiseerd worden. De realisatie zal in fasen worden uitgevoerd waarbij steeds naar een vastgesteld en afgesproken plateau wordt gewerkt. 

### Plateau 1 afspraken
Toegang
1. We passen voor dit plateau minimaal de huidige authenticatie op organisatieniveau (Organisatie identifier en certficate) toe. Voor latere scopes onderzoeken de beweging naar nieuwere vormen van identifier, certficate en contract authenticatie (FSC), authenticatie op niveau persoon/professional en daarmee o.a. OIDC/Oauth, FTV, DigiD en Wallet, en combinatie daarvan (FSC + FTV).
2. Bij toegangsverlening op basis van Organisatie identifier en certficate wordt OIN gebruikt als identifier en uitsluitend PKIoverheid certificaten.

Toegang burgerportaal
1. Bij toegangsverlening voor burgers, denk aan het burgerportaal, gebruiken we DigiD waarbij de authentiserende persoon over een BSN moet beschikken.
2. Voor de te realiseren samenwerkfuncties binnen dit plateau gerelateerd aan het burgerportaal is  betrouwbaarheidsniveau voor toegang “Substantieel” voldoende. Samenwerkfuncties die een hoger niveau vereisen vallen buiten dit plateau.
3. In de context van DigiD/eherkenning passen we SAML toe en stappen (in hogerliggende plateua’s) naar OIDC/Oauth over zodra dat wordt ondersteund door DigiD/eherkenning
4. Binnen dit plateau kan niet worden uitgegaan dat de identiteit van de persoon die het portaal gebruikt doorgeven kan worden bij inzage bij ketenpartners. Er wordt onderzocht hoe dit gerealiseerd kan worden in situatie waar dit nodig is en is toegestaan binnen opvolgende plateau’s.
5. We gebruiken voor dit plateau (voor het burgerportaal) de gezagsinformatie van de BRP en dienen Gezagsdiensten te zijn om dat te kunnen en mogen. Gezagsdiensten zijn bestuursorganen en enkele daartoe aangewezen instanties, die rechtmatig toegang hebben tot de BRP volgens de Wet BRP en het Besluit BRP. 

Gebeurtenissen
1. Binnen dit plateau werken we met gebeurtenissen die voor alle ketenpartijen toegankelijk zijn en mogen zijn. Voor latere plateau’s onderzoeken we autorisatie/abonneren op bepaalde gebeurtenissen/topics.
2. De gebeurtenissen bevatten genoeg informatie om een inzage te kunnen doen via het (REST API) inzage patroon. Zodoende wordt dus de toegangsverlening daarvan hergebruikt en is de informatie alleen zichtbaar voor partijen met toegang tot die informatie.
3. Voor dit plateau vertrekken we met in de gebeurtenissen opgenomen de persoon/BSN waar de gebeurtenis betrekking op heeft. Voor latere plateau’s onderzoeken we of pseudonimisering, etc. meerwaarde heeft en noodzakelijk is.
4. We gaan in plateau uit van één centrale Event Provenance Store en Event Hub. Voor latere scopes onderzoeken we of er nut en noodzaak is om in het stelsel meerdere event stores op te nemen.
5. Binnen dit plateau realiseren via filtering dat waar dat wenselijk is gebeurtenissen niet meer bevraagd kunnen worden.

Architectuur afspraken
-------------

> ##### Concept
{: .block-danger }

1. Het jeugd, zorg en veiligheidsdomein vormt één domein met één bounded context. Een domein is afgebakend, autonoom gebied is waarin één coherent domeinmodel geldt en alle partijen dat model hanteren.
2. De informatievoorziening in het jeugd, zorg en veiligheidsdomein is gefedereerd en centrale voorzieningen worden alleen toegepast als dat nodig is.
3. Het jeugd, zorg en veiligheidsdomein kent een uniforme dienstverlening. Deze uniforme benadering waarborgt consistentie, interoperabiliteit en gelijkwaardigheid binnen het netwerk. Elke deelnemer, ongeacht grootte of specifieke context, neemt deel vanuit zijn eigen rol in dit samenwerkverband en verbind zich aan het leveren van deze vastgestelde diensten volgens gezamenlijk overeengekomen standaarden en kwaliteitsnormen. Zie het samenwerkproces, de samenwerkfuncties en de samenwerkpatronen.
4. Binnen het jeugd, zorg en veiligheidsdomein wordt dezelfde taal gesproken. Uit het uitgangspunt “domein oriëntatie” volgt logisch dat uitgegaan wordt van één gemeenschappelijk semantisch, schematisch en syntactisch model. Populair gezegd spreken we, binnen het samenwerkverband, dezelfde taal.
5. Informatie wordt waar mogelijk en zinvol eenmalig opgeslagen en meervoudig gebruikt. Het kernidee is dat er voor elke soort informatie één leidende bron bestaat, één verantwoordelijke. In plaats van gegevens te kopiëren of over te nemen, wordt informatie steeds opnieuw opgehaald uit deze originele bron, één verantwoordelijke partij. Let wel, een verantwoordelijke partij kan een andere partij de bevoegdheid gegeven om deze gegevens beschikbaar te maken. Eenmalig opslaan en meervoudig gebruik zorgt er voor dat: de gegevens altijd up-to-date zijn, meer zekerheid over de juistheid van gegevens bestaat, er geen inconsistenties ontstaan door verouderde kopieën; we uitgaan van één actuele en historische waarheid, de integriteit van de data beter gewaarborgd blijft.
6. Gegevens zijn voorzien van context. Gegevens (in welke vorm dan ook) zijn altijd voorzien van contextuele gegevens. Door consequent context te koppelen aan gegevens wordt een robuuste basis voor geïnformeerde besluitvorming en effectieve data-gedreven processen gelegd. Dit zorgt voor een beter begrip, verhoogt de betrouwbaarheid en bevordert het juiste gebruik van de data.
7. Het jeugd, zorg en veiligheidsdomein is een gedistribueerd systeem, of kan minimaal als zodanig worden gezien, met een eventual consistency kenmerk naast availability en partition tolerance (zie het CAP theorem).
8. De bronhouder geeft toegang tot gegevens (op  basis van afspraken). In beginsel moet elke bronhouder autonoom de voorwaarden bepalen voor toegang tot zijn gegevens via hun API’s. Deze benadering waarborgt de integriteit, veiligheid en het juiste gebruik van data. Gebruikers die toegang wensen tot deze gegevens, committeren zich aan het naleven van de gestelde voorwaarden. Dit creëert een transparant en verantwoord ecosysteem voor gegevensuitwisseling, waarbij de rechten en plichten van zowel bronhouders als gebruikers duidelijk zijn gedefinieerd en gerespecteerd.
9. Flexibiliteit en aanpasbaarheid (waar dat kan) waardoor ingespeeld kan worden op veranderingen en nieuwe wensen of vereisten. Door: een modulaire opbouw, een business agnostische ICT benadering, een event gedreven benadering, real-time reactievermogen, afstemming op bedrijfsprocessen, API-first benadering, configureerbare workflows.


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



