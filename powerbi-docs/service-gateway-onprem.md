---
title: On-premises gegevensgateway
description: Dit is een overzicht van de on-premises gegevensgateway voor Power BI. U kunt deze gateway gebruiken om te werken met DirectQuery-gegevensbronnen. U kunt deze gateway ook gebruiken om cloud-gegevenssets te vernieuwen met on-premises gegevens.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 06/05/2018
ms.openlocfilehash: 7e2e0e7a980c72f203f93baf552685dce6f43bbd
ms.sourcegitcommit: 8dee40f07d284ec84a8afa0100359f146e1dd88b
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/27/2019
ms.locfileid: "67418810"
---
# <a name="on-premises-data-gateway"></a>On-premises gegevensgateway

De on-premises gegevensgateway fungeert als een brug waarmee u over snelle en veilige gegevensoverdracht beschikt tussen on-premises gegevens (gegevens die zich niet in de cloud bevinden) en de services van Power BI, Microsoft Flow, Logic Apps en PowerApps.

U kunt één gateway met verschillende services tegelijk gebruiken. Als u Power BI en PowerApps gebruikt, kan één gateway worden gebruikt voor beiden. Dit is afhankelijk van het account waarmee u zich aanmeldt.

> [!NOTE]
> Via de on-premises gegevensgateway worden gegevenscompressie en transportversleuteling in alle modi geïmplementeerd.

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-requirements-include.md)]

### <a name="limitations-of-analysis-services-live-connections"></a>Beperkingen van liveverbindingen van Analysis Services

U kunt een liveverbinding gebruiken voor tabelvormige of multidimensionale exemplaren.

| **Server-versie** | **Vereiste SKU** |
| --- | --- |
| 2012 SP1 CU4 of hoger |Business Intelligence en Enterprise-SKU |
| 2014 |Business Intelligence en Enterprise-SKU |
| 2016 |Standaard-SKU of hoger |

* Opmaak op celniveau en vertaalfuncties worden niet ondersteund.
* Acties en benoemde sets zijn niet beschikbaar in Power BI, maar u kunt wel verbinding maken met multidimensionale kubussen die ook acties of benoemde sets bevatten. Ook kunt u visuele elementen en rapporten maken.

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="download-and-install-the-on-premises-data-gateway"></a>De on-premises gegevensgateway downloaden en installeren

Selecteer **Gegevensgateway** in het menu Downloads om de gateway te downloaden. Download de [On-premises gegevensgateway](http://go.microsoft.com/fwlink/?LinkID=820925).

U kunt de on-premises gegevensgateway bijwerken door de gateway opnieuw te installeren. Dit wordt in dit gedeelte beschreven. Zolang u een nieuwere versie van de gateway installeert, blijven uw bestaande instellingen bewaard. Als u dezelfde versie installeert, wordt deze versie als nieuwe versie behandeld en worden uw instellingen niet bewaard.

![](media/service-gateway-onprem/powerbi-download-data-gateway.png)

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-install-include](./includes/gateway-onprem-install-include.md)]

## <a name="install-the-gateway-in-personal-mode"></a>De gateway in persoonlijke modus installeren

> [!NOTE]
> De persoonlijke versie van de gateway werkt alleen met Power BI.

Nadat de persoonlijke gateway is geïnstalleerd, moet u de **Power BI Gateway - Persoonlijke configuratiewizard** starten.

![](media/service-gateway-onprem/personal-gateway-launch-configuration.png)

Vervolgens moet u zich aanmelden bij Power BI om de gateway te registreren bij de cloudservice.

![](media/service-gateway-onprem/personal-gateway-signin.png)

U moet ook de Windows-gebruikersnaam en het wachtwoord invoeren dat hoort bij de Windows-service. U kunt een ander Windows-account van uzelf opgeven. De gateway-service wordt uitgevoerd met dit account.

![](media/service-gateway-onprem/personal-gateway-windows-service.png)

Nadat de installatie is voltooid, gaat u naar de gegevenssets in Power BI en controleert u of de referenties zijn ingevoerd voor uw on-premises gegevensbronnen.

<a name="credentials"></a>

## <a name="storing-encrypted-credentials-in-the-cloud"></a>Versleutelde referenties opslaan in de cloud

Wanneer u een gegevensbron aan de gateway toevoegt, moet u referenties opgeven voor de gegevensbron. Alle query's over de gegevensbron worden uitgevoerd met deze referenties. Voordat de referenties worden opgeslagen in de cloud, worden ze veilig versleuteld met behulp van symmetrische codering zodat ze in de cloud niet kunnen niet worden ontsleuteld. De referenties worden verzonden naar de machine waarop de gateway wordt uitgevoerd, waar ze worden ontsleuteld als de gegevensbronnen worden geopend.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

