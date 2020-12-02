---
title: Problemen oplossen met een gegevensbron waarvoor vernieuwen niet wordt ondersteund
description: Problemen oplossen met een gegevensbron waarvoor vernieuwen niet wordt ondersteund
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 05/08/2020
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 4ab84a4f40acff894416fe2e5b33788c413ad4f5
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410753"
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>Problemen oplossen met een gegevensbron waarvoor vernieuwen niet wordt ondersteund
Mogelijk wordt er een fout weergegeven wanneer u een gegevensset probeert te configureren voor een geplande vernieuwing.

```output
You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.
```

Dit gebeurt wanneer de gegevensbron die u hebt gebruikt in Power BI Desktop de vernieuwingsbewerking niet ondersteunt. U moet de gegevensbron zoeken die u gebruikt en aan de hand van de lijst met ondersteunde gegevensbronnen in [Gegevens vernieuwen in Power BI](refresh-data.md) controleren of de gegevensbron wordt ondersteund. 

## <a name="find-the-data-source"></a>De gegevensbron zoeken
Als u niet zeker weet welke gegevensbron is gebruikt, kunt u dit controleren door de volgende stappen uit te voeren in Power BI Desktop.  

1. Zorg ervoor dat u het deelvenster **Rapport** weergeeft in Power BI Desktop.  
   ![Deelvenster Rapport in Desktop](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-report-pane.png)
2. Selecteer **Query's bewerken** in het lint.  
   ![Query's bewerken](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-edit-queries.png)
3. Selecteer **Geavanceerde editor**.  
   ![Geavanceerde editor](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-advanced-editor.png)
4. Noteer de provider die wordt vermeld voor de bron.  In dit voorbeeld is de provider Active Directory.  
   ![Gegevensbronprovider](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-provider.png)
5. Vergelijk de provider met de lijst van ondersteunde gegevensbronnen die in [Power BI-gegevensbronnen](power-bi-data-sources.md) zijn te vinden.

> [!NOTE]
> Zie [vernieuwen en dynamische gegevensbronnen](refresh-data.md#refresh-and-dynamic-data-sources) voor meer informatie over vernieuwingsproblemen met betrekking tot dynamische gegevensbronnen, waaronder gegevensbronnen met zelfgemaakte query's.


## <a name="next-steps"></a>Volgende stappen
[Gegevens vernieuwen](refresh-data.md)  
[Power BI Gateway - Personal](service-gateway-personal-mode.md)  
[On-premises data gateway](service-gateway-onprem.md) (On-premises gegevensgateway)  
[Problemen met de on-premises gegevensgateway oplossen](service-gateway-onprem-tshoot.md)  
[Problemen met Power BI Gateway - Personal oplossen](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
