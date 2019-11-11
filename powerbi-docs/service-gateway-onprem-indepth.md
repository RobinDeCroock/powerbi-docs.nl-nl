---
title: On-premises gegevensgateway nader bekeken
description: In dit artikel wordt de on-premises gateway uitvoerig besproken. Er wordt gekeken hoe de service samenwerkt met Azure Active Directory en uw lokale Active Directory in combinatie met Analysis Services
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: e8807feeccccebab8837ac571ae4340c5c0c9b1a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881600"
---
# <a name="on-premises-data-gateway-in-depth"></a>On-premises gegevensgateway nader bekeken

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

We hebben de informatie uit dit artikel verplaatst naar verschillende artikelen in de Power BI- en algemene documentatie. Volg de koppelingen onder elke kop om de relevante inhoud te vinden.

## <a name="how-the-gateway-works"></a>Hoe de gateway werkt

Zie [Architectuur on-premises gegevensgateway](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="list-of-available-data-source-types"></a>Lijst met beschikbare typen gegevensbronnen

Zie [Gegevensbronnen beheren](service-gateway-data-sources.md).

## <a name="authentication-to-on-premises-data-sources"></a>Verificatie voor on-premises gegevensbronnen

Zie [Verificatie voor on-premises gegevensbronnen](/data-integration/gateway/service-gateway-onprem-indepth#authentication-to-on-premises-data-sources).

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Verificatie voor een live-gegevensbron van Analysis Services

Zie [Verificatie voor een live-gegevensbron van Analysis Services](service-gateway-enterprise-manage-ssas.md#authentication-to-a-live-analysis-services-data-source).

## <a name="role-based-security"></a>Beveiliging op basis van rollen

Zie [Beveiliging op basis van rollen](service-gateway-enterprise-manage-ssas.md#role-based-security).

## <a name="row-level-security"></a>Beveiliging op rijniveau

Zie [Beveiliging op rijniveau](service-gateway-enterprise-manage-ssas.md#row-level-security).

## <a name="what-about-azure-active-directory"></a>De rol van Azure Active Directory

Zie [Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#azure-active-directory).

## <a name="how-do-i-tell-what-my-upn-is"></a>Hoe weet ik wat mijn UPN is?

Zie [Hoe weet ik wat mijn UPN is?](/data-integration/gateway/service-gateway-onprem-indepth#how-do-i-tell-what-my-upn-is)

## <a name="map-user-names-for-analysis-services-data-sources"></a>Gebruikersnamen toewijzen voor gegevensbronnen van Analysis Services

Zie [Gebruikersnamen toewijzen voor gegevensbronnen van Analysis Services](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Een on-premises Active Directory synchroniseren met Azure Active Directory

Zie [Een on-premises Active Directory synchroniseren met Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#synchronize-an-on-premises-active-directory-with-azure-active-directory).

## <a name="what-to-do-next"></a>Volgende stap

Zie de artikelen over gegevensbronnen:

[Gegevensbronnen beheren](service-gateway-data-sources.md)
[Uw gegevensbron beheren - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Manage your data source - SAP HANA](service-gateway-enterprise-manage-sap.md) (Uw gegevensbron beheren - SAP HANA)  
[Manage your data source - SQL Server](service-gateway-enterprise-manage-sql.md) (Gegevensbron beheren - SQL Server)  
[Manage your data source - Oracle](service-gateway-onprem-manage-oracle.md) (Gegevensbron beheren - Oracle)  
[Manage your data source - Import/Scheduled refresh](service-gateway-enterprise-manage-scheduled-refresh.md) (Gegevensbron beheren - importeren/geplande vernieuwing)  

## <a name="where-things-can-go-wrong"></a>Aandachtspunten

Zie [Problemen met de on-premises gegevensgateway oplossen](/data-integration/gateway/service-gateway-tshoot) en [Problemen met gateways oplossen - Power BI](service-gateway-onprem-tshoot.md).

## <a name="sign-in-account"></a>Aanmeldingsaccount

Zie [Aanmeldingsaccount](/data-integration/gateway/service-gateway-onprem-indepth#sign-in-account).

## <a name="windows-service-account"></a>Windows-serviceaccount

Zie [Het serviceaccount van de on-premises gegevensgateway wijzigen](/data-integration/gateway/service-gateway-service-account).

## <a name="ports"></a>Poorten

Zie [Poorten](/data-integration/gateway/service-gateway-communication#ports).

## <a name="forcing-https-communication-with-azure-service-bus"></a>HTTPS-communicatie met Azure Service Bus afdwingen

Zie [HTTPS-communicatie met Azure Service Bus afdwingen](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus).

## <a name="support-for-tls-12"></a>Ondersteuning voor TLS 1.2

Zie [TLS 1.2 voor gatewayverkeer](/data-integration/gateway/service-gateway-communication#tls-12-for-gateway-traffic).

## <a name="how-to-restart-the-gateway"></a>De gateway opnieuw starten

Zie [Gateway opnieuw starten](/data-integration/gateway/service-gateway-restart).

## <a name="next-steps"></a>Volgende stappen

[Wat is een on-premises gegevensgateway?](service-gateway-onprem.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)