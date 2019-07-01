---
title: Sjabloon-apps in uw organisatie distribueren - Power BI
description: Meer informatie over het installeren, aanpassen en distribueren van sjabloon-apps in uw organisatie in Power BI.
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: tebercov
ms.openlocfilehash: 158345c44f8801a98e19dcd9b4c7dde14aa6126b
ms.sourcegitcommit: 8c52b3256f9c1b8e344f22c1867e56e078c6a87c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/19/2019
ms.locfileid: "67264525"
---
# <a name="install-and-distribute-template-apps-in-your-organization---power-bi"></a>Sjabloon-apps in uw organisatie installeren en distribueren - Power BI

Bent u een Power BI-analist? In dat geval leest u in dit artikel hoe u *sjabloon-apps* installeert om in verbinding te komen met de vele services waarmee u uw bedrijfsactiviteiten uitvoert, zoals Salesforce, Microsoft Dynamics en Google Analytics. U kunt het dashboard en de rapporten aanpassen om aan de behoeften van uw organisatie te voldoen en deze vervolgens als *app* naar uw collega's distribueren. 

![Geïnstalleerde Power BI-apps](media/service-template-apps-install-distribute/power-bi-get-apps.png)

Zie [Een sjabloon-app maken in Power BI](service-template-apps-create.md) als u meer wilt weten over het maken van sjabloon-apps die u zelf kunt distribueren. Power BI-partners kunnen Power BI-apps bouwen met weinig of geen code en deze implementeren naar Power BI-klanten. 

## <a name="prerequisites"></a>Vereisten  

Dit zijn de vereisten voor het installeren, aanpassen en distribueren van een sjabloon-app: 

- Een [Power BI Pro-licentie](service-self-service-signup-for-power-bi.md)
- Vertrouwd zijn met de [basisconcepten van Power BI](service-basic-concepts.md)
- Een geldige koppeling voor de installatie van de maker van de sjabloon-app of AppSource. 
- Machtigingen voor het installeren van sjabloon-apps. 

## <a name="install-a-template-app"></a>Een sjabloon-app installeren

U ontvangt mogelijk een koppeling naar een sjabloon-app. Als dit niet het geval is, kunt u in AppSource zoeken naar een sjabloon-app waarin u bent geïnteresseerd. Nadat u de sjabloon-app hebt geïnstalleerd, kunt u deze wijzigen en naar uw eigen organisatie distribueren.

### <a name="search-appsource-from-a-browser"></a>In AppSource zoeken vanuit een browser

Selecteer in een browser deze koppeling om AppSource te openen, waarbij is gefilterd op Power BI-apps:

- https://appsource.microsoft.com/marketplace/apps?product=power-bi

### <a name="search-appsource-from-the-power-bi-service"></a>In AppSource zoeken vanuit de Power BI-service

1. Selecteer in de Power BI-service in het navigatiedeelvenster aan de linkerkant **Apps** > **Apps ophalen**.

    ![Apps ophalen](media/service-template-apps-install-distribute/power-bi-get-apps-arrow.png)

2. Selecteer in AppSource **Apps**.

    ![Zoeken in AppSource](media/service-template-apps-install-distribute/power-bi-appsource.png)

3. Blader of zoek de app en selecteer vervolgens **Nu downloaden**.

4. Selecteer **Installeren** in het dialoogvenster.

    ![App installeren](media/service-template-apps-install-distribute/power-install-dialog.png) Als u een Power BI Pro-licentie hebt, wordt de app geïnstalleerd met de bijbehorende app-werkruimte. U past de app aan in de bijbehorende werkruimte.

    Wanneer de installatie is geslaagd, ziet u een melding dat uw nieuwe app gereed is.
4. Selecteer **Naar de app**.
5. Selecteer in **Aan de slag met uw nieuwe app**  een van de volgende drie opties:

    ![Aan de slag met uw app](media/service-template-apps-create/power-bi-template-app-get-started.png)

    - **App verkennen**: De voorbeeldgegevens verkennen. Begin hier om het uiterlijk en de werking van de app te zien. 
    - **Verbinding maken met gegevens**: Vervang de gegevensbron van de voorbeeldgegevens door uw eigen gegevensbron. U kunt de parameters van de gegevensset en de referenties van de gegevensbron opnieuw definiëren. Zie [Bekende beperkingen](service-template-apps-tips.md#known-limitations) in het artikel met tips voor sjabloon-apps. 
    - **Naar de werkruimte** (meest geavanceerde optie): u kunt wijzigingen aanbrengen die door de ontwikkelaar van de app zijn toegestaan.

    U kunt dit dialoogvenster ook overslaan en direct de bijbehorende werkruimte openen via **Werkruimten** in het navigatiedeelvenster aan de linkerkant.
    >[!NOTE]
    >Door een sjabloon-app te installeren, worden ook een *organisatie-app* en een *app-werkruimte* geïnstalleerd. Lees meer over [het distribueren van apps in Power BI](service-create-distribute-apps.md).
 
6. Voordat u de app met uw collega's deelt, kunt u verbinding maken met uw eigen gegevens. U kunt ook het rapport of dashboard wijzigen, zodat dit geschikt is voor uw organisatie. Ook kunt u hier andere rapporten of dashboards toevoegen.

   Als u een installatiekoppeling selecteert voor een app die niet in AppSource is vermeld, wordt het dialoogvenster voor validatie weergegeven waarin u uw keuze moet bevestigen.

   ![App installeren](media/service-template-apps-install-distribute/power-install-unvalidated-dialog.png)

   >[!NOTE]
   >Als u sjabloon-apps wilt installeren die niet in AppSource is vermeld, moet u machtigingen aanvragen bij uw beheerder. Zie de Power BI-[beheerderportal en Instellingen voor sjabloon-apps](service-admin-portal.md#template-apps-settings) voor meer informatie.

## <a name="update-and-distribute-the-app"></a>De app bijwerken en distribueren

Nadat u de app voor uw organisatie hebt bijgewerkt, kunt u de app publiceren. De stappen hiervoor zijn dezelfde als voor het publiceren van andere apps.

1. Wanneer u klaar bent met het aanpassen van de app, selecteert u **App bijwerken** in de rechterbovenhoek in de lijstweergave van de werkruimte.  

    ![De installatie van de app starten](media/service-template-apps-install-distribute/power-bi-start-install-app.png)

2. In **Details** kunt u de beschrijving en achtergrondkleur wijzigen.

   ![De app-beschrijving en -kleur instellen](media/service-template-apps-install-distribute/power-bi-install-app-details.png)

3. In **Inhoud** kunt u een landingspagina selecteren. Dit is het dashboard of het rapport.

   ![Landingspagina van app instellen](media/service-template-apps-install-distribute/power-bi-install-app-content.png)

4. In **Toegang** geeft u toegang aan geselecteerde gebruikers of aan de hele organisatie.  

   ![App-toegang instellen](media/service-template-apps-install-distribute/power-bi-install-access.png)

5. Selecteer **App bijwerken**. 

6. Nadat de app is gepubliceerd, kunt u de koppeling kopiëren en delen met degenen die u toegang hebt gegeven. Als u de app met hen hebt gedeeld, zien zij de app ook op het tabblad **Mijn organisatie** in AppSource.

## <a name="next-steps"></a>Volgende stappen 

[Werkruimten maken met uw collega's in Power BI](service-create-workspaces.md)





  

 
