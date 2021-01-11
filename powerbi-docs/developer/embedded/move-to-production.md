---
title: Uw toepassing voor ingesloten analyses in Power BI verplaatsen naar productie voor betere ingesloten BI-inzichten
description: Meer informatie over de stappen die nodig zijn om uw Power BI-toepassing naar productie te verplaatsen. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 06/02/2020
ms.openlocfilehash: 71eff0f09c0e34ffd8789f1b56347d754b6589bc
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886667"
---
# <a name="move-your-embedded-app-to-production"></a>Uw ingesloten app naar productie verplaatsen

Wanneer u de ontwikkeling van uw toepassing hebt afgerond, moet u uw werkruimte ondersteunen met een capaciteit als u de toepassing naar productie wilt verplaatsen.

> [!Important]
> Alle werkruimten (met rapporten, dashboards of gegevenssets) moeten worden toegewezen aan een capaciteit.

## <a name="create-a-capacity"></a>Een capaciteit maken

Als u een capaciteit maakt, kunt u ervan gebruikmaken dat u over een resource voor uw klanten beschikt. U kunt uit twee soorten capaciteiten kiezen:

* **Power BI Premium**: een Microsoft 356-abonnement op tenantniveau dat wordt aangeboden in twee SKU-series, *EM* en *P*. Bij het insluiten van Power BI-inhoud wordt deze oplossing aangeduid als *insluiten van Power BI*. Zie [Wat is Power BI Premium?](../../admin/service-premium-what-is.md) voor meer informatie over dit abonnement

* **Azure Power BI Embedded**: u kunt capaciteit kopen in de [Microsoft Azure-portal](https://portal.azure.com). Dit abonnement maakt gebruik van de *A*-SKU's. Zie [Power BI Embedded-capaciteit maken in Azure Portal](azure-pbie-create-capacity.md) voor meer informatie over het maken van Power BI Embedded-capaciteit.

    > [!NOTE]
    > Bij A-SKU's hebt u met een GRATIS Power BI-licentie geen toegang tot Power BI-inhoud.

### <a name="capacity-specifications"></a>Capaciteitsspecificaties

In de onderstaande tabel worden de resources en limieten van elke SKU beschreven. Als u wilt weten welke capaciteit het beste bij uw behoeften past, raadpleegt u de tabel [welke SKU moet ik kopen voor mijn scenario?](./embedded-faq.md#which-solution-should-i-choose).

| Capaciteitsknooppunten | Totaal aantal v-cores | v-cores voor back-end | RAM (GB) | v-cores voor front-end | DirectQuery/liveverbinding (per sec) | Model voor parallelle vernieuwing |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

## <a name="development-testing"></a>Ontwikkeltests

Voor het ontwikkelen van tests kunt u insluittokens als proef gebruiken met een Pro-licentie. Gebruik een capaciteit om items in te sluiten in een productieomgeving.

Het aantal insluittokens als proef dat een Power BI-*service-principal* of *hoofdgebruiker* (hoofdaccount) kan genereren, is beperkt. Gebruik de API [Beschikbare functies](/rest/api/power-bi/availablefeatures/getavailablefeatures) om het percentage van het huidige ingesloten gebruik te controleren. Het gebruiksbedrag wordt weergegeven per service-principal of hoofd account.

Als de insluittokens opraken tijdens het testen, moet u een Power BI Embedded of Premium-[capaciteit aanschaffen](embedded-capacity.md). Met een capaciteit kunt u een onbeperkt aantal insluittokens genereren.

## <a name="assign-a-workspace-to-a-capacity"></a>Werkruimte toewijzen aan een capaciteit

Zodra u capaciteit hebt gemaakt, kunt u uw werkruimte toewijzen aan die capaciteit.

Alle werkruimten die Power BI-resources bevatten die betrekking hebben op de ingesloten inhoud (inclusief gegevenssets, rapporten en dashboards), moeten worden toegewezen aan capaciteiten. Als bijvoorbeeld een ingesloten rapport en de gegevensset die hieraan is gekoppeld, zich in verschillende werkruimten bevinden, moeten beide werkruimten zijn toegewezen aan capaciteiten.

### <a name="assign-a-workspace-to-a-capacity-using-a-service-principal"></a>Een werkruimte toewijzen aan een capaciteit met behulp van een service-principal

Als u een capaciteit met behulp van een [service-principal](embed-service-principal.md) wilt toewijzen aan een werkruimte, gebruikt u de [Power BI REST API](/rest/api/power-bi/capacities/groups_assigntocapacity). Wanneer u de Power BI REST API's gebruikt, moet u de [object-id van de service-principal](embed-service-principal.md) gebruiken.

### <a name="assign-a-workspace-to-a-capacity-using-a-master-user"></a>Een werkruimte toewijzen aan een capaciteit met behulp van een hoofdgebruiker

Volg de onderstaande stappen om een capaciteit aan een werkruimte toe te wijzen met behulp van een **hoofdgebruiker**.

1. Open de werkruimte in de **Power BI-service**, selecteer de 

1. Vouw binnen **Power BI-service** werkruimten uit en selecteer het beletselteken voor de werkruimte die u gebruikt voor het insluiten van uw inhoud. Selecteer vervolgens **Werkruimten bewerken**.

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/workspace-settings.png" alt-text="Een schermopname van het menu werkruimte-instellingen in de Power BI-serviceportal.":::

2. Selecteer het tabblad **Premium** en ga als volgt te werk:

    * Schakel **Capaciteit** in.

    * Selecteer de capaciteit die u hebt gemaakt.

    * Selecteer **Opslaan**.

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-tab.png" alt-text="Een schermopname van het tabblad Premium-instellingen voor werkruimten in de Power BI-serviceportal.":::

    Nadat u uw werkruimte aan een capaciteit hebt toegewezen, wordt ernaast een ruit weergegeven 

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-workspace.png" alt-text="Een schermopname die de ruit weergeeft naast een werkruimte met een Premium-capaciteit in de Power BI-serviceportal.":::

## <a name="next-steps"></a>Volgende stappen

>[!div class="nextstepaction"]
>[Capaciteit en SKU's in Power BI Embedded-analyses](embedded-capacity.md)

>[!div class="nextstepaction"]
>[Capaciteitsplanning in ingesloten Power BI-analyse](embedded-capacity-planning.md)

>[!div class="nextstepaction"]
>[Overwegingen bij het genereren van een insluittoken](generate-embed-token.md)