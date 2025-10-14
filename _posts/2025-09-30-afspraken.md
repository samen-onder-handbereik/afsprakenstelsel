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



