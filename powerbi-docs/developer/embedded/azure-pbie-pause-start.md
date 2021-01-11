---
title: Uw Power BI Embedded-capaciteit onderbreken en starten in Azure Portal voor uw ingesloten BI-oplossing voor ingesloten analyses in Power BI
description: Dit artikel biedt informatie over het onderbreken en starten van een Power BI Embedded-capaciteit in Microsoft Azure bij gebruik van uw ingesloten BI-oplossing voor ingesloten analyses in Power BI.
author: KesemSharabi
ms.author: kesharab
services: power-bi-embedded
editor: ''
tags: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 09/28/2017
ms.openlocfilehash: 0868d63f83f42bcfa9f394e782ffab56746e23cc
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887334"
---
# <a name="pause-and-start-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Uw Power BI Embedded-capaciteit onderbreken en starten in Azure Portal

Dit artikel biedt informatie over het onderbreken en starten van Power BI Embedded-capaciteit in Microsoft Azure. Hierbij wordt ervan uitgegaan dat u Power BI Embedded-capaciteit hebt gemaakt. Als u dat nog niet hebt gedaan, gaat u naar [Power BI Embedded-capaciteit maken in Azure Portal](azure-pbie-create-capacity.md) om aan de slag te gaan.

Als u nog geen abonnement op Azure hebt, maakt u een [gratis account](https://azure.microsoft.com/free/) voordat u begint.

## <a name="pause-your-capacity"></a>Capaciteit onderbreken

Als u capaciteit onderbreekt, worden er geen kosten in rekening gebracht. Het is handig om capaciteit te onderbreken als u de capaciteit gedurende een bepaalde periode niet nodig hebt. Voer de volgende stappen uit om uw capaciteit onderbreken.

> [!NOTE]
> Als u een capaciteit onderbreekt, kan dat ertoe leiden dat inhoud niet beschikbaar wordt gemaakt in Power BI. Zorg ervoor dat u de toewijzing van werkruimten aan uw capaciteit opheft voordat u een capaciteit onderbreekt. Op die manier voorkomt u mogelijke onderbrekingen.

1. Meld u aan bij [Azure Portal](https://portal.azure.com/).

2. Selecteer **Alle services** > **Power BI Embedded** om uw capaciteiten te bekijken.

    ![Alle services in Azure Portal](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Selecteer de capaciteit die u wilt onderbreken.

    ![Lijst met Power BI Embedded-capaciteiten in Azure Portal](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Selecteer **Onderbreken** in de capaciteitsgegevens.

    ![Capaciteit onderbreken](media/azure-pbie-pause-start/azure-portal-pause-capacity.png)

5. Selecteer **Ja**. Hiermee bevestigt u dat u de capaciteit wilt onderbreken.

    ![Onderbreken bevestigen](media/azure-pbie-pause-start/azure-portal-confirm-pause.png)

## <a name="start-your-capacity"></a>Capaciteit starten

U kunt het gebruik hervatten door de capaciteit te starten. Als u de capaciteit weer start, worden er ook weer kosten in rekening gebracht.

1. Meld u aan bij [Azure Portal](https://portal.azure.com/).

2. Selecteer **Alle services** > **Power BI Embedded** om uw capaciteiten te bekijken.

    ![Alle services in Azure Portal](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Selecteer de capaciteit die u wilt starten.

    ![Lijst met Power BI Embedded-capaciteiten in Azure Portal](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Selecteer **Starten** in de capaciteitsgegevens.

    ![Capaciteit starten](media/azure-pbie-pause-start/azure-portal-start-capacity.png)

5. Selecteer **Ja**. Hiermee bevestigt u dat u de capaciteit wilt starten.

    ![Starten bevestigen](media/azure-pbie-pause-start/azure-portal-confirm-start.png)

Als er inhoud is toegewezen aan deze capaciteit, wordt deze na het starten beschikbaar gemaakt.

## <a name="next-steps"></a>Volgende stappen

Als u uw capaciteit omhoog of omlaag wilt schalen, ziet u [Uw Power BI Embedded-capaciteit schalen](azure-pbie-scale-capacity.md).

Als u Power BI-inhoud wilt insluiten in uw toepassing, ziet u [Uw Power BI-dashboards, -rapporten en -tegels insluiten](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

Nog vragen? [Misschien dat de community van Power BI het antwoord weet](https://community.powerbi.com/).