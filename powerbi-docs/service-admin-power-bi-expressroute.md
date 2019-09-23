---
title: Power BI en ExpressRoute
description: Power BI en ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: c7d12bf6a1a2a02c988f8351a1844be1080ad2b8
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074801"
---
# <a name="power-bi-and-expressroute"></a>Power BI en ExpressRoute

**ExpressRoute** is een Azure-service waarmee u particuliere verbindingen kunt opzetten tussen Azure-datacenters (waarin Power BI zich bevindt) en uw on-premises infrastructuur, of particuliere verbindingen tussen Azure-datacenters en uw co-locatieomgeving.

Met **Power BI** en **ExpressRoute** kunt u een verbinding via een particulier netwerk opzetten tussen uw organisatie en Power BI (of met behulp van de co-locatievoorziening van een internetprovider), om zo internet te omzeilen en uw gevoelige gegevens en verbindingen van Power BI beter te beveiligen.

Raadpleeg [Overzicht van ExpressRoute](/azure/expressroute/expressroute-introduction) voor meer informatie. Power BI is compatibel met ExpressRoute, met een aantal uitzonderingen waarin Power BI gegevens ophaalt of verstuurt via het openbare internet. Raadpleeg [Power BI-URL's](power-bi-whitelist-urls.md) voor een lijst van de URL's die door Power BI worden gebruikt.

![ExpressRoute-diagram](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)