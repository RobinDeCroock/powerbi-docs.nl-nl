---
title: Richtlijnen voor het implementeren van een gegevensgateway voor Power BI
description: Lees hier alles over de aanbevolen procedures en overwegingen voor het implementeren van een gateway voor Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 4351804330982b32582c4c782ef7c2fa0e92f197
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271725"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Richtlijnen voor het implementeren van een gegevensgateway voor Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Dit artikel bevat richtlijnen en overwegingen voor het implementeren van een gegevensgateway voor Power BI in uw netwerkomgeving.

Zie [Wat is een on-premises gegevensgateway](/data-integration/gateway/service-gateway-onprem) voor meer informatie over het downloaden, installeren, configureren en beheren van de on-premises gegevensgateway. U vindt ook meer informatie over de on-premises gegevensgateway en Power BI in de [Microsoft Power-blog](https://powerbi.microsoft.com/blog/) en op de [Microsoft Power BI-community](https://community.powerbi.com/)-site.

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>Overwegingen bij de installatie van een on-premises gegevensgateway

Voordat u de on-premises gegevensgateway installeert voor uw Power BI-cloudservice, zijn er diverse overwegingen om rekening mee te houden. In de volgende secties worden deze overwegingen beschreven.

### <a name="number-of-users"></a>Aantal gebruikers

Het aantal gebruikers dat via de gateway gebruikmaakt van een rapport is een belangrijke metrische factor bij het bepalen van de locatie van de gateway. Dit zijn enkele vragen die hier van belang zijn:

* Worden deze rapporten op verschillende tijdstippen van de dag gebruikt?
* Wat voor soorten verbindingen worden er gebruikt (DirectQuery of importeren)?
* Gebruiken alle gebruikers hetzelfde rapport?

Als alle gebruikers op hetzelfde moment een bepaald rapport raadplegen, moet u de gateway installeren op een computer die al deze aanvragen kan verwerken (zie de volgende secties voor prestatiemeteritems en de minimale vereisten die hierbij een rol spelen).

Er geldt een beperking in **Power BI** van *één* gateway per *rapport*. Dus zelfs als een rapport is gebaseerd op meerdere gegevensbronnen, moeten al deze gegevensbronnen via één gateway worden aangeboden. Als een dashboard echter is gebaseerd op *meerdere* rapporten, kunt u voor elk rapport een speciale gateway gebruiken en zo de belasting van de gateway verdelen over de meerdere rapporten die bijdragen aan één dashboard.

### <a name="connection-type"></a>Type verbinding

**Power BI** biedt twee typen verbindingen: **DirectQuery** en **Importeren**. Niet alle gegevensbronnen ondersteunen beide verbindingstypen en er zijn verschillende redenen waarom u juist voor het ene of het andere type zou kiezen, zoals beveiligingsvereisten, prestaties, gegevenslimieten en de grootte van het gegevensmodel. Meer informatie over verbindingstypen en ondersteunde gegevensbronnen vindt u in de [lijst met beschikbare gegevensbrontypen](service-gateway-data-sources.md#list-of-available-data-source-types).

Afhankelijk van welk type verbinding u gebruikt, kan het gatewaygebruik verschillen. Zo moet u bijvoorbeeld proberen om gegevensbronnen van het type **DirectQuery** waar mogelijk te scheiden van gegevensbronnen van het type **Geplande vernieuwing** (ervan uitgaande dat ze zich in verschillende rapporten bevinden en kunnen worden gescheiden). Hierdoor wordt voorkomen dat de wachtrij van de gateway volloopt met duizenden DirectQuery aanvragen op hetzelfde moment dat 's ochtends de vernieuwing is gepland van een groot gegevensmodel dat wordt gebruikt voor het belangrijkste dashboard van het bedrijf. Dit zijn de overwegingspunten voor beide typen:

* Voor **geplande vernieuwing**: afhankelijk van de grootte van uw query en het aantal vernieuwingen per dag, kunt u ervoor kiezen om de aanbevolen minimale hardwarevereisten te blijven hanteren of te upgraden naar een machine met betere prestaties. Als een bepaalde query niet wordt teruggestuurd naar de bron, vinden transformaties plaats op de gatewaycomputer. Om die reden is het dus gunstig als voor de gatewaycomputer meer RAM-geheugen beschikbaar is.

* Voor **DirectQuery**: er wordt telkens een query verzonden wanneer een gebruiker het rapport opent of gegevens bekijkt. Als u verwacht dat meer dan 1000 gebruikers tegelijk toegang tot de gegevens moeten hebben, is het belangrijk om te controleren of uw computer is uitgerust met stabiele en geschikte hardware-onderdelen. Meer CPU-kernen zorgen voor een betere doorvoer voor een **DirectQuery**-verbinding.

De vereisten voor een computer waarop u installeert zijn te vinden in de [installatievereisten](/data-integration/gateway/service-gateway-install#requirements) voor on-premises gegevensgateways.

### <a name="location"></a>Locatie

De locatie van de installatie van de gateway kan aanzienlijke invloed hebben op de prestaties van uw query's. Probeer er daarom voor te zorgen dat uw gateway, de gegevensbronnen en de Power BI-tenant zo dicht mogelijk bij elkaar zijn geplaatst om de netwerklatentie te minimaliseren. Om de locatie van uw Power BI-tenant te bepalen, selecteert u het vraagteken **?** in de Power BI-service (in de rechterbovenhoek) en selecteert u vervolgens **Over Power BI**.

![Uw Power BI-tenantlocatie bepalen](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

Als u van plan bent om de Power BI-gateway te gebruiken met Azure Analysis Services, moet u ervoor zorgen dat de gegevensgebieden in beide overeenkomen. Bekijk [deze video](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/) voor meer informatie over het instellen van gegevensgebieden voor meerdere services.

## <a name="next-steps"></a>Volgende stappen

* [Proxyinstellingen configureren](/data-integration/gateway/service-gateway-proxy)  
* [Problemen met gateways oplossen - Power BI](service-gateway-onprem-tshoot.md)  
* [Veelgestelde vragen over on-premises gegevensgateways - Power BI](service-gateway-power-bi-faq.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

