---
title: Een gegevensset vernieuwen in OneDrive of SharePoint Online
description: Een gegevensset vernieuwen die is gemaakt van een Power BI Desktop-bestand in OneDrive of in SharePoint Online
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 112/06/2018
ms.author: mblythe
LocalizationGroup: Data refresh
ms.openlocfilehash: 4120240b0f4de530bc62587f91bfe1fd4ff7d3df
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "60973518"
---
# <a name="refresh-a-dataset-stored-on-onedrive-or-sharepoint-online"></a>Een gegevensset vernieuwen die is opgeslagen in OneDrive of SharePoint Online
Door bestanden van OneDrive of SharePoint Online te importeren in de Power BI-service, zorgt u ervoor dat uw werk in **Power BI Desktop** gesynchroniseerd blijft met de Power BI-service.

## <a name="advantages-of-storing-a-power-bi-desktop-file-on-onedrive-or-sharepoint-online"></a>Voordelen van het opslaan van een Power BI Desktop-bestand in OneDrive of SharePoint Online
Wanneer u een **Power BI Desktop**-bestand opslaat in OneDrive of SharePoint Online, worden alle gegevens die u in het model van uw bestand hebt geladen, geïmporteerd in de gegevensset. Ook worden alle rapporten die u in het bestand hebt gemaakt, geladen in **Rapporten** in de Power BI-service. Wanneer u wijzigingen in uw bestand in OneDrive or SharePoint Online aanbrengt (zoals het toevoegen van nieuwe metingen, wijzigen van kolomnamen of bewerken van visualisaties) en u het bestand vervolgens opslaat, worden die wijzigingen gewoonlijk ook binnen een uur doorgevoerd in de Power BI-service.

U kunt de gegevens eenmalig handmatig vernieuwen in Power BI Desktop door Vernieuwen te selecteren op het tabblad Start in het lint. Wanneer u hier Vernieuwen selecteert, worden de gegevens in het model van het *bestand* vernieuwd met de bijgewerkte gegevens van de oorspronkelijke gegevensbron. Deze methode van vernieuwen, geheel vanuit de toepassing Power BI Desktop zelf, is iets anders dan het handmatig of gepland vernieuwen in Power BI. Het is belangrijk dat u dit verschil begrijpt.

![](media/refresh-desktop-file-onedrive/pbix-refresh.png)

Wanneer u uw Power BI Desktop-bestand importeert vanuit OneDrive of SharePoint Online, worden de gegevens, samen met andere informatie over het model, geladen in een gegevensset in Power BI. In de Power BI-service (niet in Power BI Desktop) wilt u de gegevens in de gegevensset vernieuwen, omdat uw rapporten in de Power BI-service daarop gebaseerd zijn. Omdat de gegevensbronnen extern zijn, kunt u de gegevensset handmatig vernieuwen met **Nu vernieuwen** of een vernieuwingsschema instellen met **Vernieuwen plannen**.

Wanneer u de gegevensset vernieuwt, wordt in Power BI geen verbinding gemaakt met het bestand in OneDrive of SharePoint Online om de bijgewerkte gegevens op te halen. De informatie in de gegevensset wordt gebruikt om rechtstreeks verbinding te maken met de gegevensbronnen, de bijgewerkte gegevens op te halen en deze vervolgens in de gegevensset te laden. Deze vernieuwde gegevens in de gegevensset worden niet gesynchroniseerd naar het bestand in OneDrive of SharePoint Online.

## <a name="whats-supported"></a>Wat wordt ondersteund?
In Power BI worden Nu vernieuwen en Vernieuwen plannen ondersteund voor gegevenssets die worden gemaakt vanuit Power BI Desktop-bestanden die worden geïmporteerd van een lokaal station, waarbij Gegevens ophalen/Query-editor wordt gebruikt om verbinding te maken met en gegevens te laden uit een van de volgende gegevensbronnen:

### <a name="power-bi-gateway---personal"></a>Power BI Gateway - persoonlijk
* Alle onlinegegevensbronnen die worden weergegeven in Gegevens ophalen en Query-editor in Power BI Desktop.
* Alle on-premises gegevensbronnen die worden weergegeven in Gegevens ophalen en Query-editor in Power BI Desktop, met uitzondering van Hadoop-bestanden (HDFS) en Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](./includes/refresh-datasources.md)]

