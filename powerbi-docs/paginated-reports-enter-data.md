---
title: Rechtstreeks gegevens invoeren in een gepagineerd rapport in Report Builder (preview)
description: In dit artikel ziet u hoe u gegevens rechtstreeks in een gepagineerd rapport in Report Builder kunt invoeren.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/19/2018
ms.openlocfilehash: 3237f4751083f374ac00a959f226429b17757b50
ms.sourcegitcommit: 244d110b28d4978f360cbece3a7c896e1a645258
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61424315"
---
# <a name="enter-data-directly-in-a-paginated-report-in-report-builder-preview---power-bi"></a>Rechtstreeks gegevens invoeren in een gepagineerd rapport in Report Builder (preview) - Power BI

In dit artikel leest u meer over een functie in de nieuwe versie van SQL Server 2016 Report Builder waarmee u gegevens rechtstreeks als ingesloten gegevensset in een RDL-rapport kunt invoeren.  Deze functie is vergelijkbaar met Power BI Desktop. U kunt de gegevens rechtstreeks in een gegevensset in uw rapport typen of deze uit een ander programma plakken zoals Microsoft Excel. Nadat u een gegevensset hebt gemaakt door gegevens te hebben ingevoerd, kunt u deze set gebruiken zoals elke andere ingesloten gegevensset die u hebt gemaakt. Bovendien kunt u meer dan een tabel toevoegen en één tabel als filter voor de andere tabellen gebruiken. Deze functie is met name nuttig voor kleine, statische gegevenssets die u wellicht in uw rapport wilt gebruiken, zoals rapportparameters.
 
## <a name="prerequisites"></a>Vereisten

