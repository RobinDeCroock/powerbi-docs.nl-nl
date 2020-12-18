---
title: Een gepagineerd rapport opslaan in OneDrive voor Bedrijven of SharePoint Online
description: In dit artikel gebruikt u Power Automate om het opslaan van een gepagineerd Power BI-rapport in OneDrive voor Bedrijven of een SharePoint Online-map te automatiseren.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 11/17/2020
LocalizationGroup: Get started
ms.openlocfilehash: 6aaad48fb3e97aa6c1b4fc51834ee593a49a8192
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/11/2020
ms.locfileid: "97097726"
---
# <a name="save-a-paginated-report-to-onedrive-for-business-or-sharepoint-online"></a>Een gepagineerd rapport opslaan in OneDrive voor Bedrijven of SharePoint Online

U kunt met [Power Automate](/power-automate/getting-started) het exporteren en distribueren van gepagineerde Power BI-rapporten naar verschillende ondersteunde indelingen en scenario's automatiseren. In dit artikel gebruikt u Power Automate om het opslaan van een gepagineerd Power BI-rapport in OneDrive voor Bedrijven of een SharePoint Online-map te automatiseren.


:::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/paginated-onedrive-flow.png" alt-text="Schermafbeelding van de Power Automate-stroom voor het opslaan van een gepagineerd rapport in OneDrive of SharePoint Online":::

Bent u op zoek naar andere Power Automate-sjablonen voor gepagineerde Power BI-rapporten? Zie [Gepagineerde Power BI-rapporten exporteren met Power Automate](service-automate-paginated-integration.md). 

## <a name="prerequisites"></a>Vereisten  

Zorg ervoor dat u over het volgende beschikt:

- Ten minste één werkruimte in uw Power BI-tenant die wordt ondersteund door een gereserveerde capaciteit. Deze capaciteit kan een van de SKU's in het bereik A4/P1 – A6/P3 zijn. Lees meer over [gereserveerde capaciteit voor gepagineerde rapporten in Power BI Premium](../admin/service-premium-what-is.md#paginated-reports)
- Toegang tot de standaardconnectors in Power Automate, die worden geleverd bij een Office 365-abonnement.

## <a name="save-a-paginated-report-to-onedrive-for-business-or-a-sharepoint-online-folder"></a>Een gepagineerd rapport opslaan in OneDrive voor Bedrijven of een SharePoint Online-map 

Met een van deze twee sjablonen stelt u herhaaldelijke exports van een gepagineerd rapport in een gewenste indeling naar OneDrive voor Bedrijven of een SharePoint Online-map in. Bekijk de vereisten als u de actie Exporteren naar bestand voor gepagineerde rapporten in een Power Automate-stroom voor de eerste keer gebruikt. 

> [!NOTE]
> In de volgende stappen en afbeeldingen ziet u hoe u een stroom instelt met de sjabloon **Een gepagineerd Power BI-rapport opslaan in OneDrive voor Bedrijven**. Voer dezelfde stappen uit om een stroom te maken met de sjabloon **Een gepagineerd Power BI-rapport opslaan in een SharePoint Online-map**. Wanneer u selecteert waarheen u het gepagineerde rapport wilt exporteren, selecteert u een SharePoint Online-map in plaats van een OneDrive voor Bedrijven-map. 

1. Meld u aan bij Power Automate [flow.microsoft.com](https://flow.microsoft.com/). 
1. Selecteer **Sjablonen** en zoek naar  **gepagineerde rapporten**. 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Schermafbeelding van Power Automate-sjablonen voor gepagineerde Power BI-rapporten.":::

1. Selecteer **Een gepagineerd Power BI-rapport opslaan in OneDrive voor Bedrijven** of **Een gepagineerd Power BI-rapport opslaan in een SharePoint Online-map**. Zorg ervoor dat u bent aangemeld bij Power BI en OneDrive voor Bedrijven of SharePoint Online.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-step1.png" alt-text="Schermafbeelding van het selecteren van de sjabloon Power BI en OneDrive voor Bedrijven.":::
1. Selecteer **Doorgaan**.  


1. Als u het **herhalingspatroon** voor uw stroom wilt instellen, selecteert u een optie in **Frequentie** en voert u de waarde voor het gewenste **interval** in.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-2-recurrence.png" alt-text="het herhalingspatroon voor de stroom selecteren.":::

1. (Optioneel) Selecteer **Geavanceerde opties weergeven** om aanvullende parameters voor **Herhalingspatroon** in te stellen, zoals **Tijdzone**, **Begintijd**, **Op deze dagen**, **Op deze uren** en **Op deze minuten**.  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-3-advanced-recurrence.png" alt-text="geavanceerde opties voor het herhalingspatroon weergeven.":::

1. Selecteer in het vak **Werkruimte** een werkruimte in een gereserveerde capaciteit. Selecteer in het vak **Rapport** het gepagineerde rapport in de geselecteerde werkruimte dat u wilt exporteren. Selecteer in het vak **Exportindeling** de gewenste exportindeling. U kunt ook parameters opgeven voor het gepagineerde rapport. Gedetailleerde beschrijvingen van de parameters vindt u in de [naslaginformatie over connectors voor de Power BI REST API](/connectors/powerbi/#export-to-file-for-paginated-reports).  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-4-export-format.png" alt-text="het gepagineerde rapport, de werkruimte en de exportindeling selecteren.":::

1. Selecteer in **Mappad** de OneDrive voor Bedrijven- of SharePoint Online-map waarheen u het gepagineerde rapport wilt exporteren.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-5-create-file.png" alt-text="de bestemming selecteren en het bestand maken.":::

1. Power Automate genereert automatisch een **bestandsnaam** en **bestandsinhoud** voor u. U kunt de bestandsnaam wijzigen, maar de dynamisch gegenereerde waarde voor **Bestandsinhoud** behouden. 

1. Wanneer u klaar bent, selecteert u  **Volgende stap**  of **Opslaan**. Power Automate maakt en evalueert de stroom en stelt u op de hoogte als er fouten zijn gevonden. 

1. Als er fouten zijn, selecteert u  **Stroom bewerken**  om deze te herstellen. Als dat niet het geval is, selecteert u de pijl voor **terug** om de stroomgegevens weer te geven en om de nieuwe stroom uit te voeren. 

    Wanneer u de stroom uitvoert, exporteert Power Automate een gepagineerd rapport in de opgegeven indeling naar OneDrive voor Bedrijven of SharePoint Online.  

## <a name="next-steps"></a>Volgende stappen

- [Gepagineerde Power BI-rapporten exporteren met Power Automate](service-automate-paginated-integration.md)
- [Aan de slag met Power Automate](/power-automate/getting-started/)
- Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
