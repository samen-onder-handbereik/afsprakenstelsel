---
title: Credits
author: lg
date: 2025-09-30
category: Jekyll
layout: post
---

This is an draft page.

Test1a

   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```

Test1b
<details><summary>▶ Click to show answer</summary>Correct Answer: A</details>  



Test2
<br>
<img src="../assets/gitbook/images/publishing_fig.png"
     alt=""
     style="float: left; margin-right: 10px; margin-bottom: 10px;" />
<br>


Test3
>### tl;dr
>blabla.
{: .block-tip }

Test4
>Consider the following data search and collection services:
>* RKGs such as [ORKG](https://orkg.org) or [OpenAIRE Graph](https://graph.openaire.eu)
>* [Papers With Code](https://paperswithcode.com)  
>* [Google Dataset Search](https://datasetsearch.research.google.com)
>* [Kaggle](https://www.kaggle.com/datasets)
>* [Hugging Face Datasets](https://huggingface.co/docs/datasets/index)
>* [Awesome Public Datasets](https://github.com/awesomedata/awesome-public-datasets)
>* [Data.world](https://data.world/search?context=community&entryTypeLabel=dataset&type=resources)
>* [ELG](https://live.european-language-grid.eu)
>* Additional useful data collection services are available under *Services Lifecycle* on the [NFDI4DS](https://www.nfdi4datascience.de/services/all/) webpage.


PlantUML
Algemeen:
@startuml  
skinparam monochrome true  
skinparam defaultTextAlignment center  

actor "Client" as Client  
rectangle "Autorisatieserver" as AuthServer  
rectangle "Policy Administration Point\n(PAP)" as PAP  
rectangle "Policy Retrieval Point\n(PRP)" as PRP  
rectangle "Policy Decision Point\n(PDP)" as PDP  
rectangle "Policy Information Point\n(PIP)" as PIP  

rectangle "Policy Enforcement Point\n(PEP)" as PEP  
database "Data Toegangspunt\n(Resource-Server)" as DataAccess  

Client -up-> AuthServer : "Tokenaanvraag"  
AuthServer -down-> Client : "JWT Access-token"  

Client -right-> PEP : "Toegangsverzoek\n(REST/GraphQL + JWT)"  
PEP -left-> Client : "Gevraagde data"  

PEP -right-> DataAccess: "Geautoriseerde data-aanvraag"  
DataAccess -left-> PEP : "Gevraagde data"  

PEP -down-> PDP : "Toegangsverzoek"  
PDP -up-> PEP : "Toegangsbesluit"  

PDP -right-> PIP : "Contextinformatie opvragen" 
PIP -left-> PDP : "Contextinformatie retourneren"  

PDP -down-> PRP : "Beleidsregels ophalen"  
PRP -up-> PDP : "Beleidsregels retourneren"  

PAP -up-> PRP: "Beleidsregels beheren"  
@enduml

Autoriseren:
@startuml  
skinparam monochrome true  
skinparam defaultTextAlignment center  

actor Client as "Deelnemer (Client)"  
participant "Autorisatieserver" as AuthzServer  

Client -> AuthzServer: **1. Aanvragen van autorisatie**\n(scope, authenticatiemiddel)  
AuthzServer -> AuthzServer: **2. Valideer authenticatiemiddel**  
AuthzServer -> AuthzServer: **3. Beoordeel scope**\n(beleidsregels)   
AuthzServer -> AuthzServer: **4. Controleer audience**  
AuthzServer --> Client: **5. Genereer en retourneer**\n(access token)  
Client <-[#red]-X AuthzServer: **6. Foutmeldingen**\n(400/403/500)  
@enduml
