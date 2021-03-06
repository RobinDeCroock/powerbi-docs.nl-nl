---
title: Ondersteunde gegevensbronnen voor gepagineerde rapporten in Power BI
description: In dit artikel vindt u informatie over ondersteunde gegevensbronnen voor gepagineerde rapporten in de Power BI-service en hoe u verbinding maakt met Azure SQL Database-gegevensbronnen.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/27/2021
ms.openlocfilehash: c544126132ce18d8093f8c07359418f2052e9c74
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/29/2021
ms.locfileid: "99044397"
---
# <a name="supported-data-sources-for-power-bi-paginated-reports"></a>Ondersteunde gegevensbronnen voor gepagineerde rapporten in Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

In dit artikel vindt u informatie over ondersteunde gegevensbronnen voor gepagineerde rapporten in de Power BI-service en hoe u verbinding maakt met Azure SQL Database-gegevensbronnen. Sommige gegevensbronnen worden inherent ondersteund. U kunt verbinding maken met andere gegevensbronnen via gegevensgateways.

## <a name="natively-supported-data-sources"></a>Inherent ondersteunde gegevensbronnen

Gepagineerde rapporten bieden inherente ondersteuning voor de volgende lijst met gegevensbronnen:

| Gegevensbron | Verificatie | Opmerkingen |
| --- | --- | --- |
| Azure SQL Database <br>Azure SQL Data Warehouse | Basic, eenmalige aanmelding (SSO), OAuth2 | U kunt een Enterprise Gateway met Azure SQL Database gebruiken. U mag in deze scenario's echter voor verificatie geen Eenmalige aanmelding of oAuth2 gebruiken.   |
| Beheerd exemplaar voor Azure SQL | Basic | via een openbaar eindpunt of een privé-eindpunt (privé-eindpunt moet worden gerouteerd via een Enterprise Gateway)  |
| Azure Analysis Services | SSO, OAuth2 | De AAS-firewall moet worden uitgeschakeld of geconfigureerd om alle IP-bereiken in de BlackForest-regio toe te staan. Dit geldt alleen voor de BlackForest-regio.  SSO vanaf een externe tenant wordt niet ondersteund. |
| Power BI-gegevensset | SSO | Premium Power BI-gegevenssets en andere Power BI-gegevenssets. Hiervoor is leesmachtiging vereist. Alleen de modus voor importeren en DirectQuery Power BI-gegevenssets worden ondersteund. |
| Premium-Power BI-gegevensset (XMLA) | SSO | Power BI-gegevenssets worden niet ondersteund als gegevensbron voor ingesloten gepagineerde rapporten in scenario's waarin de app eigenaar van de gegevens is.  Zorg ervoor dat de optie **referenties niet gebruiken** is geselecteerd bij het instellen van de gegevens bron om ervoor te zorgen dat de juiste connectiviteit in Power bi Report Builder.<br />Toegang via het XMLA respecteert het lidmaatschap van de beveiligings groep die is ingesteld op het niveau van de werk ruimte of app.<br />Gebruikers met ten minste een [rol Inzender in een werk ruimte](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) kunnen gepagineerde rapporten met Premium-Power BI gegevens sets weer geven. Andere gebruikers moeten [beschikken over de machtiging bouwen voor de onderliggende gegevens sets](../connect-data/service-datasets-build-permissions.md).    |
| Gegevens invoeren | N.v.t. | Gegevens zijn in het rapport ingesloten. |
| Dataverse | SSO, OAuth2 | Kan geen gateway gebruiken als multi-factor Authentication (MFA) niet wordt ondersteund.

Met uitzondering van Azure SQL Database zijn alle gegevensbronnen gereed voor gebruik nadat u het rapport hebt geüpload naar de Power BI-service. Voor de gegevensbronnen wordt standaard gebruikgemaakt van eenmalige aanmelding (SSO), indien van toepassing. Voor Azure Analysis Services kunt u het verificatietype wijzigen in OAuth2. Wanneer u het verificatietype voor een bepaalde gegevensbron echter wijzigt in OAuth2, kunt u dit niet meer ongedaan maken om opnieuw SSO te gebruiken.  Deze wijziging is bovendien van toepassing op alle rapporten die gebruikmaken van die gegevensbron in alle werkruimten voor een bepaalde tenant.  Beveiliging op rijniveau in gepagineerde rapporten werkt niet, tenzij gebruikers SSO kiezen als verificatietype.

Voor Azure SQL Database-gegevensbronnen moet u meer informatie opgeven, zoals beschreven in de sectie [Azure SQL Database-verificatie.](#azure-sql-database-authentication)

## <a name="other-data-sources"></a>Andere gegevensbronnen

Naast de inherent ondersteunde gegevensbronnen zijn de volgende gegevensbronnen toegankelijk via een [Power BI-bedrijfsgateway](../connect-data/service-gateway-onprem.md):

- SQL Server
- SQL Server Analysis Services
- Oracle
- Teradata

Voor gepagineerde rapporten is Azure Analysis Services momenteel niet toegankelijk via een Power BI-bedrijfsgateway.

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
- OAuth2 (opgeslagen Azure Active Directory-token)

SSO en OAuth2 werken alleen correct als [ondersteuning voor Azure Active Directory-verificatie is ingeschakeld](/azure/sql-database/sql-database-aad-authentication-configure) voor de Azure SQL Database-server waarmee de gegevensbron verbinding maakt. Voor de verificatiemethode OAuth2 wordt in Azure Active Directory een token gegenereerd. Dit token wordt opgeslagen voor toekomstige gegevensbrontoegang. Als u in plaats daarvan de [SSO-verificatiemethode](../connect-data/service-azure-sql-database-with-direct-connect.md#single-sign-on) wilt gebruiken, selecteert u de optie SSO direct eronder, **Eindgebruikers gebruiken hun eigen OAuth2-referenties bij de toegang tot deze gegevensbron via DirectQuery**.
  
## <a name="next-steps"></a>Volgende stappen

[Een gepagineerd rapport weergeven in de Power BI-service](../consumer/paginated-reports-view-power-bi-service.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
