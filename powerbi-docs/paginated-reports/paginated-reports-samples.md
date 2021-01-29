---
title: Voorbeeld van gepagineerde Power BI-rapporten
description: In dit artikel krijgt u informatie over het downloaden en gebruiken van voorbeelden van gepagineerde Power BI-rapporten.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/28/2021
ms.openlocfilehash: 282700151e605bd3571847b3b75f08e65f948e08
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/29/2021
ms.locfileid: "99044338"
---
# <a name="sample-power-bi-paginated-reports"></a>Voorbeeld van gepagineerde Power BI-rapporten


[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)]

Dit artikel biedt informatie en koppelingen naar verschillende voorbeelden van gepagineerde Power BI-rapporten die u kunt downloaden en verkennen. Ze laten zien op welke typische manieren u gepagineerde rapporten kunt gebruiken.

## <a name="prerequisites"></a>Vereisten

- U kunt deze rapporten online delen zonder ze te hoeven bewerken. U hebt hiervoor een Power BI Pro-licentie nodig. Meld u aan voor een [gratis proefversie van Power BI Pro-licentie](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro).
- Ook hebt u toegang tot een Power BI-werkruimte in een [Premium-capaciteit](../admin/service-premium-what-is.md) nodig.
- Als u deze rapporten wilt bewerken, moet u [Power BI Report Builder installeren](https://aka.ms/pbireportbuilder) vanuit het Microsoft Downloadcentrum.
- U bent nu klaar om deze voorbeelden van gepagineerde rapporten te downloaden bij GitHub. U hebt geen GitHub-account nodig. 

## <a name="download-the-reports"></a>De rapporten downloaden

Als u de rapporten wilt downloaden, moet u de opslagplaats downloaden als een ZIP-bestand en deze vervolgens uitpakken. Gepagineerde rapporten zijn RDL bestanden.

1. Open de [GitHub-opslagplaats Reporting Services](https://github.com/microsoft/Reporting-Services).
1. Selecteer de pijl op de groene knop **Code** > **ZIP-bestand downloaden**.

    :::image type="content" source="media/paginated-reports-samples/paginated-report-download-zip.png" alt-text="Schermopname van de GitHub-opslagplaats met de gepagineerde voorbeeldrapporten van Power BI.":::
    
1. Open het bestand, selecteer **Alles uitpakken** en kies een locatie voor de bestanden. De naam van de map is standaard **Reporting-Services-master**.
1. Open de map **Reporting-Services-master** en open vervolgens de map **PaginatedReportSamples**.

    >[!NOTE]
    >U kunt alle andere mappen in de map **Reporting-Services-master** verwijderen. Ze bevatten andere voorbeelden die u niet nodig hebt.

1. Selecteer een van de RDL-bestanden om deze in Power BI Report Builder te openen.
1. Nu kunt u [het gepagineerd rapport naar de Power BI-service publiceren](paginated-reports-save-to-power-bi-service.md).

## <a name="invoice"></a>Factuur

:::image type="content" source="media/paginated-reports-samples/paginated-report-invoice.png" alt-text="Schermopname van een voorbeeldfactuur van een gepagineerd Power BI-rapport.":::


Dit gepagineerde rapport is een zelfstandige factuur. Het scenario voor dit rapport is dat u een afdrukbare factuur wilt krijgen die tot op de pixel perfect is. Dit rapport moet de totale verkoop bevatten waarin beschrijvingen van artikelen, hoeveelheden, kortingen en kosten worden vermeld.

In dit voorbeeld worden unieke kenmerken uitgelicht voor het maken van echte facturen, zoals:  

- Een tablix (de onderliggende gegevensregio van zowel tabellen als matrices). Hierin wordt dynamisch gegenereerde, gebruikersspecifieke inhoud en een thema weergegeven.
- Een rechthoekig gegevensgebied wordt weergegeven op elke rij van de tablix van de rapporttekst.
- Rapportitems zoals tekstvakken en regels.
- Een rapportparameter om de inhoud dynamisch te selecteren. De inhoud die wordt weergegeven, is van toepassing op een specifiek onderwerp met behulp van tijdelijke aanduidingen van expressies. 

Gegevensbron: Opgenomen in het .rdl-bestand

## <a name="labels"></a>Labels

:::image type="content" source="media/paginated-reports-samples/paginated-report-labels.png" alt-text="Schermopname van gepagineerde rapportlabels.":::

Dit is een voorbeeld van een zelfstandig gepagineerd rapport. Het is een rapport met meerdere kolommen waarvan het formaat perfect aansluit bij de afdrukweergave van de mailinglabelsjabloon. 

Labelrapporten zijn eenvoudig, maar hebben wel een aantal unieke kenmerken voor het maken van een gepagineerd label:

- Een tablix met drie kolommen (vast aantal), met een gedefinieerde kolomafstand.
- Een rechthoekig gegevensgebied dat in alle rijen en kolommen op de afgedrukte pagina wordt herhaald.
- Een rapportparameter voor het selecteren van de inhoud die in elk rechthoekig gegevensgebied moet worden weergegeven.

Gegevensbron: Opgenomen in het .rdl-bestand

## <a name="mailing-letter"></a>Mailingbrief

:::image type="content" source="media/paginated-reports-samples/paginated-report-letter.png" alt-text="Schermopname van een voorbeeldbrief van een gepagineerd Power BI-rapport.":::

Dit voorbeeld van een zelfstandig gepagineerd rapport is ontworpen voor het maken van echte mailings. Het scenario voor dit rapport is dat u een afdrukbare brief met dynamische inhoud wilt krijgen die tot op de pixel perfect is.

Dit voorbeeld laat unieke kenmerken zien, zoals: 

- Een rechthoekig gegevensgebied wordt in verschillende delen in de rapporttekst geplaatst. 
- Afbeeldingen om de brief te personaliseren. 
- Een tablix-gegevensregio (de onderliggende gegevensregio van zowel tabellen als matrices). In de tablix wordt dynamisch gegenereerde, gebruikersspecifieke inhoud weergegeven.
- Rapportitems zoals tekstvakken en regels.
- Een rapportparameter om de inhoud dynamisch te selecteren. De inhoud die wordt weergegeven, is van toepassing op een specifiek onderwerp met behulp van tijdelijke aanduidingen van expressies. 

Gegevensbron: Opgenomen in het .rdl-bestand

## <a name="transcript"></a>Transcript

:::image type="content" source="media/paginated-reports-samples/paginated-report-transcript.png" alt-text="Schermopname van een voorbeeldtranscript van een gepagineerd Power BI-rapport.":::

Het scenario voor dit rapport is dat u een afdrukbaar transcript wilt krijgen dat tot op de pixel perfect is. Dit transcript moet dynamische inhoud bevatten met details van de programmabeschrijving en datums voor elke student.

Dit voorbeeld van een zelfstandig gepagineerd rapport heeft unieke kenmerken, zoals: 

- Een tablix-gegevensregio (de onderliggende gegevensregio van zowel tabellen als matrices). In de tablix wordt dynamisch gegenereerde, gebruikersspecifieke inhoud weergegeven aan de hand van geneste rijgroepen.
- Rechthoekige gegevensgebieden worden in verschillende delen in de rapporttekst geplaatst.
- Rapportitems zoals tekstvakken en regels.

Gegevensbron: Opgenomen in het .rdl-bestand

## <a name="sales-performance"></a>Verkoopprestaties

:::image type="content" source="media/paginated-reports-samples/paginated-report-sales-performance.png" alt-text="Schermopname van een voorbeeld van een gepagineerd Power BI-rapport voor Verkoopprestaties.":::

Verkoopprestaties van land is een voorbeeld van een zelfstandig gepagineerd rapport. Het scenario voor dit rapport is dat u een afdrukbare factuur wilt krijgen die tot op de pixel perfect is, zodat u de totale verkoop en details kunt bekijken. De volgende kenmerken zijn beschikbaar:

- Het gebruik van een parameter om details in de tabel uit te vouwen.
- Kop- en voetteksten.
- Rapportitems zoals tekstvakken, regels en rechthoeken met behulp van tijdelijke aanduidingen van expressies.
- Gegevensbalken.
- Trendlijnen.
- Meterpanelen.

Gegevensbron: Opgenomen in het .rdl-bestand

## <a name="regional-sales"></a>Regionale verkopen

:::image type="content" source="media/paginated-reports-samples/paginated-report-regional-sales.png" alt-text="Scherm afbeelding van het voor beeld-Power BI gepagineerd rapport voor regionale verkopen.":::

Regionale verkoop is een op zichzelf staand gepagineerd rapport voorbeeld. Het scenario voor dit rapport is dat u een pixel-perfect afdrukbaar rapport wilt weer geven van de totale omzet tegenover het quotum. De volgende kenmerken zijn beschikbaar:

- Het gebruik van een para meter om de geselecteerde Details in de tabel weer te geven.
- Kop- en voetteksten.
- Rapportitems zoals tekstvakken, regels en rechthoeken met behulp van tijdelijke aanduidingen van expressies.
- Meterpanelen.
- Lijn diagram geplaatst in de tabel.

Gegevensbron: Opgenomen in het .rdl-bestand

## <a name="organization-expenditures"></a>Organisatie uitgaven

:::image type="content" source="media/paginated-reports-samples/paginated-report-organization-expenditures.png" alt-text="Scherm afbeelding van het voor beeld-Power BI gepagineerd rapport voor organisatie-uitgaven.":::

Organisatie-uitgaven zijn een op zichzelf staand gepagineerd rapport voorbeeld. Het scenario voor dit rapport is dat u een in pixels perfecte afdruk bare onkosten rapport wilt weer geven van de onkosten in uw organisatie. De volgende kenmerken zijn beschikbaar:

- Kop- en voetteksten.
- Rapportitems zoals tekstvakken, regels en rechthoeken met behulp van tijdelijke aanduidingen van expressies.
- Grafieken zoals Treemap en Sun burst.

Gegevensbron: Opgenomen in het .rdl-bestand
  
## <a name="next-steps"></a>Volgende stappen

[Een gepagineerd rapport weergeven in de Power BI-service](../consumer/paginated-reports-view-power-bi-service.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
