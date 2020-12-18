---
title: Een rapport exporteren en e-mailen met Power Automate
description: In dit artikel gebruikt u Power Automate voor het automatiseren van het exporteren en distribueren van Power BI-rapporten in verschillende ondersteunde indelingen en scenario's.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Get started
ms.openlocfilehash: 45bccbefc6e499375d33aa049ead8a6c6e47bc8c
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098624"
---
# <a name="export-and-email-a-power-bi-report-with-power-automate"></a>Een Power BI-rapport exporteren en e-mailen met Power Automate

U kunt met [Power Automate](/power-automate/getting-started) het exporteren en distribueren van Power BI-rapporten naar verschillende indelingen en scenario's automatiseren. In dit artikel maakt u uw eigen volledig nieuwe stroom. U gebruikt de actie Exporteren naar bestand voor Power BI-rapport om automatisch een Power BI-rapport via e-mail te distribueren.

:::image type="content" source="media/service-automate-power-bi-report-export/automate-power-bi-report-overview.png" alt-text="Stappen van Power Automate om een rapport te exporteren en te e-mailen.":::

## <a name="prerequisites"></a>Vereisten  

Zorg ervoor dat u over het volgende beschikt:

- Ten minste één werkruimte in uw Power BI-tenant die wordt ondersteund door een gereserveerde capaciteit. Deze capaciteit kan een van de SKU's in het bereik A1/EM1 – A6/P3 zijn. Lees meer over [gereserveerde capaciteit in Power BI Premium](../admin/service-premium-what-is.md).
- Toegang tot de standaardconnectors in Power Automate, die worden geleverd bij een Office 365-abonnement.

## <a name="create-a-flow-from-scratch"></a>Een volledig nieuwe stroom maken 

In deze taak maakt u een eenvoudige volledig nieuwe stroom. De stroom exporteert een Power BI-rapport als PDF en koppelt dit aan een e-mailbericht dat wekelijks wordt verzonden.  

1. Meld u aan bij Power Automate (flow.microsoft.com).
2. Selecteer **Maken** > **Geplande stroom**. 

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-scheduled-flow-2.png" alt-text="Maak een geplande stroom in Power Automate.":::

3. Geef in **Een geplande stroom maken** uw stroom een naam. 
4. Selecteer in **Deze stroom uitvoeren** de begin datum en -tijd voor uw stroom op alsook de frequentie van herhalingen.
5. Selecteer in **Op deze dagen** de dagen waarop u de stroom wilt uitvoeren en selecteer **Maken**.

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-build-flow-5.png" alt-text="Power Automate, de stroom plannen.":::

6. Selecteer in **Terugkeerpatroon**  de **Geavanceerde opties weergeven** en voer een waarde in bij **Op deze uren** en **Op deze minuten** om een specifieke tijd in te stellen waarop de stroom wordt uitgevoerd.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-recurrence-6.png" alt-text="Stel in Power Automate het terugkeerpatroon in.":::

7. Selecteer **Nieuwe stap**.
8. In **Kies een actie**, zoekt u naar **Power BI** en selecteert u **Exporteren naar bestand voor Power BI-rapporten**.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-choose-action-8.png" alt-text="Kies een actie in Power Automate.":::

9. Selecteer in **Exporteren naar bestand voor Power BI-rapporten** en **Werkruimte** en **Rapport** in de vervolgkeuzelijsten.
10. Selecteer de gewenste **Exportindeling** voor uw Power BI-rapport.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-export-file-10.png" alt-text="Selecteer de exportindeling in Power Automate.":::

11. Geef eventueel specifieke pagina's op die u wilt exporteren in het veld **Pagina's paginaNaam -1**. Let erop dat de parameter voor de paginanaam afwijkt van de weergavenaam van de pagina. Zoek de naam van de pagina door te navigeren naar de pagina in de Power BI-service en het laatste deel van de URL te kopiëren.
 
     :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-copy-url-11.png" alt-text="Selecteer de deelvensternaam in de URL.":::

12. Geef eventueel een specifieke bladwijzer op die u wilt weergeven in het veld **Pagina’s bladwijzernaam**. Net als bij de parameter van de paginanaam vindt u de parameter van de bladwijzernaam in de rapport-URL. U kunt aanvullende parameters voor het Power BI-rapport opgeven. Gedetailleerde beschrijvingen van deze parameters vindt u in de [naslaginformatie over connectors voor de Power BI REST API](/connectors/powerbi/#export-to-file-for-power-bi-reports).

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-bookmark-url-12.png" alt-text="Selecteer de bladwijzernaam in de URL.":::

13. Selecteer **Nieuwe stap**.
14. In **Een actie kiezen**, zoekt u naar **Outlook** en selecteert u **Een e-mail (v2) verzenden**.
15. In **Een e-mail bericht (v2) verzenden** voltooit u de velden **Aan**, **Onderwerp** en **Hoofdtekst** voor uw e-mailbericht.
16. Selecteer **Geavanceerde opties weergeven**. Voer in **Naam van bijlagen – 1** een naam in voor uw bijlage. Voeg een bestandsextensie toe aan de naam van het bestand (bijvoorbeeld .PDF) die overeenkomt met de gewenste **Exportindeling**.
17. Selecteer in **Inhoud van bijlagen** **Bestandsinhoud** om het geëxporteerde Power BI-rapport bij te voegen.  
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-send-email-17.png" alt-text="Selecteer het geëxporteerde rapport naar de e-mail.":::

18. Wanneer u klaar bent, selecteert u **Volgende stap** of **Opslaan**. Power Automate maakt en evalueert de stroom en stelt u op de hoogte als er fouten zijn gevonden.
1. Als er fouten zijn, selecteert u  **Stroom bewerken**  om deze te herstellen. Als dat niet het geval is, selecteert u de pijl voor **terug** om de stroomgegevens weer te geven en om de nieuwe stroom uit te voeren.
    Wanneer u de stroom uitvoert, exporteert Power Automate een Power BI-rapport in de opgegeven indeling en verzonden als een e-mailbijlage zoals gepland.  

## <a name="next-steps"></a>Volgende stappen

- [Power BI-gegevenswaarschuwingen integreren met Power Automate](service-flow-integration.md)
- [Aan de slag met Power Automate](/power-automate/getting-started/)
- Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
