---
title: Een gepagineerd rapport exporteren voor elke rij in een Excel Online-tabel of SharePoint-lijst
description: In dit artikel gebruikt u Power Automate om het exporteren van een gepagineerd rapport te automatiseren voor elke rij in een Excel Online-tabel of SharePoint Online-lijst.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 11/17/2020
LocalizationGroup: Get started
ms.openlocfilehash: 74d61d40c4447f2649f5cce5fbcdcba68cd31afe
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96407993"
---
# <a name="export-a-paginated-report-for-each-row-in-an-excel-online-table-or-sharepoint-list"></a>Een gepagineerd rapport exporteren voor elke rij in een Excel Online-tabel of SharePoint-lijst

U kunt met [Power Automate](/power-automate/getting-started) het exporteren en distribueren van gepagineerde Power BI-rapporten naar verschillende ondersteunde indelingen en scenario's automatiseren. In dit artikel gebruikt u een Power Automate-sjabloon om het instellen van herhaaldelijke exports van een of meer gepagineerde rapporten te automatiseren. U exporteert deze in een gewenste indeling voor elke rij in een Excel Online-tabel of SharePoint Online-lijst. U kunt het geëxporteerde gepagineerde rapport distribueren naar OneDrive voor Bedrijven of een SharePoint Online-site, of dit per e-mailen verzenden via Office 365 Outlook.

:::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-overview.png" alt-text="Een gepagineerd rapport exporteren met behulp van een Excel Online-tabel.":::

Elke rij in uw Excel Online-tabel of SharePoint Online-lijst kan staan voor één gebruiker die een gepagineerd rapport ontvangt op basis van een abonnement. Anderzijds kan elke rij ook staan voor een uniek gepagineerd rapport dat u wilt distribueren. Uw tabel of lijst moet een kolom bevatten waarin wordt aangegeven hoe een rapport wordt gedistribueerd, via OneDrive, SharePoint Online of Outlook. De Power Automate-stroom gebruikt deze kolom in de Switch-instructie.

Bent u op zoek naar andere Power Automate-sjablonen voor gepagineerde Power BI-rapporten? Zie [Gepagineerde Power BI-rapporten exporteren met Power Automate](service-automate-paginated-integration.md).

## <a name="prerequisites"></a>Vereisten  

Zorg ervoor dat u over het volgende beschikt:

- Ten minste één werkruimte in uw Power BI-tenant die wordt ondersteund door een gereserveerde capaciteit. Deze capaciteit kan een van de SKU's in het bereik A4/P1 – A6/P3 zijn. Lees meer over [gereserveerde capaciteit in Power BI Premium](../admin/service-premium-what-is.md).
- Toegang tot de standaardconnectors in Power Automate, die worden geleverd bij een Office 365-abonnement.
- Als u een Excel Online-tabel gebruikt, moet deze zijn opgemaakt als een tabel in Excel. Zie [Een tabel maken](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f) voor meer informatie.

## <a name="export-a-paginated-report-for-each-row-in-a-table-or-list"></a>Een gepagineerd rapport voor elke rij in een tabel of lijst exporteren

> [!NOTE]
> In de volgende stappen en afbeeldingen ziet u hoe u een stroom instelt met de sjabloon **Een gepagineerd Power BI-rapport exporteren voor elke rij in een Excel Online-tabel**. U kunt dezelfde stappen uitvoeren om een stroom te maken met de sjabloon **Een gepagineerd Power BI-rapport exporteren voor items in een SharePoint Online-lijst**. In tegenstelling tot een Excel Online-tabel bevat een SharePoint Online-lijst de informatie over het exporteren van het gepagineerde rapport.  

