---
title: Technische patronen
author: lg
date: 2025-09-27 14:00:00
category: Jekyll
layout: post
---

> ##### Concept
{: .block-danger }

Opdracht, Inzage en Gebeurtenissen zijn functionele patronen. In dit onderdeel zijn de technische patronen beschreven waarmee deze functionele samenwerkpatronen kunnen worden gerealiseerd en op hun beurt daarmee de functionele samenwerkfuncties.

Kortom de samenwerkfuncties zijn op te bouwen uit de samenwerkpatronen en  de samenwerkpatronen uit de volgende technische patronen:

- Command
- Query
- Event

Het Command patroon levert een toestandswijzing op (change of state).

Het Query patroon voert een leesoperatie uit (read of state).

Het Event patroon geeft aan dat een feit of toestandsverandering heeft plaatsgevonden. Zie ook onderstaande vergelijk.

| Aspect | Command | Query | Event |
| --- | --- | --- | --- |
| Doel | Toestandswijziging | Leesoperatie | Declaratie dat iets heeft plaatsgevonden |
| Type | Doorgaans synchroon | Doorgaans synchroon | Doorgaans asynchroon |
| Adressering | Specifieke bestemming | Specifieke bestemming | Meerdere geabonneerden of broadcast |
| Communicatie | request-response | request-response | fire and forget |
| Actie | Initieert een verandering (state change) | Leesoperatie (read of state) | Beschrijft een toestandsverandering |
| Return response | Success/failure acknowledgment | Success/failure acknowledgment | Geen directe response verwacht |

Binnen het Afsprakenstelsel worden deze patronen concreet toegepast in de vormen:

| Patroon | Protocol | Methode | Response | Type |
| --- | --- | --- | --- | --- |
| Command | HTTPS REST API call | POST, PUT, PATCH, DELETE | 200, 201, 400, 401, etc. | Synchroon |
| Query | HTTPS REST API call | GET | 200, 204, 400, 401, etc. | Synchroon |
| Event | HTTPS REST API call* | POST (event versturen), GET (even lezen) | 200, 400, 401, etc. | Asynchroon |

_\* Events kunnen worden gedeeld via o.a. AMQP, MQTT, Kafka, WebSockets maar ook via REST. Voor HTTPS REST is hier gekozen om een loosely coupled koppelvlak te creëren, een relatief eenvoudig koppelvlak aan te bieden wat bekend is voor alle >1000 organisaties in het domein en gelet het type oplossing (ketenindex)._

Hieronder worden enkele voorbeelden genoemd die het verband tussen Samenwerkpatroon en Technisch patroon laten zien.

Opdracht

a) via REST API
Organisatie A geeft een opdrachten of verzoekt om een opdracht uit te voeren richting Organisatie B (Opdracht samenwerkpatroon). Organisatie A stuurt REST API POST naar API van Organisatie B (**Command patroon**). Organisatie B geeft een 200/201 terug (ontvangen en wordt opgepakt) of een 202 (geaccepteerd maar nog niet afgerond, bevat informatie om status te kunnen nagaan en/of voortgang te volgen). Hierop zijn allerlei variaties mogelijk afhankelijk hoe de Samenwerkfunctie is gedefinieerd en de composite/ capability API.

b) via events
Organisatie A geeft een opdrachten of verzoekt om een opdracht uit te voeren richting Organisatie B (Opdracht samenwerkpatroon) dan wel een partij die de opdracht wil/kan uitvoeren als er daar meerdere van zijn (Opdracht samenwerkpatroon). Organisatie A stuurt een event (**Event patroon**). Organisatie B (of een andere organisatie) stuurt een event dat de opdracht wordt opgepakt. Organisatie A bevestigt naar Organisatie B (of een andere organisatie) dat de opdracht aan die partij wordt toegekend. In de events kunnen URL’s zijn opgenomen waar informatie over de opdracht is te vinden (**Query patroon**) of de status van uitvoering (Query patroon). Hierop zijn allerlei variaties mogelijk afhankelijk hoe de Samenwerkfunctie is gedefinieerd en de event gebaseerde invulling wordt ontworpen.

c) via ebMS
Dit is de huidige benadering (CORV1).

Inzage  
Organisatie A wil informatie inzien waarvan Organisatie B bronhouder is (Inzage samenwerkpatroon). Organisatie A stuurt een REST API GET naar de API van Organisatie B (**Query patroon**). Organisatie B geeft een 200 terug en de informatie. Hierop zijn allerlei variaties mogelijk afhankelijk hoe de Samenwerkfunctie is gedefinieerd en de composite/ capability API.

Organisatie A kan genotificeerd zijn of acteren op een event welke Organisatie A heeft gezien of ontvangen. In het event kan een URL zijn opgenomen voor de Inzage.

Gebeurtenis  
Organisatie A geeft aan dat een bepaalde gebeurtenis, actie of toestandswijziging heeft plaatsgevonden (Gebeurtenis samenwerkpatroon). Een aantal andere organisaties is hierin geïnteresseerd. Organisatie A stuur het event via een REST API POST naar de Event Provenance Store en Event Hub (CORV2) (Command patroon). De geïnteresseerde organisaties sturen via REST API POST een query naar de Event Provenance Store en Event Hub (Command patroon). Daarna sturen ze een REST API GET om na te gaan over de query resultaten heeft (‘pollen’) (Query patroon).  Bij elkaar geven deze invulling aan het **Event** **patroon** via een asynchone API benadering (waarbij AsyncAPI wordt toegepast voor de API beschrijvingen.