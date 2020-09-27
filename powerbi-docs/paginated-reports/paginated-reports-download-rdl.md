---
title: Het RDL-bestand voor een gepagineerd rapport downloaden vanuit een gegevensset
description: In dit artikel leert u hoe u het RDL-bestand voor een gepagineerd Power BI-rapport kunt downloaden vanuit een gedeelde gegevensset in de Power BI-service.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 09/16/2020
ms.openlocfilehash: a0b684403274a0ec69b184d8fb40486d6d2e3e27
ms.sourcegitcommit: cb606d3ae95300683caf1853e229d8981302a8e2
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/18/2020
ms.locfileid: "90764980"
---
# <a name="download-the-rdl-for-a-power-bi-paginated-report-from-a-dataset"></a>Het RDL-bestand voor een gepagineerd Power BI-rapport downloaden vanuit een gegevensset

In dit artikel leert u hoe u het RDL-bestand voor een gepagineerd Power BI-rapport kunt downloaden vanuit een gegevensset in de Power BI-service. Gepagineerde rapporten hebben de bestandsindeling *RDL*. U kunt een RDL-bestand rechtstreeks maken vanuit een gegevensset in de Power BI-service.

1. Ga naar de lijstweergave voor een werkruimte. Dit geldt ook voor Mijn werkruimte. 
1. Selecteer **Meer opties (...)** voor een gegevensset en selecteer vervolgens **RDL-bestand downloaden**.

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-paginated-download-rdl.png" alt-text="Schermopname van de optie RDL-bestand downloaden in de Power BI-service.":::
1. Er wordt een bericht weergegeven dat er enkele Power BI Report Builder-updates nodig zijn. Selecteer **Downloaden**. 

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-updates.png" alt-text="Schermopname van het installeren van Power BI Report Builder-updates.":::

    Als u weet dat u de meest recente versie van Power BI Report Builder hebt, selecteert u **Ik heb deze updates al geïnstalleerd**.

1. Voer het installatieproces van Power BI Report Builder uit: 

    1. Selecteer **Downloaden**.  
    2. Selecteer **Bestand openen** en voer de stappen uit in de installatiewizard Power BI Report Builder Setup.

1. Wanneer de installatie van Report Builder is voltooid, gaat u terug naar de Power BI-service en selecteert u **RDL-bestand downloaden**.

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-finished-installing.png" alt-text="Schermopname van het dialoogvenster RDL-bestand downloaden.":::

1. Selecteer **Bestand openen** in het browservenster.

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-paginated-open-file.png" alt-text="Schermopname van het selecteren van Bestand openen in een browser.":::

1. Power BI Report Builder wordt geopend met een automatisch gegenereerde titel en het PBIX-bestand van de Power BI-gegevensset in de map **Gegevensbronnen** . De gegevensbron heeft dezelfde naam als de Power BI-gegevensset.

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-design-canvas.png" alt-text="Schermopname van Power BI Report Builder in de ontwerpweergave.":::

    Het ontwerpoppervlak bevat ook een koppeling naar de videocursus [Gepagineerde Power BI-rapporten in een dag](../learning-catalog/paginated-reports-online-course.md). Als u geen ervaring hebt met het maken van gepagineerde rapporten, is de cursus een goede manier om hiermee snel aan de slag te gaan.  U kunt deze verwijderen wanneer u begint met het ontwerpen van uw rapport.

    U bent klaar om uw gepagineerde rapport te ontwerpen.
 
## <a name="next-steps"></a>Volgende stappen 

- [Wat zijn gepagineerde rapporten in Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
- [Zelfstudie: Een gepagineerd rapport maken en uploaden naar de Power BI-service](paginated-reports-quickstart-aw.md)
- [Een gepagineerd rapport publiceren in de Power BI-service](paginated-reports-save-to-power-bi-service.md)