<!-- How the gateway works -->
[!INCLUDE [gateway-onprem-how-it-works-include](./includes/gateway-onprem-how-it-works-include.md)]

## <a name="limitations-and-considerations"></a>Beperkingen en overwegingen

* [Azure Information Protection](https://docs.microsoft.com/microsoft-365/enterprise/protect-files-with-aip
) wordt momenteel niet ondersteund.
* [Access Online](https://products.office.com/access) wordt momenteel niet ondersteund.
* R-scripts worden alleen ondersteund als de gateway wordt uitgevoerd in de persoonlijke modus.

## <a name="tenant-level-administration"></a>Beheer op tenantniveau

Als tenantbeheerder kunt u alle on-premises gegevensgateways zien die binnen uw tenant zijn geïnstalleerd en kunt u deze beheren. Deze mogelijkheid is momenteel beschikbaar als openbare preview-versie. Zie de [documentatie over het beheercentrum van Power-platform](/power-platform/admin/onpremises-data-gateway-management) voor meer informatie.

Als u een tenantbeheerder bent, kunt u ook de gebruikers in uw organisatie vragen u toe te voegen als beheerder aan elke gateway die ze installeren. Op deze manier kunt u alle gateways in uw organisatie beheren via de pagina Gateway-instellingen of via [PowerShell-opdrachten](service-gateway-high-availability-clusters.md#powershell-support-for-gateway-clusters). 

## <a name="enabling-outbound-azure-connections"></a>Uitgaande Azure-verbindingen inschakelen

De on-premises gegevensgateway is afhankelijk van Azure Service Bus voor cloudconnectiviteit en brengt dienovereenkomstig uitgaande verbindingen naar de bijbehorende Azure-regio tot stand. Standaard is dit de locatie van uw Power BI-tenant. Zie [Waar bevindt mijn Power BI-tenant zich?](https://powerbi.microsoft.com/documentation/powerbi-admin-where-is-my-tenant-located/)
Als uitgaande verbindingen door een firewall worden geblokkeerd, moet u de firewall configureren zodat deze uitgaande verbindingen toestaat van de on-premises gegevensgateway naar de bijbehorende Azure-regio. Zie [Microsoft Azure Datacenter IP-bereiken](https://www.microsoft.com/download/details.aspx?id=41653) voor meer informatie over het IP-adressenbereik van elk Azure-datacenter.
> [!NOTE]
> Het IP-adressenbereik kan na verloop van tijd worden gewijzigd; download dus regelmatig de nieuwste informatie. 

## <a name="troubleshooting"></a>Probleemoplossing

Zie [Problemen met de on-premises gegevensgateway oplossen](service-gateway-onprem-tshoot.md) als u problemen hebt bij het installeren en configureren van een gateway. Als u denkt dat er een probleem is met uw firewall, raadpleegt u de sectie [Firewall of proxyserver](service-gateway-onprem-tshoot.md#firewall-or-proxy) in het artikel over probleemoplossing.

Zie [Proxy-instellingen voor de Power BI-gateways configureren](service-gateway-proxy.md) als u denkt dat er proxy-problemen met de gateway zijn.

## <a name="next-steps"></a>Volgende stappen

[Manage your data source - Analysis Services](service-gateway-enterprise-manage-ssas.md) (Uw gegevensbron beheren - Analysis Services)  
[Manage your data source - SAP HANA](service-gateway-enterprise-manage-sap.md) (Uw gegevensbron beheren - SAP HANA)  
[Manage your data source - SQL Server](service-gateway-enterprise-manage-sql.md) (Gegevensbron beheren - SQL Server)  
[Manage your data source - Oracle](service-gateway-onprem-manage-oracle.md) (Gegevensbron beheren - Oracle)  
[Manage your data source - Import/Scheduled refresh](service-gateway-enterprise-manage-scheduled-refresh.md) (Gegevensbron beheren - importeren/geplande vernieuwing)  
[On-premises data gateway in-depth](service-gateway-onprem-indepth.md) (On-premises gegevensgateway - uitgebreid)  
[On-premises gegevensgateway (persoonlijke modus): de nieuwe versie van de persoonlijke gateway](service-gateway-personal-mode.md)  
[Proxyinstellingen configureren voor de on-premises gegevensgateway](service-gateway-proxy.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
