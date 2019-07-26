---
title: Uw gegevensbron beheren - SQL
description: De on-premises gegevensgateway en de gegevensbronnen hiervoor beheren.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 7d9e670d2567181a0dc99c23997ac3bc2d35f3c9
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271605"
---
# <a name="manage-your-data-source---sql-server"></a>Uw gegevensbron beheren - SQL Server

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Nadat u de [on-premises gegevensgateway hebt geïnstalleerd](/data-integration/gateway/service-gateway-install), kunt u [gegevensbronnen toevoegen](service-gateway-data-sources.md#add-a-data-source) die met de gateway kunnen worden gebruikt. In dit artikel wordt beschreven hoe u werkt met gateways en SQL Server-gegevensbronnen die worden gebruikt voor gepland vernieuwen of voor DirectQuery.

## <a name="add-a-data-source"></a>Een gegevensbron toevoegen

Zie [Een gegevensbron toevoegen](service-gateway-data-sources.md#add-a-data-source) voor meer informatie over het toevoegen van een gegevensbron.

![De SQL Server-gegevensbron selecteren](media/service-gateway-enterprise-manage-sql/datasourcesettings2.png)

> [!NOTE]
> Wanneer u DirectQuery gebruikt, biedt de gateway alleen ondersteuning voor **SQL Server 2012 SP1** en latere versies.

Vul vervolgens de gegevens voor de gegevensbron in, waaronder de **Server** en de **Database**.  

U moet ook een **Verificatiemethode** kiezen. Dit kan **Windows** of **Standaard** zijn. Kies **Basic** als u SQL-verificatie in plaats van Windows-verificatie wilt gebruiken. Voer vervolgens de referenties in die u voor deze gegevensbron wilt gebruiken.

> [!NOTE]
> Alle query's voor de gegevensbron worden uitgevoerd met deze referenties, tenzij eenmalige aanmelding (SSO) met Kerberos is geconfigureerd en ingeschakeld voor de gegevensbron. Bij eenmalige aanmelding gebruiken importgegevenssets de opgeslagen referenties, maar DirectQuery-gegevenssets gebruiken de huidige Power BI-gebruiker om de query's met behulp van eenmalige aanmelding uit te voeren. Zie [Versleutelde referenties opslaan in de cloud](service-gateway-data-sources.md#storing-encrypted-credentials-in-the-cloud) voor meer informatie over hoe referenties worden opgeslagen. U kunt hiervoor ook het artikel lezen waarin wordt beschreven hoe u [Kerberos gebruikt voor eenmalige aanmelding (SSO) in Power BI bij on-premises gegevensbronnen](service-gateway-sso-kerberos.md).

![De gegevensbroninstellingen invullen](media/service-gateway-enterprise-manage-sql/datasourcesettings3.png)

Selecteer **Toevoegen** nadat u alles hebt ingevuld. U kunt deze gegevensbron nu gebruiken voor geplande vernieuwing, of DirectQuery, bij een on-premises SQL-server. De tekst *Verbinding gemaakt* wordt weergegeven als deze bewerking is geslaagd.

![De verbindingsstatus weergeven](media/service-gateway-enterprise-manage-sql/datasourcesettings4.png)

### <a name="advanced-settings"></a>Geavanceerde instellingen

U kunt optioneel het privacyniveau voor uw gegevensbron configureren. Hiermee bepaalt u hoe gegevens kunnen worden gecombineerd. Dit wordt alleen gebruikt voor geplande vernieuwing. Het geldt niet voor DirectQuery. Zie [privacyniveaus (Power query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)voor meer informatie over privacyniveaus voor uw gegevensbron.

![Het privacyniveau instellen](media/service-gateway-enterprise-manage-sql/datasourcesettings9.png)

## <a name="using-the-data-source"></a>De gegevensbron gebruiken

Nadat u de gegevensbron hebt gemaakt, kan deze worden gebruikt met DirectQuery-verbindingen of via geplande vernieuwing.

> [!NOTE]
> De servernaam en databasenaam die worden gebruikt voor Power BI Desktop en de gegevensbron in de on-premises gegevensgateway moeten overeenkomen.

De koppeling tussen uw gegevensset en de gegevensbron in de gateway is gebaseerd op uw server- en databasenaam. Deze moeten overeenkomen. Als u bijvoorbeeld een IP-adres gebruikt als servernaam in **Power BI Desktop**, moet u dit IP-adres ook gebruiken voor de gegevensbron in de gatewayconfiguratie. Als u in Power BI Desktop *SERVER\EXEMPLAAR* gebruikt, moet u daar ook gebruik van maken in de gegevensbron die u voor de gateway configureert.

Dit geldt voor zowel DirectQuery als geplande vernieuwing.

### <a name="using-the-data-source-with-directquery-connections"></a>De gegevensbron gebruiken met DirectQuery-verbindingen

Zorg ervoor dat de servernaam en databasenaam voor **Power BI Desktop** en de geconfigureerde gegevensbron voor de gateway overeenkomen. Zorg er ook voor dat de gebruiker wordt vermeld op het tabblad **Gebruikers** van de gegevensbron om DirectQuery-gegevenssets te kunnen publiceren. De selectie voor DirectQuery vindt plaats in Power BI Desktop wanneer u voor het eerst gegevens importeert. Zie [DirectQuery in Power BI Desktop gebruiken](desktop-use-directquery.md) voor meer informatie over het gebruik van DirectQuery.

Als het goed is, werken uw rapporten nadat u de gegevens hebt gepubliceerd vanuit Power BI Desktop of via **Gegevens ophalen**. Nadat u de gegevensbron in de gateway hebt gemaakt, kan het enkele minuten duren voordat de verbinding kan worden gebruikt.

### <a name="using-the-data-source-with-scheduled-refresh"></a>De gegevensbron gebruiken met geplande vernieuwing

Als u wordt vermeld op het tabblad **Gebruikers** voor de gegevensbron die is geconfigureerd in de gateway en als de server- en databasenaam overeenkomen, wordt de gateway als optie vermeld om te gebruiken bij geplande vernieuwing.

![De gebruikers weergeven](media/service-gateway-enterprise-manage-sql/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Volgende stappen

* [Verbinding maken met on-premises gegevens in SQL Server](service-gateway-sql-tutorial.md)
* [Problemen met de on-premises gegevensgateway oplossen](/data-integration/gateway/service-gateway-tshoot)
* [Problemen met gateways oplossen - Power BI](service-gateway-onprem-tshoot.md)
* [Use Kerberos for SSO (single sign-on) from Power BI to on-premises data sources](service-gateway-sso-kerberos.md) (Kerberos gebruiken voor eenmalige aanmelding (SSO) van Power BI naar on-premises gegevensbronnen)

Nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

