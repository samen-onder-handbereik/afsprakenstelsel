---
title: Beheer en monitoring
author: lg
date: 2025-10-04
category: Jekyll
layout: post
---

> ##### Concept
{: .block-danger }

Enerzijds is er het beheer en de monitoring van het Afsprakenstelsel zelf, anderzijds het functionele en technische beheer en de monitoring binnen het landschap als geheel.

Beheer en monitoring Afsprakenstelsel
-------------
Het doel van dit beheer is te zorgen dat het Afsprakenstel aan blijft sluiten bij wat nodig is en continue wordt verbetert. Dit vindt plaats door roadmaps beschikbaar te maken waarin de ontwikkeling van het Afsprakenstel gevolgd kan worden. Door mogelijkheden te bieden om wijzigingsverzoeken en verbetervoorstellen in te dienen en te volgen, maar ook issues die ervaren worden. Er wordt nauw aangesloten bij werkwijzen die aansluiten bij de development praktijk en software ontwikkelende organisaties en afdelingen. Daarnaast worden ook traditionelere kanalen geboden (documenten, formulieren, etc). Uitvoering van het beheer vindt plaats door de partijen, vanuit de verschillende rollen, benoemd in hoofdstuk [Governance][1]. 

Beheer en monitoring binnen het landschap als geheel
-------------
Voor dit beheer is onderscheid te maken naar het beheer van stelselvoorzieningen en beheer in de context van het geheel waarbij ook het beheer bij de deelnemers een belangrijke rol speelt.

### Stelselvoorzieningen
Het beheer en de monitoring van de stelselvoorzieningen is recht toe en recht aan. Dit wordt uitgevoerd door de partijen die de stelselvoorzieningen leveren en dat conform afspraken en service level agreements (SLA’s). Het is gericht op het functioneren van de stelselvoorzieningen in lijn met deze afspraken, SLA’s en onderliggende functionele en niet-functionele eisen. Organisaties kunnen bij operationele problemen, verstoringen of wijzigingsverzoeken contact opnemen met de beheerpartijen van de stelselvoorzieningen, en voor niet operationele aspecten met de eigenaar/opdrachtgever voor het leveren, beheren en monitoren van de stelselvoorzieningen. Zie de beschrijving van de rollen in het hoofdstuk [Governance][1].

### Decentrale voorzieningen
Omdat sprake is federatief landschap betekent dit dat er niet één beheerpartij is (voor een centrale dienst), maar een landschap van beheerpartijen die in het federatieve landschap alle een eigen verantwoordelijkheid hebben. Concreet betekent dit dat bij problemen, verstoringen of wijzigingsverzoeken het kan zijn dat contact opgenomen moet (kunnen) worden met de een specifieke partij in het landschap en mogelijk meerdere. Dit levert een aantal uitdagingen op:
- Het moet idealiter eenvoudig mogelijk zijn vast te kunnen stellen waar in het landschap iets mis gaat of waar een wijziging nodig is. Dit is geen sinecure in een loosely coupled landschap met veel partijen.
- Deelnemers moeten bewust zijn dat zijn dat zij niet alleen hun eigen interne organisatie moeten bedienen, maar ook organisaties binnen het Afsprakenstelsel. Processen en contactpunten moeten daarop ingericht zijn.
- Deelnemers moeten bewust zijn dat zij zelf niet alles kunnen oplossen en afhandelen, maar daarvoor ook andere organisaties moeten kunnen benaderen en daar afhankelijk van kunnen zijn. Ook hier moeten processen op ingericht zijn. 
- Deelnemers moeten bewust zijn dat het uitvoeren van wijzigingen of onderhoud op API’s invloed kan hebben op andere Deelnemers, maar ook dat het niet (tijdig) uitvoeren van wijzigingen of onderhoud dat ook kan hebben.
- Voor bepaalde wijzigingen kan een georkestreerde wijziging nodig zijn bij een tal van partijen tegelijkertijd of in een bepaalde volgorde in de tijd. 

### Interacties
Zoals hiervoor geschetst zijn soms interacties nodig tussen partijen. De ervaring leert dat dit tijdrovend is en belastend voor organisaties. Belangrijk is het aantal interacties tot een minimum te beperken. Dat kan door:
- In de eerste plaats door de afspraken te volgen, denk aan afspraken rond versiebeheer.
- Duidelijke documentatie te publiceren, bijvoorbeeld op API Management DevPortals.
- Test services (API’s) beschikbaar te stellen zodat anderen deze kunnen ‘pollen’  en zelf kunnen vaststellen dat er connectiviteit is, de achterliggende services operationeel zijn en de basis authenticatie en autorisatie services operationeel zijn.
- Optioneel test services (API’s) beschikbaar te stellen waar functioneel kan worden getest, bijvoorbeeld t.a.v. Inzage en Opdracht.
- (Optioneel?) het uitsturen van gebeurtenissen die service health aangeven op frequente basis en waarbij het niet meer ontvangen daarvan een aanwijzing is dat de service mogelijk niet meer (goed) functioneert, beheerorganisaties kunnen deze gebeurtenissen of het plots ontbreken daarvan nagaan en daar geautomatiseerde acties aan koppelen. 
- Test services (API’s) beschikbaar te stellen waar ketenvoorzieningen functioneel kunnen worden getest, bijvoorbeeld t.a.v. het publiceren of bevragen van gebeurtenissen, het terug ontvangen van API calls (van test Services), het kunne valideren van event (CloudEvent/PROV) syntax, etc. Dit in de vorm van een Self Service Test en Validatie voorziening.
- Optioneel een keten dashboard te publiceren dat alle test services bevraagd en de status daarvan toont in een ketenbeeld.

### Monitoring
Monitoring richt zich in eerste instantie op de eigen services en het eigen ICT landschap. In deze context is het echter ook van belang monitoring breder te zien. Voor beheerafdelingen/teams is het van belang een beeld van het functioneren van het landschap te kunnen hebben en zelf validaties te kunnen doen om na te gaan waar zich verstoringen voordoen. Te denken valt het gebruik van een dashboard welke remote (test) services valideert (zie vorige paragraaf) of het gebruik binnen het beheer en monitoring proces van een centraal dashboard.

[1]: https://samen-onder-handbereik.github.io/afsprakenstelsel/jekyll/2025-09-24-werking.html#governance



