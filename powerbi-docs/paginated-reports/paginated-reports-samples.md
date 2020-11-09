---
title: Voorbeeld van gepagineerde Power BI-rapporten
description: In dit artikel krijgt u informatie over het downloaden en gebruiken van voorbeelden van gepagineerde Power BI-rapporten.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/01/2020
ms.openlocfilehash: cf0e6a6e7cd40a5b8bb97560caf94b71c1b48e7a
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/04/2020
ms.locfileid: "93324018"
---
# <a name="sample-power-bi-paginated-reports"></a>Voorbeeld van gepagineerde Power BI-rapporten


[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)]

Dit artikel biedt informatie en koppelingen naar verschillende voorbeelden van gepagineerde Power BI-rapporten die u kunt downloaden en verkennen. Ze laten zien op welke typische manieren u gepagineerde rapporten kunt gebruiken.

## <a name="prerequisites"></a>Vereisten

- U kunt deze rapporten online delen zonder ze te hoeven bewerken. U hebt hiervoor een Power BI Pro-licentie nodig. Meld u aan voor een [gratis proefversie van Power BI Pro-licentie](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro).
- Ook hebt u toegang tot een Power BI-werkruimte in een [Premium-capaciteit](../admin/service-premium-what-is.md) nodig.
- Als u deze rapporten wilt bewerken, moet u [Power BI Report Builder installeren](https://aka.ms/pbireportbuilder) vanuit het Microsoft Downloadcentrum.
- U bent nu klaar om [deze voorbeelden van gepagineerde rapporten te downloaden](https://github.com/microsoft/Reporting-Services/tree/master/PaginatedReportSamples) bij GitHub. U hebt geen GitHub-account nodig. 


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
  
## <a name="next-steps"></a>Volgende stappen

[Een gepagineerd rapport weergeven in de Power BI-service](../consumer/paginated-reports-view-power-bi-service.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)