---
title: Ondersteunde gegevensbronnen voor gepagineerde rapporten in Power BI
description: In dit artikel vindt u informatie over ondersteunde gegevensbronnen voor gepagineerde rapporten in de Power BI-service en hoe u verbinding maakt met Azure SQL Database-gegevensbronnen.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 07/19/2019
ms.openlocfilehash: 91ddcfca56ac7c08736c35c7232df04082e4e921
ms.sourcegitcommit: a58461fe7dfa65c751490b52de5fc73f8e69a17f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68352971"
---
# <a name="supported-data-sources-for-power-bi-paginated-reports"></a>Ondersteunde gegevensbronnen voor gepagineerde rapporten in Power BI

In dit artikel vindt u informatie over ondersteunde gegevensbronnen voor gepagineerde rapporten in de Power BI-service en hoe u verbinding maakt met Azure SQL Database-gegevensbronnen. Sommige gegevensbronnen worden inherent ondersteund. U kunt verbinding maken met andere gegevensbronnen via gegevensgateways.

## <a name="natively-supported-data-sources"></a>Inherent ondersteunde gegevensbronnen

Gepagineerde rapporten bieden inherente ondersteuning voor de volgende lijst met gegevensbronnen:

| Gegevensbron | Verificatie | Opmerkingen |
| --- | --- | --- |
| Azure SQL Database <br>Azure SQL Data Warehouse | Basic, eenmalige aanmelding (SSO), OAuth2 |   |
| Azure Analysis Services | SSO, OAuth2 |   |
| Power BI-gegevensset | SSO | Premium- en niet-Premium-Power BI-gegevenssets |
| Premium-Power BI-gegevensset (XMLA) | SSO |   |
| Gegevens invoeren | N.v.t. | Gegevens zijn in het rapport ingesloten. |

Met uitzondering van Azure SQL Database zijn alle gegevensbronnen gereed voor gebruik nadat u het rapport hebt geüpload naar de Power BI-service. Voor de gegevensbronnen wordt standaard gebruikgemaakt van eenmalige aanmelding (SSO), indien van toepassing. Voor Azure Analysis Services kunt u het verificatietype wijzigen in OAuth2.

Voor Azure SQL Database-gegevensbronnen moet u meer informatie opgeven, zoals beschreven in de sectie [Azure SQL Database-verificatie.](#azure-sql-database-authentication)

## <a name="other-data-sources"></a>Andere gegevensbronnen

Naast de inherent ondersteunde gegevensbronnen zijn de volgende gegevensbronnen toegankelijk via een [Power BI-gegevensgateway](service-gateway-onprem.md):

- SQL Server
- SQL Server Analysis Services
- Oracle
- Teradata

Voor gepagineerde rapporten zijn Azure SQL Database en Azure Analysis Services momenteel niet toegankelijk via een Power BI-gegevensgateway.

## <a name="azure-sql-database-authentication"></a>Azure SQL Database-verificatie

For Azure SQL Database-gegevensbronnen moet u een verificatietype instellen voordat u het rapport uitvoert. Dit geldt alleen als u een gegevensbron voor het eerst in een werkruimte gebruikt. Die eerste keer ziet u het volgende bericht:

![Publiceren naar Power BI](media/paginated-reports-data-sources/power-bi-paginated-publishing.png)

Als u geen referenties opgeeft, treedt er een fout op wanneer u het rapport uitvoert. Selecteer **Doorgaan** om naar de pagina **Gegevensbronreferenties** te gaan voor het rapport dat u zojuist hebt geüpload:

![Instellingen voor Azure SQL Database](media/paginated-reports-data-sources/power-bi-paginated-settings-azure-sql.png)

Selecteer de koppeling **Referenties bewerken** voor een bepaalde gegevensbron om het dialoogvenster **Configureren** weer te geven:

![Azure SQL Database configureren](media/paginated-reports-data-sources/power-bi-paginated-configure-azure-sql.png)

Voor Azure SQL Database-gegevensbronnen zijn dit de ondersteunde verificatietypen:

- Basic (gebruikersnaam en wachtwoord)
- SSO (eenmalige aanmelding)
- OAuth2 (opgeslagen AAD-token)

SSO en OAuth2 werken alleen correct als [ondersteuning voor AAD-verificatie is ingeschakeld](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure) voor de Azure SQL Database-server waarmee de gegevensbron verbinding maakt. Voor de verificatiemethode OAuth2 wordt in AAD een token gegenereerd. Dit token wordt opgeslagen voor toekomstige gegevensbrontoegang. Als u in plaats daarvan de [SSO-verificatiemethode](https://docs.microsoft.com/power-bi/service-azure-sql-database-with-direct-connect#single-sign-on) wilt gebruiken, selecteert u de optie SSO direct eronder, **Eindgebruikers gebruiken hun eigen OAuth2-referenties bij de toegang tot deze gegevensbron via DirectQuery**.
  
## <a name="next-steps"></a>Volgende stappen

[Een gepagineerd rapport weergeven in de Power BI-service](paginated-reports-view-power-bi-service.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
