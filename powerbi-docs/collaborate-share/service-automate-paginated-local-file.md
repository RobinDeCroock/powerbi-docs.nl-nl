---
title: Een gepagineerd rapport opslaan in een lokale map met Power Automate
description: In dit artikel gebruikt u een sjabloon voor het instellen van terugkerende export van een gepagineerd rapport naar het bestandssysteem, in een gewenste indeling.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/08/2020
LocalizationGroup: Get started
ms.openlocfilehash: a30f0df972c375af4fb284ce3bba5372870d6efb
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098618"
---
# <a name="save-a-power-bi-paginated-report-to-a-local-folder--with-power-automate"></a>Een gepagineerd Power BI-rapport opslaan in een lokale map met Power Automate

U kunt met [Power Automate](/power-automate/getting-started) het exporteren en distribueren van gepagineerde Power BI-rapporten naar verschillende ondersteunde indelingen en scenario's automatiseren. In dit artikel gebruikt u een sjabloon voor het instellen van terugkerende export van een gepagineerd rapport naar het bestandssysteem, in een gewenste indeling. Bekijk de Vereisten als u de actie Exporteren naar bestand voor gepagineerde rapporten in een Power Automate-stroom voor de eerste keer gebruikt.

:::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-overview.png" alt-text="Stel terugkerende export van een gepagineerd rapport in.":::

Bent u op zoek naar andere Power Automate-sjablonen voor gepagineerde Power BI-rapporten? Zie [Gepagineerde Power BI-rapporten exporteren met Power Automate](service-automate-paginated-integration.md).

## <a name="prerequisites"></a>Vereisten  

Zorg ervoor dat u over het volgende beschikt:

- Ten minste één werkruimte in uw Power BI-tenant die wordt ondersteund door een gereserveerde capaciteit. Deze capaciteit kan een van de SKU's in het bereik A4/P1 – A6/P3 zijn. Lees meer over [gereserveerde capaciteit voor gepagineerde rapporten in Power BI Premium](../admin/service-premium-what-is.md#paginated-reports).
- Toegang tot de standaardconnectors in Power Automate, die worden geleverd bij een Office 365-abonnement.

## <a name="save-a-power-bi-paginated-report-to-a-local-folder"></a>Sla een gepagineerd Power BI-rapport in een lokale map

1. Selecteer de sjabloon **Een gepagineerd Power BI-rapport opslaan in een lokaal bestandssysteem**. Zorg ervoor dat u bent aangemeld bij Power BI en bent verbonden met uw lokale bestandssysteem. Selecteer **Doorgaan**. 

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-save-report-local-file-1.png" alt-text="Sla een gepagineerd Power BI-rapport op in een lokaal bestandssysteem":::.

2. Mogelijk moet u **Nieuwe verbinding toevoegen**  selecteren om verbinding te maken met uw bestandssysteem. 
1. Voer een **Verbindingsnaam** in, het pad naar de gewenste **Hoofdmap** en verificatie door uw **Gebruikersnaam** en **Wachtwoord** in te voeren. Selecteer een **gateway** uit de vervolgkeuzelijst als u een on-premises gegevensgateway gebruikt.

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-set-file-system-2.png" alt-text="Voer een Verbindingsnaam en een Hoofdmap in.":::
 
3. Als u de frequentie van het **Terugkeerpatroon** voor uw stroom wilt instellen, selecteert u een optie uit het vervolgkeuzelijst **Frequentie** en voert u de waarde voor het gewenste **Interval** in.  

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-frequency-3.png" alt-text="Stel de frequentie van het terugkeerpatroon voor uw stroom in.":::

4. Selecteer eventueel **Geavanceerde opties weergeven**. Stel aanvullende parameters voor het **Terugkeerpatroon**, zoals **Tijdzone**, **Begintijd**, **Op deze dagen**, **Op deze uren** en **Op deze minuten**. 
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-advanced-4.png" alt-text="Stel geavanceerde opties voor het terugkeerpatroon in.":::

5. Selecteer in het vak **Werkruimte** een werkruimte in een gereserveerde capaciteit waar het rapport zich bevindt. Selecteer in het vak **Rapport** het gepagineerde rapport dat u wilt exporteren in de werkruimte. Selecteer in het vak **Exportindeling** de gewenste exportindeling. U kunt ook parameters opgeven voor het gepagineerde rapport. U vindt gedetailleerde beschrijvingen van de parameters in de [naslaginformatie over connectors voor de Power BI REST API](/connectors/powerbi/#export-to-file-for-paginated-reports).  
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-select-workspace-report-5.png" alt-text="Selecteer de werkruimte en het rapport.":::

6. Selecteer in het dialoogvenster **Bestand maken** **Mappad** de map waarheen u het gepagineerde rapport wilt exporteren.
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-create-file-6.png" alt-text="Selecteer de map waarnaar u het gepagineerde rapport wilt exporteren":::

7. Power Automate genereert automatisch een **Bestandsnaam** en **Bestandsinhoud** voor u. U kunt de **Bestandsnaam** aanpassen, maar de dynamisch gegenereerde waarde voor **Bestandsinhoud** behouden.
8. Wanneer u klaar bent, selecteert u **Volgende stap** of **Opslaan**. De stroom wordt gemaakt en geëvalueerd in Power Automate.
9. Als Power Automate fouten vindt, selecteert u **Stroom bewerken** om ze te herstellen. Als dat niet het geval is, selecteert u de pijl voor Terug om de stroomgegevens weer te geven en om de nieuwe stroom uit te voeren.
10. Wanneer u de stroom uitvoert, exporteert Power Automate een gepagineerd rapport in de opgegeven indeling naar de geselecteerde map in uw bestandssysteem.

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-exported-10.png" alt-text="Power Automate-uitvoer exporteert een gepagineerd rapport in de opgegeven indeling.":::

## <a name="next-steps"></a>Volgende stappen

- [Gepagineerde Power BI-rapporten exporteren met Power Automate](service-automate-paginated-integration.md)
- [Aan de slag met Power Automate](/power-automate/getting-started/)
- Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