> [!NOTE]
> Power BI kan alleen verbinding maken met on-premises gegevensbronnen en de gegevensset vernieuwen als een gateway is geïnstalleerd en actief is.
> 
> 

## <a name="onedrive-or-onedrive-for-business-whats-the-difference"></a>OneDrive of OneDrive voor Bedrijven. Wat is het verschil?
Als u zowel een persoonlijk OneDrive-account als een OneDrive voor Bedrijven-account hebt, kunt u het beste alle bestanden die u wilt importeren in Power BI bewaren in OneDrive voor Bedrijven. Waarom? Omdat u waarschijnlijk twee verschillende accounts gebruikt om u aan te melden.

Verbinding maken met OneDrive voor Bedrijven verloopt vaak zonder problemen in Power BI omdat het account waarmee u zich aanmeldt bij Power BI meestal hetzelfde account is als het account waarmee u zich aanmeldt bij OneDrive voor Bedrijven. Bij het persoonlijke OneDrive-account meldt u zich echter waarschijnlijk met een ander [Microsoft-account](https://account.microsoft.com) aan.

Zorg, wanneer u zich aanmeldt met uw Microsoft-account, dat u Aangemeld blijven selecteert. In dat geval kunnen alle wijzigingen die u aanbrengt in het bestand in Power BI Desktop worden gesynchroniseerd met gegevenssets in Power BI  
    ![](media/refresh-desktop-file-onedrive/refresh_signin_keepmesignedin.png)

Als u in uw bestand in OneDrive wijzigingen aanbrengt die niet kunnen worden gesynchroniseerd met de gegevensset of rapporten in Power BI, bijvoorbeeld omdat de referenties voor uw Microsoft-account zijn gewijzigd, moet u opnieuw verbinding maken en het bestand importeren vanuit uw persoonlijke OneDrive.

## <a name="how-do-i-schedule-refresh"></a>Hoe kan ik het vernieuwen plannen?
Wanneer u een vernieuwingsschema instelt, maakt Power BI rechtstreeks verbinding met de gegevensbronnen met behulp van de verbindingsgegevens en referenties in de gegevensset om eventuele bijgewerkte gegevens op te halen en in de gegevensset te laden. Alle visualisaties in rapporten en dashboards die zijn gebaseerd op die gegevensset in de Power BI-service, worden ook bijgewerkt.

Zie [Het plannen van de vernieuwing configureren](refresh-scheduled-refresh.md) voor meer informatie over het instellen van de planning voor een vernieuwing.

## <a name="when-things-go-wrong"></a>Wanneer het fout gaat
Als er iets fout gaat, komt dit meestal doordat Power BI niet kan worden aangemeld bij gegevensbronnen of doordat de gegevensset verbinding maakt met een on-premises gegevensbron terwijl de gateway offline is. Controleer eerst of Power BI kan worden aangemeld bij gegevensbronnen. Als het wachtwoord voor aanmelding bij een gegevensbron is veranderd, of als Power BI wordt afgemeld bij een gegevensbron, probeert u eerst om opnieuw aan te melden bij de gegevensbronnen met de gegevensbronreferenties.

Als u wijzigingen aanbrengt in het Power BI Desktop-bestand in OneDrive en het bestand opslaat maar die wijzigingen na een uur of zo nog niet zijn gesynchroniseerd in Power BI, kan in Power BI mogelijk geen verbinding worden gemaakt met OneDrive. Probeer nogmaals verbinding te maken met het bestand in OneDrive. Als u zich moet aanmelden, schakelt u Aangemeld blijven in. Omdat in Power BI geen verbinding met OneDrive tot stand kon worden gebracht om het bestand te synchroniseren, moet u het bestand opnieuw importeren.

Laat de optie **Mij e-mail met melding voor mislukte vernieuwing sturen** ingeschakeld. U wilt het immers direct weten als een geplande vernieuwing mislukt.

## <a name="troubleshooting"></a>Problemen oplossen
Soms gaat het vernieuwen van gegevens niet zoals u verwacht. Meestal komt dat door een probleem met een gateway. Zie de artikelen over het oplossen van problemen met de gateway voor informatie over hulpprogramma's en bekende problemen.

[Problemen met de on-premises gegevensgateway oplossen](service-gateway-onprem-tshoot.md)

[Problemen met Power BI Gateway - Personal oplossen](service-admin-troubleshooting-power-bi-personal-gateway.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

