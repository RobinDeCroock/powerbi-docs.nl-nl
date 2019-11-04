---
title: Verbinding maken met Office365Mon met Power BI
description: Office365Mon voor Power BI
author: teddybercovitz
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 8/29/2019
ms.author: tebercov
LocalizationGroup: Connect to services
ms.openlocfilehash: 5d31eccd52164bb4d1ff37532d89dc7e147693d3
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060834"
---
# <a name="connect-to-office365mon-with-power-bi"></a>Verbinding maken met Office365Mon met Power BI
U kunt eenvoudig de onderbrekingen van Office 365 en prestatiegegevens analyseren met Power BI en de Office365Mon-sjabloon-app. Uw gegevens, inclusief storingen en statuscontroles, worden opgehaald met Power BI en er worden een kant-en-klaar dashboard en rapporten gemaakt op basis van die gegevens.

Maak verbinding met de [Office365Mon-sjabloon-app](https://app.powerbi.com/groups/me/getdata/services/office365mon) voor Power BI.

>[!NOTE]
>Een Office365Mon-beheerdersaccount is vereist om de Power BI-sjabloon-app te verbinden en laden.

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer **Gegevens ophalen** onder in het linkernavigatievenster.
   
   ![](media/service-connect-to-office365mon/pbi_getdata.png)
2. Selecteer in het vak **Services** de optie **Ophalen**.
   
   ![](media/service-connect-to-office365mon/pbi_getservices.png) 
3. Selecteer **Office365Mon** \> **Ophalen**.
   
   ![](media/service-connect-to-office365mon/o365mon.png)
4. Selecteer voor de verificatiemethode **oAuth2** \> **Aanmelden**.
   
   Geef desgevraagd uw Office365Mon-beheerdersreferenties op en voer het verificatieproces uit.
   
   ![](media/service-connect-to-office365mon/creds.png)
   
   ![](media/service-connect-to-office365mon/creds2.png)
5. Nadat de gegevens in Power BI zijn geïmporteerd, ziet u een nieuw dashboard, een nieuw rapport en een nieuwe gegevensset in het navigatiedeelvenster aan de linkerzijde. Nieuwe items worden gemarkeerd met een geel sterretje \*; selecteer de vermelding Office365Mon.
   
   ![](media/service-connect-to-office365mon/dashboard4.png)

**Wat nu?**

* [Stel vragen in het vak Q&A](consumer/end-user-q-and-a.md) boven in het dashboard.
* [Wijzig de tegels](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](consumer/end-user-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

## <a name="troubleshooting"></a>Problemen oplossen
Als u een fout **Aanmelden is mislukt** krijgt nadat u uw Office365Mon-abonnementsgegevens hebt gebruikt om in te loggen, dan heeft het account dat u gebruikt geen rechten om de Office365Mon-gegevens van uw account op te halen. Controleer of het een beheerdersaccount is en probeer het opnieuw.

## <a name="next-steps"></a>Volgende stappen
[Wat is Power BI?](fundamentals/power-bi-overview.md)

[Gegevens ophalen voor Power BI](service-get-data.md)

