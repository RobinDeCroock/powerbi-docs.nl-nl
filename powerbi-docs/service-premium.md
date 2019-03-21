---
title: Wat is Microsoft Power BI Premium?
description: Power BI Premium is toegewezen capaciteit voor uw organisatie of team om u betrouwbaardere prestaties en grotere gegevensvolumes te kunnen bieden, zonder dat u voor iedere gebruiker een licentie hoeft te kopen.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/12/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: f327cb95c10756f079778d20e62cba4871b95c02
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/18/2019
ms.locfileid: "57964934"
---
# <a name="what-is-microsoft-power-bi-premium"></a>Wat is Microsoft Power BI Premium?

> [!NOTE]
> Dit artikel wordt momenteel bijgewerkt met beschrijvingen van nieuwe functies, meer informatie en betere leesbaarheid. Zie [Power BI Premium-capaciteiten implementeren en beheren](whitepaper-powerbi-premium-deployment.md) voor het laatste nieuws.

Power BI Premium bevat toegewezen resources om de Power BI-service voor uw organisatie uit te voeren. Dit resulteert in betrouwbaardere prestaties en u kunt grotere gegevensvolumes verwerken. Premium biedt ook de mogelijkheid tot een wijdverspreide distributie zonder dat u per gebruiker Pro-licenties hoeft te kopen voor inhoudsgebruikers.  

## <a name="premium-capacity-and-shared-capacity"></a>Premium-capaciteit en gedeelde capaciteit

U kunt profiteren van Power BI Premium door werkruimten aan een *Premium-capaciteit* toe te wijzen. Premium-capaciteit is een toegewezen resource voor uw organisatie. Werkruimten die niet zijn toegewezen aan een Premium-capaciteit, bevinden zich in een *gedeelde capaciteit*. Met gedeelde capaciteit worden uw workloads uitgevoerd via rekenresources die met andere klanten worden gedeeld.

In de volgende afbeelding wordt de Contoso-organisatie als voorbeeld gebruikt om de relatie tussen de Premium-capaciteit en de gedeelde capaciteit te demonstreren.

![Afbeelding van Power BI Premium](media/service-premium/premium-chart.png)

| Oppervlakte | Beschrijving |
| --- | --- |
| **(1)** Items binnen een Premium-capaciteit | <ul><li>Voor de toegang tot app-werkruimten (als leden of beheerders) en het publiceren van apps is Power BI Pro-licentie vereist.<li>Voor het delen van een app is een Pro-licentie vereist, voor het gebruik van een app niet.<li>Alle ontvangers van het dashboard kunnen gegevensmeldingen instellen, ongeacht de licentie die aan hen is toegewezen.<li>REST-API's voor insluiten maken gebruik van een serviceaccount met een Pro-licentie, in plaats van een gebruikersaccount.</ul> |
| **(2)** Mijn werkruimte in gedeelde capaciteit | <ul><li>Er is een Pro-licentie vereist voor zowel het delen als gebruiken van een app.</ul> |
| **(3)** App-werkruimten in gedeelde capaciteit | <ul><li>Voor het gebruik van de apps is een Pro-licentie vereist.</ul>|
| | |

Bij een gedeelde capaciteit past Power BI meer beperkingen toe voor individuele gebruikers om alle gebruikers een goede ervaring te geven. Uw werkruimte bevindt zich standaard in een gedeelde capaciteit, evenals uw persoonlijke *Mijn werkruimte* en app-werkruimten.

De volgende tabel bevat een overzicht van de verschillen tussen de gedeelde capaciteit en de Premium-capaciteit:

