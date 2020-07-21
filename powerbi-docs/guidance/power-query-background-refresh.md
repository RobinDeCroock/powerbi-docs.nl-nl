---
title: Power Query op de achtergrond vernieuwen uitschakelen
description: Richtlijnen voor het uitschakelen van Power Query op de achtergrond vernieuwen.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: 39eef27e746e636ddb331d28a930c1cd0dca0a5d
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2020
ms.locfileid: "86214926"
---
# <a name="disable-power-query-background-refresh"></a>Power Query op de achtergrond vernieuwen uitschakelen

Dit artikel is geschreven voor iedereen die Import-gegevensmodellen maakt met Power BI Desktop.

Als in Power Query gegevens worden geïmporteerd, worden voor elke query standaard tot 1.000 rijen met voorbeeldgegevens in de cache opgeslagen. Met voorbeeldgegevens kunt u een snel voorbeeld weergeven van brongegevens en van transformatieresultaten voor elke stap van uw query's. Deze worden afzonderlijk op schijf opgeslagen en niet in het Power BI Desktop-bestand.

Als uw Power BI Desktop-bestand echter veel query's bevat, kan het vernieuwen langer duren vanwege het ophalen en opslaan van voorbeeldgegevens.

## <a name="recommendation"></a>Aanbeveling

U kunt sneller vernieuwen door het Power BI Desktop-bestand in te stellen op het bijwerken van de voorbeeldcache _op de achtergrond_. In Power BI Desktop schakelt u dit in door _Bestand > Opties en instellingen > Opties_ te selecteren en vervolgens de pagina _Gegevens laden_ te selecteren. Vervolgens kunt u de optie **Toestaan dat voorbeeld van gegevens op de achtergrond wordt gedownload** inschakelen. Deze optie kan alleen worden ingesteld voor het huidige bestand.

![Schermopname van Power BI Desktop met de opties voor achtergrondgegevens.](media/power-query-background-refresh/power-query-options-background-data.png)

Het inschakelen van op de achtergrond vernieuwen kan ertoe leiden dat voorbeeldgegevens verouderd raken. Als dit gebeurt, ontvangt u de volgende waarschuwing van de Power Query-editor:

![Schermopname van Power BI Desktop met een waarschuwing voor de Power Query Editor over oude voorbeeldgegevens.](media/power-query-background-refresh/power-query-preview-data-old.png)

Het is altijd mogelijk om de voorbeeldcache bij te werken. U kunt deze bijwerken voor één query of voor alle query's met behulp van de opdracht **Voorbeeld vernieuwen**. U vindt deze opdracht op het lint **Start** van het venster van de Power Query-editor.

![Schermopname van Power BI Desktop met Power Query Editor-opdrachten voor het vernieuwen van voorbeeldgegevens.](media/power-query-background-refresh/power-query-refresh-preview-data.png)

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Power Query-documentatie](/power-query/)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