- Als u gegevens rechtstreeks in een gepagineerd rapport wilt invoeren, moet u de nieuwe versie van [Report Builder installeren via het Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53613). 
- Als u uw gepagineerde rapport wilt opslaan naar de Power BI-service, hebt u een [Power BI Pro-account](service-self-service-signup-for-power-bi.md) en schrijftoegang tot een werkruimte in een [Power BI Premium-capaciteit](service-premium-what-is.md) nodig.
- Als u uw gepagineerde rapport naar een rapportserver wilt opslaan, hebt u machtigingen nodig om [het bestand RsReportServer.config te bewerken](#upload-the-paginated-report-to-a-report-server).

## <a name="get-started"></a>Aan de slag

Nadat u Report Builder hebt gedownload en geïnstalleerd, volgt u dezelfde werkstroom die u gebruikt om een ingesloten gegevensbron en gegevensset aan uw rapport toe te voegen. In de volgende procedure ziet u onder **Gegevensbronnen** een nieuwe optie: **Gegevens invoeren**.  U hoeft deze gegevensbron maar eenmalig in een rapport in te stellen. Daarna kunt u meerdere tabellen maken met ingevoerde gegevens als afzonderlijke gegevenssets die elk die ene gegevensbron gebruiken.

1. In het deelvenster **Rapportgegevens** selecteert u **Nieuw** > **Gegevensset**.

    ![Nieuwe gegevensset voor Report Builder](media/paginated-reports-enter-data/paginated-new-dataset.png)

1. In het dialoogvenster **Eigenschappen van gegevensset** selecteert u **Een in mijn rapport ingesloten gegevensset gebruiken**.

1. Naast **Gegevensbron** selecteert u **Nieuw**.

    ![Nieuwe ingesloten gegevensbron](media/paginated-reports-enter-data/paginated-new-data-source.png)

1. In het dialoogvenster **Eigenschappen van gegevensbron** selecteert u **Een in mijn rapport ingesloten verbinding gebruiken**.
2. In het vak **Verbindingstype selecteren** selecteert u **GEGEVENS INVOEREN** > **OK**.

    ![Gegevensbron GEGEVENS INVOEREN](media/paginated-reports-enter-data/paginated-data-source-properties-enter-data.png)

1. In het dialoogvenster **Eigenschappen van gegevensset** selecteert u **Query Designer**.
2. In het deelvenster **Query Designer** klikt u met de rechtermuisknop en plakt u uw gegevens in de tabel.

    ![Gegevens invoeren in de Query Designer](media/paginated-reports-enter-data/paginated-enter-data.png)

1. Als u de kolomnamen wilt instellen, dubbelklikt u op elke **NewColumn** en typt u de kolomnaam.

    ![Kolomnamen instellen](media/paginated-reports-enter-data/paginated-column-name.png)

1. Als de eerste rij kolomkoppen van de oorspronkelijke gegevens bevat, klikt u met de rechtermuisknop en verwijdert u deze kolomkoppen.
    
9. Het gegevenstype voor elke kolom is standaard ingesteld op Tekenreeks. Als u het gegevenstype wilt wijzigen, klikt u met de rechtermuisknop op de kolomkop > **Type wijzigen** en stelt u deze in op een ander gegevenstype, zoals Datum of Float.

    ![Gegevenstype wijzigen](media/paginated-reports-enter-data/paginated-data-type.png)

1. Wanneer klaar bent met het maken van de tabel selecteert u **OK**.  

    De query die wordt gegenereerd, is dezelfde als de query die u ziet voor een XML-gegevensbron. Op de achtergrond gebruiken we XML als gegevensprovider.  We hebben deze aangepast zodat we ook dit scenario mogelijk kunnen maken.

    ![XML-gegevensstructuur](media/paginated-reports-enter-data/paginated-xml-data.png)

12. In het dialoogvenster **Eigenschappen van gegevensset** selecteert u **OK**.

13. U ziet uw gegevensbron en gegevensset in het deelvenster **Rapportgegevens**.

    ![Gegevensset in het deelvenster Rapportgegevens](media/paginated-reports-enter-data/paginated-report-data-pane.png)

U kunt uw gegevensset gebruiken als basis voor gegevensvisualisaties in uw rapport. U kunt ook nog een gegevensset toevoegen en hiervoor dezelfde gegevensbron gebruiken.

## <a name="upload-the-paginated-report-to-the-power-bi-service"></a>Een gepagineerd rapport uploaden naar de Power BI-service

Nu gepagineerde rapporten worden ondersteund in de Power BI-service in preview, kunt u uw gepagineerde rapport uploaden naar een Premium-capaciteit. Zie [Een gepagineerd rapport uploaden](paginated-reports-save-to-power-bi-service.md#upload-a-paginated-report) voor meer informatie.

## <a name="upload-the-paginated-report-to-a-report-server"></a>Upload het gepagineerde rapport naar een rapportserver

U kunt ook uw gepagineerde rapport uploaden naar een Power BI Report Server of SQL Server Reporting Services 2016- of 2017-rapportserver. Voordat u dit doet, moet u het volgende item toevoegen aan uw RsReportServer.config-bestand als extra gegevensextensie. Maak een back-up van uw RsReportServer.config-bestand voordat u de wijziging doorvoert, in het geval er problemen optreden.

```xml
<Extension Name="ENTERDATA" Type="Microsoft.ReportingServices.DataExtensions.XmlDPConnection,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <ConfigName>ENTERDATA</ConfigName>
    </Configuration>
</Extension>
```

Nadat de bewerking ziet de lijst met gegevensproviders in het configuratiebestand er als volgt uit:

![RsReportServer-configuratiebestand](media/paginated-reports-enter-data/paginated-rsreportserver-config-file.png)

Dat is alles. U kunt nu rapporten die van deze nieuwe functionaliteit gebruikmaken naar uw rapportserver publiceren.

## <a name="next-steps"></a>Volgende stappen

- [Wat zijn gepagineerde rapporten in Power BI Premium? (Preview)](paginated-reports-report-builder-power-bi.md)
- [Wat is Power BI Report Server?](report-server/get-started.md)
