---
title: Ketenvoorzieningen
author: lg
date: 2025-09-29
category: Jekyll
layout: post
---

> ##### Concept
{: .block-danger }

Binnen de keten leveren de verschillende partijen diensten. Er is sprake van een federatief landschap. Idealiter zijn er geen centrale voorzieningen, of wel ketenvoorzieningen, nodig. In die zin volgen we een zelfde uitgangspunt als het Federatief Datastelsel (FDS): “afspraken boven standaarden boven voorzieningen”. Echter zullen ketenvoorzieningen niet te voorkomen zijn. Zie ook CORV. Voor de werking van het stelsel zullen de volgende ketenvoorzieningen nodig zijn:
1. Event Provenance Store en Event Hub
2. Diensten Catalogus (optioneel)
3. API Catalogus (optioneel)

Daar waar “optioneel” is aangeven, is geen sprake van een noodzaak, maar van een potentieel nut. Dit type voorzieningen zal niet in het eerste plateau worden gerealiseerd, maar mogelijk in opvolgende plateau’s. 


Event Provenance Store en Event Hub
-------------

> ##### Concept
{: .block-danger }

Om relevante gebeurtenissen te kunnen vinden en customer journey of tijdlijnen mogelijk te maken is een ketenindex nodig en de gestructureerde (graph based) opslag van events in een onveranderlijke chronologische volgorde. Dus een voorziening die dit levert voor binnen keten uitgewisselde gebeurtenissen of wel een Event Provenance Store. Er moeten in grote hoeveel heden gebeurtenisgegevens (events) kunnen worden ontvangen, gedistribueerd, opgeslagen in logs/topics, etc. Er is hiervoor een streamingplatform nodig, we noemen dat de Event Hub. Merk op dat de ketenpartners vaak ook zullen beschikken over streamingplatformen, we noemen deze Event Brokers. Het verschil tussen Event Hub en Event Broker is dat de Event Hub meer geschikt is voor efficiënt verwerken van grote hoeveelheden event data en is daarvoor geoptimaliseerd. Ook geeft de term Event Hub in deze context aan dat het een centrale voorziening betreft in een hub-spoke architectuur.


Diensten Catalogus (optioneel)
-------------

> ##### Concept
{: .block-danger }

De Diensten Catalogus is een centrale voorziening in de keten waarin de diensten die aangeboden worden door de keten- of samenwerkingspartners binnen de Jeugd, Zorg en Veiligheidsketen worden beschreven en gepubliceerd. De dienstencatalogus bevat gegevens over een dienst, de aanbiedende ketenpartner, de toegestane afnemende ketenpartners, de contactgegevens bij de aanbieder, de URL voor het aanvragen van de dienst, en de minimale vereiste gegevens voor het ‘bestellen’ van de dienst en een verwijzing naar de bij de dienst behorende SLA. Er moet, niet vrijblijvend, altijd een contract, convenant of andersoortige afspraak tussen afnemer en aanbieder aan het leveren van een dienst ten grondslag liggen. Deze en eventuele bijbehorende DPIA of andersoortige afspraken kunnen eventueel ook via de Dienstencatalogus ontsloten worden.


API Catalogus (optioneel)
-------------

> ##### Concept
{: .block-danger }

Idealiter zijn API goed vindbaar. De API Catalogus voorziening vormt een centrale plek om keten API’s te kunnen vinden. De API Catalogus voorziening verwijst door naar de centrale API Catalogi / DevPortals. REST API is immers een decentraal patroon en afhankelijkheden van centrale voorzieningen zijn ongewenst. De API Catalogus voorziening maakt het zoeken slechts eenvoudiger en levert een totaal overzicht van de keten API’s op één plek. Dat is handig, maar geen vereiste.


Bericht transformatie dienst (optioneel, ongewenst doch mogelijk onvermijdbaar)
-------------

> ##### Concept
{: .block-danger }

De communicatie tussen verschillende domeinen die hun eigen protocollen, eigen datamodellering en eigen semantiek voeren vraagt om een vertaalservice. Naast deze verschillen moet het verschil tussen verschillende versies en release kalenders van services en clients worden opgevangen. Een verschil tussen service (bron) en client (gebruiker) zal altijd opgelost moeten worden. In een zuivere API gedachte zijn de clients en de service loosely coupled, wat het translatie en transformatie probleem bij de ontvanger van de gegevens legt. 

