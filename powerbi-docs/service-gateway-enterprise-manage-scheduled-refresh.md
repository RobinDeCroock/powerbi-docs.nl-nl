---
title: Uw gegevensbron beheren - importeren/geplande vernieuwing
description: De on-premises gegevensgateway en de gegevensbronnen hiervoor beheren. Dit artikel is specifiek bedoeld voor gegevensbronnen die kunnen worden gebruikt met importeren/geplande vernieuwing.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 7512257a3abad33babe2a5b6b56f613c7bb1b50f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881695"
---
# <a name="manage-your-data-source---importscheduled-refresh"></a>Uw gegevensbron beheren - importeren/geplande vernieuwing

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Nadat u de [on-premises gegevensgateway hebt geïnstalleerd](/data-integration/gateway/service-gateway-install), moet u [gegevensbronnen toevoegen](service-gateway-data-sources.md#add-a-data-source) die met de gateway kunnen worden gebruikt. In dit artikel wordt beschreven hoe u werkt met gateways en gegevensbronnen die worden gebruikt voor geplande vernieuwing in plaats van DirectQuery of liveverbindingen.

## <a name="add-a-data-source"></a>Een gegevensbron toevoegen

Zie [Een gegevensbron toevoegen](service-gateway-data-sources.md#add-a-data-source) voor meer informatie over het toevoegen van een gegevensbron. Selecteer een gegevensbrontype.

Alle vermelde gegevensbrontypen kunnen worden gebruikt voor geplande vernieuwing met de on-premises gegevensgateway. Analysis Services, SQL Server en SAP HANA kunnen worden gebruikt voor geplande vernieuwing of DirectQuery/liveverbindingen.

![De gegevensbron selecteren](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings2.png)

Vul vervolgens de informatie over de gegevensbron in, zoals de brongegevens en referenties voor toegang tot de gegevensbron.

> [!NOTE]
> Alle query's voor de gegevensbron worden uitgevoerd met deze referenties. Zie [Versleutelde referenties opslaan in de cloud](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud) voor meer informatie over het opslaan van referenties.

![De gegevensbroninstellingen invullen](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings3-oracle.png)

Zie [lijst met beschikbare gegevensbrontypen](service-gateway-data-sources.md#list-of-available-data-source-types) voor een lijst met gegevensbrontypen die kunnen worden gebruikt met geplande vernieuwing.

Nadat u alles hebt ingevuld, selecteert u **Toevoegen**. U kunt deze gegevensbron nu gebruiken voor geplande vernieuwing met uw on-premises gegevens. De tekst *Verbinding gemaakt* wordt weergegeven als deze bewerking is geslaagd.

![De verbindingsstatus weergeven](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings4.png)

### <a name="advanced-settings"></a>Geavanceerde instellingen

U kunt optioneel het privacyniveau voor uw gegevensbron configureren. Met deze instelling bepaalt u hoe gegevens kunnen worden gecombineerd. Deze wordt alleen gebruikt voor geplande vernieuwing. Zie [privacyniveaus (Power query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)voor meer informatie over privacyniveaus voor uw gegevensbron.

![Het privacyniveau instellen](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings9.png)

## <a name="use-the-data-source-for-scheduled-refresh"></a>De gegevensbron gebruiken voor geplande vernieuwing

Nadat u de gegevensbron hebt gemaakt, is deze beschikbaar voor gebruik met zowel DirectQuery-verbindingen als via geplande vernieuwing.

> [!NOTE]
> De servernaam en databasenaam die worden gebruikt voor Power BI Desktop en de gegevensbron in de on-premises gegevensgateway moeten overeenkomen.

De koppeling tussen uw gegevensset en de gegevensbron in de gateway is gebaseerd op uw server- en databasenaam. Deze namen moeten overeenkomen. Als u bijvoorbeeld een IP-adres gebruikt als servernaam in Power BI Desktop, moet u dit IP-adres ook gebruiken voor de gegevensbron in de gatewayconfiguratie. Als u in Power BI Desktop *SERVER\EXEMPLAAR* gebruikt, moet u daarvan ook gebruik maken in de gegevensbron die u voor de gateway configureert.

Als u wordt vermeld op het tabblad **Gebruikers** voor de gegevensbron die is geconfigureerd in de gateway en als de server- en databasenaam overeenkomen, wordt de gateway als optie vermeld om te gebruiken bij geplande vernieuwing.

![De gebruikers weergeven](media/service-gateway-enterprise-manage-scheduled-refresh/powerbi-gateway-enterprise-schedule-refresh.png)

> [!WARNING]
> Als de gegevensset meerdere gegevensbronnen bevat, moet elke gegevensbron aan de gateway worden toegevoegd. Als een of meer gegevensbronnen niet aan de gateway zijn toegevoegd, wordt de gateway niet weergegeven omdat deze niet beschikbaar is voor geplande vernieuwing.

## <a name="limitations"></a>Beperkingen

OAuth wordt niet ondersteund als verificatieschema voor de on-premises gegevensgateway. U kunt geen gegevensbronnen toevoegen waarvoor OAuth vereist is. Als uw gegevensset een gegevensbron bevat waarvoor OAuth vereist is, kunt u de gateway niet gebruiken voor geplande vernieuwing.

## <a name="next-steps"></a>Volgende stappen

* [Problemen met de on-premises gegevensgateway oplossen](/data-integration/gateway/service-gateway-tshoot)
* [Problemen met gateways oplossen - Power BI](service-gateway-onprem-tshoot.md)

Hebt u nog vragen? Misschien dat de [Power BI-community](https://community.powerbi.com/) het antwoord weet.
