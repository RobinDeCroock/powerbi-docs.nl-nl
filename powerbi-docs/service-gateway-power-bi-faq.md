---
title: Veelgestelde vragen over on-premises gegevensgateways - Power BI
description: In dit artikel vindt u de veelgestelde vragen over on-premises gegevensgateways voor Power BI. Op deze centrale plek zijn alle veelgestelde vragen over de gateway die in Power BI wordt gebruikt, bij elkaar gebracht.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 45a645227a5d7a18fd05738559ed0bccc0e1f7c9
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872390"
---
# <a name="on-premises-data-gateway-faq---power-bi"></a>Veelgestelde vragen over on-premises gegevensgateways - Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

## <a name="power-bi"></a>Power BI

**Vraag:** Moet ik de on-premises gegevensgateway (persoonlijke modus) upgraden?

**Antwoord**: Nee, u kunt de gateway (persoonlijke modus) blijven gebruiken voor Power BI.

**Vraag:** Zijn er speciale machtigingen vereist om de gateway te installeren en te beheren in de Power BI-service?

**Antwoord**: Er zijn geen speciale machtigingen vereist.

**Vraag:** Kan ik Excel-werkmappen met Power Pivot-gegevensmodellen uploaden die verbinding maken met on-premises gegevensbronnen? Heb ik een gateway nodig voor dit scenario? 

**Antwoord**: Ja, u kunt de werkmap uploaden. En nee, u hebt geen gateway nodig. Maar omdat de gegevens zich bevinden in het gegevensmodel van Excel, zijn rapporten in Power BI die zijn gebaseerd op de Excel-werkmap niet live. Als u rapporten in Power BI wilt vernieuwen, moet u een bijgewerkte werkmap elke keer uploaden. U kunt de gateway ook gebruiken met geplande vernieuwing.

**Vraag:** Als gebruikers dashboards delen die een DirectQuery-verbinding hebben, kunnen die andere gebruikers dan de gegevens zien, ook als ze misschien niet dezelfde machtigingen hebben? 

**Antwoord**: Voor een dashboard dat is verbonden met Azure Analysis Services, zien gebruikers alleen de gegevens waartoe ze toegang hebben. Als de gebruikers niet dezelfde machtigingen hebben, kunnen ze geen gegevens zien. Voor andere gegevensbronnen delen alle gebruikers de referenties die door de beheerder zijn ingevoerd voor de gegevensbron.

**Vraag:** Waarom kan ik geen verbinding maken met mijn Oracle-server? 

**Antwoord**: Mogelijk moet u de Oracle-client installeren en het bestand tnsnames.ora configureren met de juiste servergegevens om verbinding te kunnen maken met de Oracle-server. Dit is een afzonderlijke installatie buiten de gateway. Zie [De Oracle-client installeren](service-gateway-onprem-manage-oracle.md#install-the-oracle-client) voor meer informatie.

**Vraag:** Werkt de gateway met Azure ExpressRoute? 

**Antwoord**: Ja. Zie [Power BI en ExpressRoute](service-admin-power-bi-expressroute.md) voor meer informatie over ExpressRoute en Power BI.

**Vraag:** Ik gebruik R-scripts. Wordt dit ondersteund?

**Antwoord**: R-scripts worden alleen ondersteund voor de persoonlijke modus.

## <a name="analysis-services-in-power-bi"></a>Analysis Services in Power BI

**Vraag:** Kan ik msdmpump.dll gebruiken voor het maken van effectieve toewijzingen van aangepaste gebruikersnamen voor Analysis Services? 

**Antwoord**: Nee. Dit gebruik wordt op dit moment niet ondersteund.

**Vraag:** Kan ik de gateway gebruiken om verbinding te maken met een multidimensionaal exemplaar (OLAP)? 

**Antwoord**: Ja. De on-premises gegevensgateway ondersteunt live-verbindingen met zowel tabellaire modellen van Analysis Services als multidimensionale modellen.

**Vraag:** Wat gebeurt er als ik de gateway installeer op een computer in een ander domein dan mijn on-premises server die gebruikmaakt van Windows-authenticatie? 

**Antwoord**: Hier kunnen we helaas geen duidelijk antwoord geven. Het hangt allemaal af van de vertrouwensrelatie tussen de twee domeinen. Als de twee verschillende domeinen deel uitmaken van een model op basis van vertrouwde domeinen, kan de gateway mogelijk verbinding maken met de Analysis Services-server en kan de effectieve gebruikersnaam mogelijk worden omgezet. Als dat niet het geval is, kan de aanmelding mislukken.

**Vraag:** Hoe kom ik erachter welke effectieve gebruikersnaam wordt doorgegeven aan mijn on-premises Analysis Services-server? 

**Antwoord**: Het antwoord op deze vraag vindt u in dit [artikel voor probleemoplossing](service-gateway-onprem-tshoot.md).

## <a name="next-steps"></a>Volgende stappen

* [Problemen met de on-premises gegevensgateway oplossen](/data-integration/gateway/service-gateway-tshoot)

Hebt u nog vragen? Misschien dat de [Power BI-community](https://community.powerbi.com/) het antwoord weet.