In het meest ideale geval worden services, zoals ze worden gedefinieerd overal hetzelfde toegepast én volgen ze allemaal volgens dezelfde releasekalender nieuwe versies. Dat is echter een utopie en zal nooit voorkomen. Vandaar dat berichttransformatie en protocol translatie functies zijn die ook CORV2 zal moeten ondersteunen. Het vertalen van berichten is een standaard functie van het huidige CORV. Doorgaans is standaard vertaling niet mogelijk en in plaats daarvan moet vrijwel altijd maatwerk worden ingezet. 

Het centraal transformeren van gegevens verlangt veel kennis van de bron en de ontvangende partij. Vooral als deze vertalingen complexe “IF THEN ELSE” constructies bevatten. Ze zijn kostbaar om te onderhouden en relatief foutgevoelig. Omdat we verwachten dat het aantal services zal stijgen is het zaak om deze transformaties (als wel de translaties) tot een minimum te beperken. Een landschap dat via transformaties is gekoppeld is sterk monolithisch. Dergelijke transformaties centraal uitvoeren is ongewenst en dient dus alleen te worden gedaan als dit realistisch niet anders kan en dienen in principe altijd tijdelijk te zijn (ter overbrugging).


Service orkestratie (optioneel, vermijden)
-------------

> ##### Concept
{: .block-danger }

Via service orkestratie kunnen end-to-end workflows en processen geautomatiseerd afgehandeld. Ze omvatten de volledige reeks van stappen en activiteiten die nodig zijn om te komen tot een informatieproduct. De service orkestratie bevat de business logica van de bron en de informatie behoeftige. Op deze manier kunnen systemen worden gekoppeld via een uniform raamwerk. 

Een voorbeeld van service orkestratie is de routering service van CORV waarbij op basis van logica een specifieke dienst, lees gemeente wordt benaderd. Een verdergaand concept is die van de e-makelaar. E-makelaar bevat in hoge mate business logica en voegt een extra laag van complexiteit en afhankelijkheid toe. Net als alle centrale service orkestratieve oplossingen wordt de business logica van andere ketenpartners centraal geïmplementeerd. Dit is een monolithische denklijn die mits toegepast op een bepaald gebied werkbaar is. 

Orkestratie beperkt ook de autonomie van individuele services en kan leiden tot prestatieproblemen en veiligheidsrisico's door centralisatie. In dergelijke situaties zijn meer losgekoppelde, event-driven architecturen of choreografie-benaderingen vaak beter geschikt, omdat ze flexibiliteit en schaalbaarheid bevorderen.


Service orkestratie (optioneel, vermijden)
-------------

> ##### Concept
{: .block-danger }

Via service orkestratie kunnen end-to-end workflows en processen geautomatiseerd afgehandeld. Ze omvatten de volledige reeks van stappen en activiteiten die nodig zijn om te komen tot een informatieproduct. De service orkestratie bevat de business logica van de bron en de informatie behoeftige. Op deze manier kunnen systemen worden gekoppeld via een uniform raamwerk. 

Een voorbeeld van service orkestratie is de routering service van CORV waarbij op basis van logica een specifieke dienst, lees gemeente wordt benaderd. Een verdergaand concept is die van de e-makelaar. E-makelaar bevat in hoge mate business logica en voegt een extra laag van complexiteit en afhankelijkheid toe. Net als alle centrale service orkestratieve oplossingen wordt de business logica van andere ketenpartners centraal geïmplementeerd. Dit is een monolithische denklijn die mits toegepast op een bepaald gebied werkbaar is. 

Orkestratie beperkt ook de autonomie van individuele services en kan leiden tot prestatieproblemen en veiligheidsrisico's door centralisatie. In dergelijke situaties zijn meer losgekoppelde, event-driven architecturen of choreografie-benaderingen vaak beter geschikt, omdat ze flexibiliteit en schaalbaarheid bevorderen.








