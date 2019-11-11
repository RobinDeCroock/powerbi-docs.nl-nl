---
title: Inleiding tot dashboards voor Power BI-ontwerpers
description: Dashboards zijn een belangrijke functie van de Power BI-service. Een dashboard bestaat uit één pagina, ook wel een canvas genoemd, waarin een verhaal wordt verteld aan de hand van visualisaties.
author: maggieMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 41381a2f0ccc2c5db904d9ac94c7dad19edfa4e5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872743"
---
# <a name="introduction-to-dashboards-for-power-bi-designers"></a>Inleiding tot dashboards voor Power BI-ontwerpers

Een Power BI-*dashboard* bestaat uit één pagina, ook wel een canvas genoemd, waarin een verhaal wordt verteld aan de hand van visualisaties. Aangezien het maar één pagina betreft, bevat een goed ontworpen dashboard alleen de belangrijkste elementen van dat verhaal. Lezers kunnen gerelateerde rapporten lezen voor meer informatie.

![Dashboard](media/service-dashboards/power-bi-dashboard2.png)

Dashboards zijn alleen een functie van de Power BI-service. Ze zijn niet beschikbaar in Power BI Desktop. U kunt weliswaar geen dashboards op mobiele apparaten maken, maar u kunt ze daar wel [weergeven en delen](mobile-apps-view-dashboard.md).

## <a name="dashboard-basics"></a>Basisbeginselen over dashboards 

De visualisaties die u op het dashboard ziet, worden *tegels* genoemd. U kunt tegels vanuit rapporten *vastmaken* aan een dashboard. Als u geen ervaring hebt met Power BI, kunt u een goede basis leggen door [Basisconcepten voor ontwerpers in de Power BI-service](service-basic-concepts.md) te lezen.

De visualisaties op een dashboard zijn afkomstig uit rapporten en elk rapport is gebaseerd op een gegevensset. Een dashboard kan worden gezien als een ingang tot de onderliggende rapporten en gegevenssets. Als u een visualisatie selecteert, gaat u naar het rapport (en de gegevensset) waarop de visualisatie is gebaseerd.

![Diagram met de relatie tussen dashboards, rapporten en gegevenssets](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Voordelen van dashboards
Dashboards zijn een fantastische manier om uw bedrijf te monitoren en de belangrijkste metrische gegevens in één oogopslag te zien. De visualisaties op een dashboard kunnen afkomstig zijn uit een of meer onderliggende gegevenssets en rapporten. Een dashboard combineert on-premises gegevens en gegevens in de cloud om zo een geconsolideerde weergave te bieden van uw gegevens, ongeacht waar deze zich bevinden.

Een dashboard is niet alleen een mooi plaatje. Het is zeer interactief en de tegels worden bijgewerkt wanneer de onderliggende gegevens worden gewijzigd.

## <a name="who-can-create-a-dashboard"></a>Wie mag een dashboard maken?
De mogelijkheid om een dashboard te maken is een functie die beschikbaar is voor *makers*. Hiervoor zijn bewerkingsmachtigingen voor het rapport vereist. Bewerkingsmachtigingen zijn beschikbaar voor makers van rapporten en voor de collega's die toegang hebben gekregen van de maker. Als David bijvoorbeeld een rapport maakt in workspaceABC en u als lid van deze werkruimte toevoegt, krijgen David en u allebei bewerkingsmachtigingen. Maar indien een rapport rechtstreeks of als onderdeel van een [Power BI-app](service-create-distribute-apps.md) met u is gedeeld, *gebruikt* u het rapport. U kunt mogelijk geen tegels vastmaken aan een dashboard. 

> [!IMPORTANT]
> U hebt een [Power BI Pro](service-free-vs-pro.md)-licentie nodig om dashboards te maken in werkruimten. U kunt dashboards maken in uw eigen sectie Mijn werkruimte zonder een Power BI Pro-licentie.


## <a name="dashboards-versus-reports"></a>Dashboards versus rapporten
[Rapporten](service-reports.md) en dashboards lijken veel op elkaar, omdat het beide canvassen zijn die met visualisaties worden ingevuld. Maar er zijn belangrijke verschillen, zoals u kunt zien in de volgende tabel.

| **Mogelijkheid** | **Dashboards** | **Rapporten** |
| --- | --- | --- |
| Pagina's |Eén pagina |Een of meer pagina's |
| Gegevensbronnen |Een of meer rapporten en een of meer gegevenssets per dashboard |Eén gegevensset per rapport |
| Beschikbaar in Power BI Desktop |Nee | Ja. Kunnen rapporten maken en weergeven in Power BI Desktop |
| Abonneren |Ja. U kunt zich abonneren op een dashboard |Ja. U kunt zich abonneren op een rapportpagina |
| Filteren |Nee. U kunt niet filteren of segmenteren |Ja. Er zijn verschillende manieren voor filteren, markeren en segmenteren |
| Aanbevolen |Ja. U kunt één dashboard instellen als uw *aanbevolen* dashboard |Nee |
| Favoriet | Ja. U kunt meerdere dashboards instellen als *favorieten* | Ja. U kunt meerdere rapporten instellen als *favorieten*
| Waarschuwingen instellen |Ja. Beschikbaar voor dashboardtegels in bepaalde omstandigheden |Nee |
| Query's in natuurlijke taal (Q&A) |Ja | Ja, mits u bewerkingsmachtigingen voor het rapport en de onderliggende gegevensset hebt |
| U kunt onderliggende tabellen en velden van de gegevensset bekijken |Nee. U kunt gegevens exporteren maar geen tabellen en velden in het dashboard zelf zien |Ja |


## <a name="next-steps"></a>Volgende stappen
* Maak kennis met dashboards door het bekijken van een van onze [voorbeelddashboards](sample-tutorial-connect-to-the-samples.md).
* Alles over [dashboardtegels](service-dashboard-tiles.md).
* Wilt u een bepaalde dashboardtegel monitoren en een e-mail ontvangen wanneer deze een bepaalde drempelwaarde bereikt? [Maak een waarschuwing op een tegel](service-set-data-alerts.md).
* Ontdek hoe u [Q&A van Power BI](power-bi-tutorial-q-and-a.md) gebruikt om een vraag te stellen over uw gegevens en antwoord krijgt in de vorm van een visualisatie.
