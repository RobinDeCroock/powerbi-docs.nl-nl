---
title: Verbinding maken met Office365Mon met Power BI
description: Office365Mon voor Power BI
author: paulinbar
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 11/26/2019
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 422782c3036f94c1ea764f46135200116092d70c
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2020
ms.locfileid: "86216222"
---
# <a name="connect-to-office365mon-with-power-bi"></a>Verbinding maken met Office365Mon met Power BI
U kunt eenvoudig de onderbrekingen van Office 365 en prestatiegegevens analyseren met Power BI en de Office365Mon-sjabloon-app. Uw gegevens, inclusief storingen en statuscontroles, worden opgehaald met Power BI en er worden een kant-en-klaar dashboard en rapporten gemaakt op basis van die gegevens.

Maak verbinding met de [Office365Mon-sjabloon-app](https://msit.powerbi.com/groups/me/getapps/services/office365mon.office365mon_powerbi_v3) voor Power BI.

>[!NOTE]
>Een Office365Mon-beheerdersaccount is vereist om de Power BI-sjabloon-app te verbinden en laden.

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer **Gegevens ophalen** onderaan het navigatievenster.
   
   ![Schermopname van de knop Gegevens ophalen in het navigatiedeelvenster.](media/service-connect-to-office365mon/pbi_getdata.png)
2. Selecteer **Ophalen** in het vak **Services**.
   
   ![Schermopname van het dialoogvenster Services met de knop Ophalen.](media/service-connect-to-office365mon/pbi_getservices.png) 
3. Selecteer **Office365Mon** \> **Ophalen**.
   
   ![Schermopname van het dialoogvenster Office365Mon met de koppeling Ophalen.](media/service-connect-to-office365mon/o365mon.png)
4. Selecteer voor de verificatiemethode de optie **oAuth2** \>  **Aanmelden**.
   
   Geef desgevraagd uw Office365Mon-beheerdersreferenties op en voer het verificatieproces uit.
   
   ![Schermopname van het dialoogvenster Verbinding maken met Office365Mon, waarin de optie oAuth2 in het veld Verificatiemethode wordt weergegeven.](media/service-connect-to-office365mon/creds.png)
   
   ![Schermopname van de Office365Mon-aanmelding, waarin om referenties wordt gevraagd.](media/service-connect-to-office365mon/creds2.png)
5. Nadat de gegevens in Power BI zijn geïmporteerd, ziet u een nieuw dashboard, een nieuw rapport en een nieuwe gegevensset in het navigatievenster. Nieuwe items worden gemarkeerd met een geel sterretje \*; selecteer de vermelding Office365Mon.
   
   ![Schermopname van het navigatiedeelvenster in Power BI, met het dashboard, het rapport en de gegevensset.](media/service-connect-to-office365mon/dashboard4.png)

**Wat nu?**

* [Stel vragen in het vak Q&A](../consumer/end-user-q-and-a.md) boven in het dashboard.
* [Wijzig de tegels](../create-reports/service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](../consumer/end-user-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

## <a name="troubleshooting"></a>Problemen oplossen
Als u een fout **Aanmelden is mislukt** krijgt nadat u uw Office365Mon-abonnementsgegevens hebt gebruikt om in te loggen, dan heeft het account dat u gebruikt geen rechten om de Office365Mon-gegevens van uw account op te halen. Controleer of het een beheerdersaccount is en probeer het opnieuw.

## <a name="next-steps"></a>Volgende stappen
[Wat is Power BI?](../fundamentals/power-bi-overview.md)

[Gegevens ophalen voor Power BI](service-get-data.md)
