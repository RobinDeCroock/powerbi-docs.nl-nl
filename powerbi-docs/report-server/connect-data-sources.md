---
title: Gegevensbronnen voor gepagineerde rapporten in Power BI Report Server
description: Meer informatie over gegevensbronnen waarmee gepagineerde rapporten (.rdl) in Power BI Report Server verbinding kunnen maken.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 06/26/2020
ms.author: maggies
ms.openlocfilehash: fcf0a286487922fcfc217b4d293aa731ad1564a6
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861217"
---
# <a name="paginated-report-data-sources--in-power-bi-report-server"></a>Gegevensbronnen voor gepagineerde rapporten in Power BI Report Server
Gepagineerde rapporten van Reporting Services in Power BI Report Server ondersteunen dezelfde gegevensbronnen die worden ondersteund in SQL Server Reporting Services. Zie de lijst met [gegevensbronnen die worden ondersteund door Reporting Services](/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

## <a name="connect-to-oracle-data-sources-with-useinstalleduiculture"></a>Verbinding maken met Oracle-gegevensbronnen met behulp van UseInstalledUICulture

Om verbinding te maken met Oracle-gegevensbronnen maakt Power BI Report Server gebruik van de Oracle-gegevensprovider voor .NET (ODP.NET), die NLS-agnostisch is.

De rapportserver maakt standaard gebruik van de UI-cultuur van de eerste client om ODP.NET te laden.  Als gevolg hiervan zijn alle volgende verbindingen met Oracle vanaf de rapportserver ook in deze oorspronkelijke UI-cultuur, totdat de service opnieuw wordt gestart.  Deze aanpak kan problemen veroorzaken bij de weergave van een rapport, vanwege verschillen in de indeling van de UI-culturen.

We hebben een configuratie-instelling geïntroduceerd met de naam UseInstalledUICulture, om een betere ervaring te bieden in Power BI Report Server. Wanneer UseInstalledUICulture is ingesteld op True, laadt de rapportserver ODP.NET altijd in de UI-cultuur van de server, in plaats van in de cultuur van de eerste client.
Deze instelling is vanaf de servicerelease van maart 2020 beschikbaar in Power BI Report Server.

Als u de functie wilt inschakelen, wijzigt u de vermelding voor de ORACLE-extensie in het bestand rsreportserver.config zoals hieronder.
```xml
<Extension Name="ORACLE" Type="Microsoft.ReportingServices.DataExtensions.OracleClientConnectionWrapper,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <UseInstalledUICulture>true</UseInstalledUICulture>
    </Configuration>
</Extension>
```

## <a name="next-steps"></a>Volgende stappen
Nu u verbinding hebt met uw gegevensbron,kunt u [een gepagineerd rapport maken](quickstart-create-paginated-report.md).  


Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)