|  | Gedeelde capaciteit | Power BI Premium-capaciteit |
| --- | --- | --- |
| **Vernieuwingsfrequentie** |8 keer per dag |48 keer per dag |
| Isolatie met toegewezen hardware |![Niet beschikbaar](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| Enterprise-distributie naar *alle gebruikers* | | |
| Apps en delen |![Niet beschikbaar](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| Ingesloten API en besturingselementen |![Niet beschikbaar](media/service-premium/not-available.png) |![](media/service-premium/available.png)<sup>[1](#fnt1)</sup> |
| Power BI-rapporten on-premises publiceren |![Niet beschikbaar](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| | | |

<a name="fnt1">1</a> Toekomstige verbeteringen voor Power BI Premium.



### <a name="premium-capacity-nodes"></a>Premium-capaciteitsknooppunten

Power BI Premium is beschikbaar in knooppuntconfiguraties met verschillende v-corecapaciteiten. Zie [Prijzen van Power BI](https://powerbi.microsoft.com/pricing/) voor meer informatie over het specifieke SKU-aanbod en de kosten. Er is ook een [kostencalculator](https://powerbi.microsoft.com/calculator/) beschikbaar. Zie [Technisch document over het plannen van een Power BI Enterprise-implementatie](https://aka.ms/pbienterprisedeploy) voor meer informatie over het plannen van de ingesloten analysecapaciteit. Samenvattend:

* P-knooppunten kunnen worden gebruikt voor ingesloten of service-implementaties.

* EM-knooppunten kunnen alleen worden gebruikt voor ingesloten implementaties. EM-knooppunten hebben geen toegang tot premiummogelijkheden, zoals apps delen met gebruikers die geen Power BI Pro-licentie hebben.

| Capaciteitsknooppunt | Totaal aantal v-cores<br/>*(Back-end + front-end)*  | V-cores voor back-end<sup>[1](#fn1)</sup> | V-cores voor front-end<sup>[2](#fn2)</sup> | Limieten voor DirectQuery/liveverbindingen | Maximum aantal gelijktijdige vernieuwingen |
| --- | --- | --- | --- | --- | --- |
| EM1 (maandelijks) |1-v-core |0,5 v-core, 2,5 GB RAM |0,5 v-core |3,75 per seconde |  1 |
| EM2 (maandelijks) |2 v-cores |1 v-core, 5 GB RAM |1-v-core |7,5 per seconde |  2 |
| EM3 (maandelijks) |4 v-cores |2 v-cores, 10 GB RAM |2 v-cores | 15 | 3 |
| P1 |8 v-cores |4 v-cores, 25 GB RAM |4 v-cores |30 per seconde | 6 |
| P2 |16 v-cores |8 v-cores, 50 GB RAM |8 v-cores |60 per seconde | 12 |
| P3 |32 v-cores |16 v-cores, 100 GB RAM |16 v-cores |120 per seconde | 24 |
| | | | | | |

<a name="fn1">1</a>: V-cores voor front-end zijn verantwoordelijk voor de webservice. Dit gaat dan bijvoorbeeld om het documentbeheer voor dashboards en rapporten, het beheren van de toegangsrechten, de planning, API's, uploaden en downloaden en in het algemeen voor alles met betrekking tot de gebruikerservaring. 

<a name="fn2">2</a>: De back-end-v-cores zijn verantwoordelijk voor het zware werk: verwerken van query's, cachebeheer, uitvoeren van R-servers, vernieuwen van gegevens, natuurlijke taalverwerking, realtime feeds en het weergeven van rapporten en afbeeldingen op de server. Voor de back-end-v-cores wordt ook een bepaalde hoeveelheid geheugen gereserveerd. Het is met name belangrijk om voldoende geheugen te hebben wanneer er met grote gegevensmodellen of met een groot aantal actieve gegevenssets wordt gewerkt.

## <a name="workloads-in-premium-capacity"></a>Workloads in Premium-capaciteit

De standaardconfiguratie is dat Power BI Premium- en Power BI Embedded-capaciteiten alleen de workload ondersteunen die is gekoppeld aan het uitvoeren van Power BI-query's in de cloud. Premium biedt tevens ondersteuning voor extra workloads voor **AI**, **gegevensstromen** en **gepagineerde rapporten**. Voordat deze workloads de resources van uw capaciteit kunnen gebruiken, moeten ze zijn ingeschakeld in de Power BI-beheerportal of via de REST API van Power BI. Elke workload heeft standaardinstellingen voor het maximale geheugen dat elke workload kan gebruiken. U kunt echter andere instellingen voor geheugengebruik configureren om te bepalen hoe de workloads van invloed zijn op elkaar en hoe de resources van uw capaciteit worden gebruikt. Zie [Workloads configureren](service-admin-premium-workloads.md) voor meer informatie.

## <a name="power-bi-report-server"></a>Power BI Report Server

Met Power BI Premium kunt u Power BI Report Server ook on-premises uitvoeren in uw organisatie. Zie [Aan de slag met Power BI Report Server](report-server/get-started.md) voor meer informatie.

## <a name="next-steps"></a>Volgende stappen

[Power BI Premium-capaciteiten implementeren en beheren](whitepaper-powerbi-premium-deployment.md)   
[Power BI Premium aanschaffen](service-admin-premium-purchase.md)   
[Veelgestelde vragen over Power BI Premium](service-premium-faq.md)   



Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
