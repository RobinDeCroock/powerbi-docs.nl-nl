---
title: Beperkingen van een service-principal
description: Beperkingen van een service-principal
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 06/06/2020
ms.custom: include file
ms.openlocfilehash: a8dd57b84f016ed798366898f4172ac9379ca26f
ms.sourcegitcommit: 02484b2d7a352e96213353702d60c21e8c07c6c0
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "91989656"
---
## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

* De service-principal werkt alleen met [nieuwe werkruimten](../collaborate-share/service-create-the-new-workspaces.md).
* **Mijn werkruimte** wordt niet ondersteund bij het gebruik van een service-principal.
* Een capaciteit is vereist voor het verplaatsen naar productie.
* U kunt zich niet aanmelden bij de Power BI-portal met behulp van een service-principal.
* Power BI-beheerdersrechten zijn vereist voor het inschakelen van de service-principal in instellingen voor ontwikkelaars in de Power BI-beheerportal.
* Voor [Insluiten voor uw organisatie](../developer/embedded/embed-sample-for-your-organization.md)-toepassingen kan geen service-principal worden gebruikt.
* Beheer van [gegevensstromen](../transform-model/service-dataflows-overview.md) wordt niet ondersteund.
* Service-principals bieden momenteel geen ondersteuning voor beheer-API's.
* Wanneer u de service-principal gebruikt met een [Azure Analysis Services](/azure/analysis-services/analysis-services-overview)-gegevensbron, moet de service-principal zelf machtigingen hebben voor Azure Analysis Services-instanties. Het gebruik van een beveiligingsgroep die de service-principal voor dit doel bevat, werkt niet.