1. Meld u aan bij Power Automate [flow.microsoft.com](https://flow.microsoft.com/). 
1. Selecteer **Sjablonen** en zoek naar  **gepagineerde rapporten**. 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Schermafbeelding van Power Automate-sjablonen voor gepagineerde Power BI-rapporten.":::

1. Selecteer de sjabloon **Een gepagineerd Power BI-rapport exporteren voor elke rij in een Excel Online-tabel** of de sjabloon **Een gepagineerd Power BI-rapport exporteren voor items in een SharePoint Online-lijst**. Zorg ervoor dat u bent aangemeld bij Excel Online, Power BI, OneDrive voor Bedrijven, SharePoint Online en Office 365 Outlook. Selecteer **Doorgaan**.  

   :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-excel-online-1.png" alt-text="Een gepagineerd Power BI-rapport exporteren voor elke rij in een Excel Online-tabel.":::

1. Als u het **herhalingspatroon** voor uw stroom wilt instellen, selecteert u een optie in **Frequentie** en voert u de waarde voor het gewenste **interval** in.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-recurrence-2.png" alt-text="Selecteer herhalingspatroon voor uw stroom.":::

1. (Optioneel) Selecteer **Geavanceerde opties weergeven** om aanvullende parameters voor **Herhalingspatroon** in te stellen, zoals **Tijdzone**, **Begintijd**, **Op deze dagen**, **Op deze uren** en **Op deze minuten**.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-advanced-recurrence-3.png" alt-text="Optioneel, selecteer geavanceerde opties voor herhalingspatroon.":::

1. Selecteer in het vak **Locatie** de optie OneDrive voor Bedrijven of de SharePoint Online-site waar uw Excel Online-tabel of SharePoint Online-lijst wordt opgeslagen. Selecteer vervolgens de **Documentbibliotheek** in de vervolgkeuzelijst.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-location-4.png" alt-text="Selecteer de locatie van de Excel Online-tabel.":::

1. Selecteer het Excel Online-bestand of de SharePoint Online-lijst in het vak **Bestand**. Selecteer de naam van de tabel of lijst in de vervolgkeuzelijst in het vak **Tabel**. 
 
    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-file-table-5.png" alt-text="Selecteer het Excel Online-bestand en de naam van de tabel.":::

    > [!TIP]
    > Raadpleeg [Een tabel maken](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f) om te zien hoe u gegevens opmaakt als een tabel in Excel. 

1. Initialiseer een variabele die wordt gebruikt voor de bestandsnaam. U kunt de standaardwaarden voor **Naam** en **Waarde** behouden of wijzigen, maar laat de waarde voor **Type** ongewijzigd op **Tekenreeks**.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-name-type-6.png" alt-text="Vul de naam en waarde in en laat de waarde voor Type ongewijzigd op Tekenreeks.":::

1. In **Op elke toepassen** is het vak **Selecteer een uitvoer uit de vorige stap** standaard ingesteld op **Waarde**. Deze instelling doorloopt de acties die zijn opgenomen in **Op elke toepassen** voor elke rij in uw Excel Online-tabel of SharePoint Online-lijst.  

1. Selecteer in het vak **Werkruimte** een werkruimte in een toegewezen capaciteit. Selecteer in het vak **Rapport** het gepagineerde rapport in de geselecteerde werkruimte dat u wilt exporteren. Als u **Een aangepaste waarde invoeren** instelt in de vervolgkeuzelijst, kunt u **Werkruimte** en **Rapport** instellen op een kolom in uw Excel Online-tabel of SharePoint Online-lijst. Deze kolommen moeten respectievelijk werkruimte-id's en rapport-id's bevatten.  

1. Selecteer in de vervolgkeuzelijst een **exportindeling** of stel deze in op een kolom in uw Excel Online-tabel die de gewenste exportindelingen bevat. bijvoorbeeld PDF, DOCX of PPTX. U kunt ook parameters opgeven voor het gepagineerde rapport. Gedetailleerde beschrijvingen van de parameters vindt u in de [naslaginformatie over connectors voor de Power BI Rest API](/connectors/powerbi/#export-to-file-for-paginated-reports).

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-export-format-9.png" alt-text="Vul Exporteren naar bestand voor gepagineerde rapporten in.":::

1. Voer in het vak **Waarde** een naam in voor het gepagineerde rapport nadat dit is geëxporteerd. Zorg ervoor dat u een bestandsextensie opgeeft. U kunt deze statisch instellen, bijvoorbeeld .pdf, .docx of .pptx. U kunt deze ook dynamisch instellen door de kolom in de Excel-tabel voor de gewenste exportindeling te selecteren. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-output-value-10.png" alt-text="Selecteer de naam van het rapport en een bestandsextensie.":::

1. Vul in de actie **Schakelen** het vak **In** met de kolom in uw Excel Online-tabel die overeenkomt met de gewenste leveringsmethode: **OneDrive**, **SharePoint** of **E-mail**. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-switch-11.png" alt-text="Vul in Schakelen het vak In met de kolom in uw Excel Online-tabel.":::

1. In **Geval 1**, **Geval 2** en **Geval 3** voert u de waarden in die zijn opgenomen in de kolom in de Excel Online-tabel die is geselecteerd in de vorige stap.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-1-2-3-12.png" alt-text="Voer waarden in voor Geval 1, Geval 2 en Geval 3.":::

1. Als u het gepagineerde rapport opslaat in OneDrive, selecteert u het **mappad** waar het moet worden opgeslagen.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-onedrive-13.png" alt-text="In het geval dat u het rapport opslaat in OneDrive.":::

1. Als u het gepagineerde rapport opslaat in SharePoint Online, voert u het **siteadres** en het **mappad** in waar het rapport moet worden opgeslagen. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-sharepoint-14.png" alt-text="In het geval dat u het gepagineerde rapport opslaat in SharePoint Online.":::

1. Als u het gepagineerde rapport verzendt als e-mailbericht via Outlook, vult u de vakken **Naar**, **Onderwerp** en **Hoofdtekst** in. Deze vakken kunnen statische inhoud of dynamische inhoud uit de Excel Online-tabel of SharePoint Online-lijst bevatten. Power Automate koppelt uw gepagineerde rapport automatisch aan dit e-mailbericht.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-email-15.png" alt-text="In het geval dat u het gepagineerde rapport verzendt als e-mailbericht via Outlook.":::

1. Wanneer u klaar bent, selecteert u  **Volgende stap**  of **Opslaan**. Power Automate maakt en evalueert de stroom en stelt u op de hoogte als er fouten zijn gevonden. 

1. Als er fouten zijn, selecteert u  **Stroom bewerken**  om deze te herstellen. Als dat niet het geval is, selecteert u de pijl voor **terug** om de stroomgegevens weer te geven en de nieuwe stroom uit te voeren. 


## <a name="next-steps"></a>Volgende stappen

- [Gepagineerde Power BI-rapporten exporteren met Power Automate](service-automate-paginated-integration.md)
- [Aan de slag met Power Automate](/power-automate/getting-started/)
- Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

