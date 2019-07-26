---
title: Aangepaste gegevensconnectoren gebruiken met de on-premises gegevensgateway
description: U kunt aangepaste gegevensconnectoren gebruiken met de on-premises gegevensgateway.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 074a8dd876e0612f87c220f9fb077b60b2b85c88
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271812"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>Aangepaste gegevensconnectoren gebruiken met de on-premises gegevensgateway

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Met gegevensconnectoren voor Power BI kunt u verbinding maken met en toegang krijgen tot gegevens vanuit een toepassing, service of gegevensbron. U kunt aangepaste gegevensconnectoren ontwikkelen en deze gebruiken in Power BI Desktop.

Bekijk de [GitHub-pagina Gegevensconnector-SDK](http://aka.ms/dataconnectors) voor meer informatie over het ontwikkelen van aangepaste gegevensconnectoren voor Power BI. Deze site bevat informatie om aan de slag te gaan en voorbeelden voor Power BI en Power Query.

Wanneer u in Power BI Desktop rapporten bouwt die gebruikmaken van aangepaste gegevensconnectoren, kunt u de on-premises gegevensgateway gebruiken om deze rapporten vanuit de Power BI-service te vernieuwen.

## <a name="how-to-enable-and-use-this-capability"></a>Deze functionaliteit inschakelen en gebruiken

Wanneer u de versie van juli 2018 of een latere versie van de on-premises gegevensgateway hebt geïnstalleerd, ziet u een tabblad **Connectoren** in de on-premises gegevensgateway-app met een optie voor het kiezen van een map waaruit u aangepaste connectoren wilt laden. Zorg ervoor dat u een map kiest die kan worden geopend door de gebruiker die de gateway-service uitvoert (standaard is dat de map *NT SERVICE\PBIEgwService*). De aangepaste connectorbestanden in die map worden automatisch in de gateway geladen en worden weergegeven in de lijst met gegevensconnectoren.

![Aangepaste connector 1](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

Als u de on-premises gegevensgateway (persoonlijke modus) gebruikt, moet u op dit moment uw Power BI-rapport kunnen uploaden naar de Power BI-service en de gateway kunnen gebruiken om dit rapport te vernieuwen.

Voor de on-premises gegevensgateway moet u nog steeds een gegevensbron voor uw aangepaste connector maken. In de instellingenpagina van de gateway in de Power BI-service ziet u een nieuwe optie wanneer u aangeeft dat de gatewaycluster aangepaste connectoren mag gebruiken voor dit cluster. Zorg ervoor dat alle gateways in het cluster de updateversie van juli 2018 of later hebben om te kunnen beschikken over deze optie. Selecteer nu die optie om het gebruik van aangepaste connectoren in te schakelen voor dit cluster.

![Aangepaste connector 2](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

Wanneer deze optie is ingeschakeld, ziet u nu uw aangepaste connectoren als beschikbare gegevensbronnen die u onder dit gatewaycluster kunt maken. Als u een gegevensbron met behulp van de nieuwe aangepaste connector maakt, kunt u nu Power BI-rapporten vernieuwen met behulp van deze aangepaste connector in Power BI-service.

![Aangepaste connector 3](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

* Zorg ervoor dat de map die u maakt toegankelijk is voor de gatewayservice voor de achtergrond. Normaal gesproken zijn mappen onder de map Windows of systeemmappen van uw gebruiker niet toegankelijk. In de on-premises gegevensgateway-app wordt een bericht weergegeven als de map niet toegankelijk is (dit geldt niet voor de persoonlijke versie van de gateway)
* In de code voor aangepaste connectoren moet een sectie TestConnection worden geïmplementeerd om deze te laten werken met de on-premises gegevensgateway. Dit is niet vereist als u de aangepaste connectoren voor Power BI Desktop gebruikt. U kunt om deze reden een connector hebben die met Power BI Desktop werkt, maar niet met de gateway. Raadpleeg [deze documentatie](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support) voor het implementeren van een TestConnection-sectie.

## <a name="next-steps"></a>Volgende stappen

* [Manage your data source - Analysis Services](service-gateway-enterprise-manage-ssas.md) (Uw gegevensbron beheren - Analysis Services)  
* [Manage your data source - SAP HANA](service-gateway-enterprise-manage-sap.md) (Uw gegevensbron beheren - SAP HANA)  
* [Manage your data source - SQL Server](service-gateway-enterprise-manage-sql.md) (Gegevensbron beheren - SQL Server)  
* [Manage your data source - Oracle](service-gateway-onprem-manage-oracle.md) (Gegevensbron beheren - Oracle)  
* [Manage your data source - Import/Scheduled refresh](service-gateway-enterprise-manage-scheduled-refresh.md) (Uw gegevensbron beheren - importeren/geplande vernieuwing)  

* [Proxyinstellingen configureren voor de on-premises gegevensgateway](/data-integration/gateway/service-gateway-proxy)  
* [Use Kerberos for SSO (single sign-on) from Power BI to on-premises data sources](service-gateway-sso-kerberos.md) (Kerberos gebruiken voor eenmalige aanmelding (SSO) van Power BI naar on-premises gegevensbronnen)  

Nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
