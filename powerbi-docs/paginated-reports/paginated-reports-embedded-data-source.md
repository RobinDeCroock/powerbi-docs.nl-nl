---
title: Ingesloten gegevensbronnen voor gepagineerde rapporten in de Power BI-service
description: In dit artikel leert u hoe u een ingesloten gegevensbron maakt en wijzigt in een gepagineerd rapport in de Power BI-service.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 03/02/2020
ms.openlocfilehash: 29ed0a764773c2252989aa05bfcabe5976472d11
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297831"
---
# <a name="create-an-embedded-data-source-for-paginated-reports-in-the-power-bi-service"></a>Een ingesloten gegevensbron voor gepagineerde rapporten maken in de Power BI-service

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

In dit artikel leert u hoe u een ingesloten gegevensbron maakt en wijzigt voor een gepagineerd rapport in de Power BI-service. U definieert een ingesloten gegevensbron in een specifiek rapport en gebruikt de bron vervolgens alleen in dat rapport. Momenteel zijn voor rapporten die in de Power BI-service zijn gepubliceerd, ingesloten gegevenssets en ingesloten gegevensbronnen nodig. Gepagineerde rapporten kunnen worden verbonden met deze gegevensbronnen:

- Azure Analysis Services
- Azure SQL-database en 
- Azure SQL Data Warehouse
- SQL Server
- SQL Server Analysis Services
- Oracle 
- Teradata 

Gebruik de optie [SQL Server Analysis Services-verbinding](../admin/service-premium-connect-tools.md) voor de volgende gegevensbronnen:

- Power BI Premium-gegevenssets

Gepagineerde rapporten maken via een [Power BI-gateway](../connect-data/service-gateway-onprem.md)-verbinding met on-premises gegevensbronnen. U stelt de gateway in nadat u het rapport naar de Power BI-service hebt gepubliceerd.

Zie [Rapportgegevens in Power BI Report Builder](report-builder-data.md) voor meer informatie.

## <a name="create-an-embedded-data-source"></a>Een ingesloten gegevensbron maken
  
1. Open Power BI Report Builder.

1. Selecteer **Nieuw** > **Gegevensbron** op de werkbalk in het deelvenster Rapportgegevens. Het dialoogvenster **Eigenschappen van gegevensbron** wordt geopend.

   ![Nieuwe gegevensbron](media/paginated-reports-embedded-data-source/power-bi-paginated-new-data-source.png)
  
1. Typ in het tekstvak **Naam** een naam voor de gegevensbron of accepteer de standaardwaarde.  
  
1. Selecteer **Een ingesloten verbinding in mijn rapport gebruiken**.  
  
1. Selecteer een type gegevensbron in de lijst **Verbindingstype selecteren**. 

1. Geef op een van de volgende manieren een verbindingsreeks op:  
  
   - Typ de verbindingsreeks rechtstreeks in het tekstvak **Verbindingsreeks**. 
  
   - Selecteer **Bouwen** om het dialoogvenster **Verbindingseigenschappen** te openen voor de gegevensbron die u hebt gekozen in stap 2.  
  
     Vul de velden in het dialoogvenster **Verbindingseigenschappen** in op basis van het type gegevensbron. Voorbeelden van eigenschappen van de verbinding zijn het type van de gegevensbron, de naam van de gegevensbron en de te gebruiken referenties. Nadat u waarden hebt opgegeven in dit dialoogvenster, selecteert u **Verbinding testen** om te controleren of de gegevensbron beschikbaar is en of de opgegeven referenties juist zijn.  
  
1. Selecteer **Referenties**.  
  
   Geef de referenties op die u wilt gebruiken voor deze gegevensbron. De eigenaar van de gegevensbron kiest welke typen referenties worden ondersteund. Zie [Specify Credential and Connection Information for Report Data Sources](/sql/reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources) (Referentie en verbindingsgegevens opgeven voor rapportgegevensbronnen) voor meer informatie.
  
1. Selecteer **OK**.  
  
   De gegevensbron wordt weergegeven in het deelvenster Rapportgegevens.

## <a name="limitations-and-considerations"></a>Beperkingen en overwegingen

Voor gepagineerde rapporten die verbinding maken met Power BI-gegevenssets worden de regels voor gedeelde gegevenssets in Power BI gebruikt, met een aantal kleine wijzigingen.  Als u wilt dat gebruikers gepagineerde rapporten goed kunnen weergeven met behulp van Power BI-gegevenssets en om ervoor te zorgen dat beveiliging op rijniveau (RLS) is ingeschakeld en wordt afgedwongen voor uw kijkers, dan moet u deze regels volgen:

### <a name="classic-apps-and-workspaces"></a>Klassieke apps en werkruimten

- .rdl in dezelfde werkruimte als de gegevensset (dezelfde eigenaar): Ondersteund
- .rdl in een andere werkruimte als de gegevensset (dezelfde eigenaar): Ondersteund
- Gedeelde .rdl: Er moeten leesmachtigingen op gegevenssetniveau zijn toegewezen aan elke gebruiker die het rapport bekijkt
- Gedeelde app: Er moeten leesmachtigingen op gegevenssetniveau zijn toegewezen aan elke gebruiker die het rapport bekijkt
- .rdl in dezelfde werkruimte als de gegevensset (andere gebruiker): Ondersteund
- .rdl in een andere werkruimte dan de gegevensset (andere gebruiker): er moeten leesmachtigingen op gegevenssetniveau zijn toegewezen aan elke gebruiker die het rapport bekijkt
- Beveiliging op rijniveau: Er moeten leesmachtigingen op gegevenssetniveau zijn toegewezen aan elke gebruiker die het rapport bekijkt om dit af te dwingen.

### <a name="new-experience-apps-and-workspaces"></a>Nieuwe ervarings-apps en werkruimten

- .rdl in dezelfde werkruimte als de gegevensset: Ondersteund
- .rdl in een andere werkruimte als de gegevensset (dezelfde eigenaar): Ondersteund
- Gedeelde .rdl: Er moeten leesmachtigingen op gegevenssetniveau zijn toegewezen aan elke gebruiker die het rapport bekijkt
- Gedeelde app: Er moeten leesmachtigingen op gegevenssetniveau zijn toegewezen aan elke gebruiker die het rapport bekijkt
- .rdl in dezelfde werkruimte als de gegevensset (andere gebruiker) - Ondersteund
- .rdl in een andere werkruimte als de gegevensset (andere gebruiker): Er moeten leesmachtigingen op gegevenssetniveau zijn toegewezen aan elke gebruiker die het rapport bekijkt
- Beveiliging op rijniveau: Er moeten leesmachtigingen op gegevenssetniveau zijn toegewezen aan elke gebruiker die het rapport bekijkt om dit af te dwingen

## <a name="next-steps"></a>Volgende stappen

- [Een ingesloten gegevensset maken voor een gepagineerd rapport in de Power BI-service](paginated-reports-create-embedded-dataset.md)
- [Wat zijn gepagineerde rapporten in Power BI Premium?](paginated-reports-report-builder-power-bi.md)