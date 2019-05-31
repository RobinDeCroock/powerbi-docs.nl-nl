---
title: Uw Power BI Embedded-capaciteit schalen | Microsoft Docs
description: Dit artikel biedt informatie over het schalen van Power BI Embedded-capaciteit in Microsoft Azure.
services: power-bi-embedded
author: rkarlin
ms.author: rkarlin
manager: kfile
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 01/31/2019
ms.openlocfilehash: b9a632fa39d320d14d1282cee5e59022a8ab0303
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61388432"
---
# <a name="scale-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Uw Power BI Embedded-capaciteit in Azure Portal schalen

Dit artikel biedt informatie over het schalen van Power BI Embedded-capaciteit in Microsoft Azure. Door te schalen kunt u uw capaciteit vergroten of verkleinen.

Hierbij wordt ervan uitgegaan dat u Power BI Embedded-capaciteit hebt gemaakt. Als u dat nog niet hebt gedaan, gaat u naar [Power BI Embedded-capaciteit maken in Azure Portal](azure-pbie-create-capacity.md) om aan de slag te gaan.

> [!NOTE]
> Het aanpassen van de schaal kan ongeveer een minuut duren. Gedurende deze tijd is de capaciteit niet beschikbaar. Ingesloten inhoud wordt mogelijk niet geladen.

## <a name="scale-a-capacity"></a>Capaciteit schalen

1. Meld u aan bij [Azure Portal](https://portal.azure.com/).

2. Selecteer **Alle services** > **Power BI Embedded** om uw capaciteiten te bekijken.

    ![Alle services in Azure Portal](media/azure-pbie-scale-capacity/azure-portal-more-services.png)

3. Selecteer de capaciteit die u wilt schalen.

    ![Lijst met Power BI Embedded-capaciteiten in Azure Portal](media/azure-pbie-scale-capacity/azure-portal-capacity-list.png)

4. Selecteer **Prijscategorie** bij **Schaal** in uw capaciteit.

    ![De optie Prijscategorie bij Schaal](media/azure-pbie-scale-capacity/azure-portal-scale-pricing-tier.png)

    De huidige prijscategorie is blauw gemarkeerd.

    ![Huidige prijscategorie blauw gemarkeerd](media/azure-pbie-scale-capacity/azure-portal-current-tier.png)

5. Als u omhoog of omlaag wilt schalen, selecteert u de categorie waarnaar u wilt overstappen. Wanneer u een nieuwe categorie hebt geselecteerd, wordt deze blauw gemarkeerd. Selecteer **Selecteren** om over te stappen naar de nieuwe categorie.

    ![Nieuwe categorie selecteren](media/azure-pbie-scale-capacity/azure-portal-select-new-tier.png)

    Het schalen van de capaciteit kan een of twee minuten duren.

6. Controleer of de juiste categorie nu is geselecteerd door naar het tabblad Overzicht te gaan. De huidige prijscategorie wordt vermeld.

    ![Huidige categorie bekijken](media/azure-pbie-scale-capacity/azure-portal-confirm-tier.png)

## <a name="next-steps"></a>Volgende stappen

Als u uw capaciteit wilt onderbreken of starten, ziet u [Uw Power BI Embedded-capaciteit onderbreken of starten in Azure Portal](azure-pbie-pause-start.md).

Als u Power BI-inhoud wilt insluiten in uw toepassing, ziet u [Uw Power BI-dashboards, -rapporten en -tegels insluiten](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
