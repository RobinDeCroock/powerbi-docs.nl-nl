---
title: On-premises gegevensgateway
description: Dit artikel is een overzicht van de on-premises gegevensgateway voor Power BI. U kunt deze gateway gebruiken om te werken met DirectQuery-gegevensbronnen. U kunt deze gateway ook gebruiken om cloud-gegevenssets te vernieuwen met on-premises gegevens.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 07/15/2019
ms.openlocfilehash: 883d5c83019df293628d096f5834c9b5c6d425b6
ms.sourcegitcommit: 73228d0a9038b8369369c059ad06168d2c5ff062
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/02/2019
ms.locfileid: "68730275"
---
# <a name="what-is-an-on-premises-data-gateway"></a>Wat is een on-premises gegevensgateway?

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

De on-premises gegevensgateway fungeert als een brug waarmee u over snelle en veilige gegevensoverdracht beschikt tussen on-premises gegevens (gegevens die zich niet in de cloud bevinden) en diverse Microsoft-cloudservices. Deze cloudservices omvatten Power BI, PowerApps, Microsoft Flow, Azure Analysis Services en Azure Logic Apps. Door een gateway te gebruiken kunnen organisaties databases en andere gegevensbronnen in hun on-premises netwerken houden en deze on-premises gegevens toch veilig gebruiken in cloudservices.

## <a name="how-the-gateway-works"></a>Hoe de gateway werkt

![Overzicht van de gateway](media/service-gateway-onprem/on-premises-data-gateway.png)

Zie [Architectuur on-premises gegevensgateway](/data-integration/gateway/service-gateway-onprem-indepth) voor meer informatie over de werking van de gateway.

## <a name="types-of-gateways"></a>Typen gateways

Er zijn twee verschillende soorten gateways, elk voor een ander scenario:

* Met een **on-premises gegevensgateway** kunnen meerdere gebruikers verbinding maken met meerdere on-premises gegevensbronnen. U kunt een on-premises gegevensgateway gebruiken met alle ondersteunde services, met één gatewayinstallatie. Deze gateway is geschikt voor complexe scenario's waarbij meerdere personen toegang moeten krijgen tot meerdere gegevensbronnen.

* Met de **on-premises gegevensgateway (persoonlijke modus)** kan één gebruiker verbinding maken met bronnen. Delen met anderen is niet mogelijk. Een on-premises gegevensgateway (persoonlijke modus) kan alleen worden gebruikt met Power BI. Deze gateway is geschikt voor scenario's waarin u de enige bent die rapporten maakt en u geen gegevensbronnen met anderen hoeft te delen.

## <a name="use-a-gateway"></a>Een gateway gebruiken

Er zijn vier hoofdstappen voor het gebruik van een gateway.

1. [Download en installeer de gateway](/data-integration/gateway/service-gateway-install) op een lokale computer.
2. [Configureer](/data-integration/gateway/service-gateway-app) de gateway op basis van uw firewall- en andere netwerkvereisten.
3. [Voeg gatewaybeheerders](/data-integration/gateway/service-gateway-manage) toe die ook andere netwerkvereisten kunnen beheren.
4. [Los gatewayproblemen op](service-gateway-onprem-tshoot.md) als er fouten optreden.

## <a name="next-steps"></a>Volgende stappen

* [De on-premises gegevensgateway installeren](/data-integration/gateway/service-gateway-install)


Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
