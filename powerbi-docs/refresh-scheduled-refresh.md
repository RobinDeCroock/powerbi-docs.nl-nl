---
title: Geplande vernieuwing configureren
description: In dit artikel wordt uitgelegd welke stappen u moet uitvoeren om een gateway te selecteren en een geplande vernieuwing te configureren.
author: mgblythe
manager: kfile
ms.reviewer: kayu''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/06/2019
ms.author: mblythe
LocalizationGroup: Data refresh
ms.openlocfilehash: 9f1289b5fce74c60e5b3802054cef008dd33ada2
ms.sourcegitcommit: 2aa83bd53faad6fb02eb059188ae623e26503b2a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73021553"
---
# <a name="configure-scheduled-refresh"></a>Geplande vernieuwing configureren

>[!NOTE]
>Na twee maanden van inactiviteit wordt de geplande vernieuwing voor uw gegevensset onderbroken. Zie [*Geplande vernieuwing*](#scheduled-refresh) verderop in dit artikel voor meer informatie.
>
>

Als uw gegevensset geplande vernieuwing ondersteunt met **Nu vernieuwen** en **Vernieuwen plannen**, zijn er enkele belangrijke vereisten en instellingen voor een geslaagde vernieuwing. Dit zijn **Gatewayverbinding**, **Gegevensbronreferenties** en **Geplande vernieuwing**. Laten we deze items eens nader bekijken.

Hieronder worden de opties beschreven voor de [on-premises gegevensgateway (persoonlijke modus)](service-gateway-personal-mode.md) en de [on-premises gegevensgateway](service-gateway-onprem.md).

Ga als volgt te werk om het venster **Geplande vernieuwing** weer te geven.

1. Selecteer **Meer opties** (...) naast een gegevensset die wordt vermeld onder **Gegevenssets**.
2. Selecteer **Vernieuwen plannen**.

    ![Planning vernieuwen](media/refresh-scheduled-refresh/dataset-menu.png)

## <a name="gateway-connection"></a>Gatewayverbinding
Welke opties hier worden weergegeven, is afhankelijk van het type gateway (een persoonlijke of bedrijfsgateway) en of de gateway online en beschikbaar is.

Als er geen gateway beschikbaar is, ziet u dat **Gatewayverbinding** is uitgeschakeld. Daarnaast wordt er een bericht weergegeven met informatie hoe u de persoonlijke gateway kunt installeren.

![Gateway niet geconfigureerd](media/refresh-scheduled-refresh/gateway-not-configured.png)

Als u een persoonlijke gateway hebt geconfigureerd, kan de gateway worden geselecteerd als deze online is. Als er geen gateway beschikbaar is, wordt aangegeven dat deze offline is.

![Gatewayverbinding](media/refresh-scheduled-refresh/gateway-connection.png)

U kunt ook de bedrijfsgateway selecteren als deze beschikbaar is voor. Er is alleen een bedrijfsgateway beschikbaar als uw account wordt vermeld op het tabblad **Gebruikers** van de gegevensbron die is geconfigureerd voor een bepaalde gateway.

## <a name="data-source-credentials"></a>Gegevensbronreferenties
### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
Als u de persoonlijke gateway gebruikt om gegevens te vernieuwen, moet u de referenties opgeven waarmee u verbinding maakt met de back-endgegevensbron. Als u verbinding hebt gemaakt met een inhoudspakket van een onlineservice, worden de referenties die u hebt opgegeven om verbinding te maken, overgedragen voor geplande vernieuwing.

![Gegevensbronreferenties](media/refresh-scheduled-refresh/data-source-credentials-pgw.png)

U hoeft zich alleen de eerste keer dat u een gegevensset vernieuwt aan te melden bij de gegevensbron. Wanneer u de referenties eenmaal hebt ingevoerd, worden deze bewaard in de gegevensset.

> [!NOTE]
> Als het wachtwoord dat u gebruikt om u aan te melden bij een gegevensbron, is verlopen of gewijzigd, moet u voor bepaalde verificatiemethoden het wachtwoord voor de gegevensbron ook wijzigen in **Gegevensbronreferenties**.
>
>

Wanneer er iets niet goed gaat, komt dit doorgaans doordat de gateway offline is omdat deze niet kan worden aangemeld bij Windows, en dus de service niet kan worden gestart, of omdat Power BI niet kan worden aangemeld bij de gegevensbronnen om naar bijgewerkte gegevens te zoeken. Als de vernieuwingsbewerking mislukt, controleert u de instellingen van de gegevensset. Als de gatewayservice offline is, wordt deze fout weergegeven bij **Status**. Als Power BI niet kan worden aangemeld bij de gegevensbronnen, wordt er een fout weergegeven in Referenties voor gegevensbron.

### <a name="on-premises-data-gateway"></a>On-premises gegevensgateway
Als u de on-premises gegevensgateway gebruikt om gegevens te vernieuwen, hoeft u geen referenties op te geven, aangezien de referenties voor de gegevensbron worden gedefinieerd de gatewaybeheerder.

![Opdracht Vernieuwen plannen](media/refresh-scheduled-refresh/data-source-credentials-egw.png)

> [!NOTE]
> Als u verbinding met een on-premises SharePoint maakt om gegevens te vernieuwen, ondersteunt Power BI alleen de volgende verificatiemechanismen: *Anoniem*, *Basis* en *Windows (NTLM/Kerberos)* . Power BI biedt geen ondersteuning voor *ADFS* of een *formulieren gebaseerde verificatie* om gegevens van on-premises SharePoint-gegevensbronnen te vernieuwen.
>
>

## <a name="scheduled-refresh"></a>Geplande vernieuwing
In de sectie **Geplande vernieuwing** definieert u de frequentie en de tijdvakken voor het vernieuwen van de gegevensset. Bij sommige gegevensbronnen is het niet nodig dat er een gateway voor vernieuwen kan worden geconfigureerd; voor andere gegevensbronnen is wel een gateway vereist.

Stel de schuifregelaar **Uw gegevens actueel houden** in op **Aan** om de instellingen te configureren.

> [!NOTE]
> Met de Power BI-service worden uw gegevens binnen **15 minuten** van de geplande vernieuwingstijd vernieuwd.
>
>

![Dialoogvenster Geplande vernieuwing](media/refresh-scheduled-refresh/scheduled-refresh.png)

> [!NOTE]
> Na twee maanden van inactiviteit wordt de geplande vernieuwing voor uw gegevensset onderbroken. Een gegevensset wordt gezien als inactief als de dasboards en rapporten die op basis van de gegevensset zijn samengesteld, niet door gebruikers zijn bezocht. Op dat moment ontvangt de eigenaar van de gegevensset een e-mail met het bericht dat de geplande vernieuwing is onderbroken en het vernieuwingsschema voor de gegevensset wordt weergegeven als **uitgeschakeld**. Als u de geplande vernieuwing wilt hervatten, hoeft u een van de dashboard of rapporten die op basis van de gegevensset zijn samengesteld, alleen maar te bezoeken.
>
>

## <a name="whats-supported"></a>Wat wordt ondersteund?
Bepaalde gegevenssets worden ondersteund door verschillende gateways met betrekking tot geplande vernieuwingen. Ter referentie volgt hier wat beschikbaar.

### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
**Power BI Desktop**

* Alle onlinegegevensbronnen die worden weergegeven in **Gegevens ophalen** en Query-editor in Power BI Desktop.
* Alle on-premises gegevensbronnen die worden weergegeven in **Gegevens ophalen** en Query-editor in Power BI Desktop, met uitzondering van Hadoop-bestanden (HDFS) en Microsoft Exchange.

**Excel**

> [!NOTE]
> In Excel 2016 en hoger wordt Power Query in de sectie **Gegevens** van het lint onder **Gegevens ophalen en transformeren** weergegeven.
>
>

* Alle onlinegegevensbronnen die worden weergegeven in Power Query.
* Alle on-premises gegevensbronnen die worden weergegeven in Power Query, met uitzondering van Hadoop-bestanden (HDFS) en Microsoft Exchange.
* Alle onlinegegevensbronnen die worden weergegeven in Power Pivot.
* Alle on-premises gegevensbronnen die worden weergegeven in Power Pivot, met uitzondering van Hadoop-bestanden (HDFS) en Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](./includes/refresh-datasources.md)]

## <a name="troubleshooting"></a>Probleemoplossing
Soms gaat het vernieuwen van gegevens niet zoals u verwacht. Meestal komt dat door een probleem met een gateway. Zie de artikelen over het oplossen van problemen met de gateway voor informatie over hulpprogramma's en bekende problemen.

- [Problemen met de on-premises gegevensgateway oplossen](service-gateway-onprem-tshoot.md)
- [Problemen met Power BI Gateway - Personal oplossen](service-admin-troubleshooting-power-bi-personal-gateway.md)

## <a name="next-steps"></a>Volgende stappen
- [Gegevens vernieuwen in Power BI](refresh-data.md)  
- [Power BI Gateway - Personal](service-gateway-personal-mode.md)  
- [On-premises data gateway (personal mode)](service-gateway-onprem.md) (On-premises gegevensgateway (persoonlijke modus))  
- [Problemen met de on-premises gegevensgateway oplossen](service-gateway-onprem-tshoot.md)  
- [Problemen met Power BI Gateway - Personal oplossen](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

