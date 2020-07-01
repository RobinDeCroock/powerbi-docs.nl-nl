---
title: Verbinding maken met Zendesk met Power BI
description: Zendesk voor Power BI
author: paulinbar
ms.reviewer: sarinas
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/04/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 6cac39407cac3af833656a4e94edf9a3c80bbc26
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85231633"
---
# <a name="connect-to-zendesk-with-power-bi"></a>Verbinding maken met Zendesk met Power BI

In dit artikel wordt uitgelegd hoe u uw gegevens ophaalt uit uw Zendesk-account met een Power BI-sjabloon-app. De Zendesk-app biedt een Power BI-dashboard en een set Power BI-rapporten die inzicht geven in uw ticketaantallen en agentprestaties. De gegevens worden eenmaal per dag automatisch vernieuwd. 

Nadat u de sjabloon-app hebt geïnstalleerd, kunt u het dashboard en rapport aanpassen om de informatie te markeren die u het belangrijkst vindt. Vervolgens kunt u deze als een app distribueren naar collega's in uw organisatie.

Maak verbinding met de [Zendesk-app](https://app.powerbi.com/getdata/services/zendesk) of lees meer over de [Zendesk-integratie](https://powerbi.microsoft.com/integrations/zendesk) met Power BI.

Nadat u de sjabloon-app hebt geïnstalleerd, kunt u het dashboard en rapport wijzigen. Vervolgens kunt u deze als een app distribueren naar collega's in uw organisatie.

>[!NOTE]
>U hebt een Zendesk-beheerdersaccount nodig om verbinding te maken. Meer informatie over de [vereisten](#system-requirements) leest u hieronder.

## <a name="how-to-connect"></a>Verbinding maken

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Selecteer **Zendesk** \> **Nu downloaden**.
4. Selecteer in **Deze Power BI-app installeren?** de optie **Installeren**.
4. Selecteer in het deelvenster **Apps** de tegel **Zendesk**.

    ![Tegel voor Zendesk-app voor Power BI](media/service-connect-to-zendesk/power-bi-zendesk-tile.png)

6. Selecteer in **Aan de slag met uw nieuwe app** de optie **Verbinding maken**.

    ![Aan de slag met uw nieuwe app](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Geef de URL die is gekoppeld aan uw account. De URL heeft de vorm **https://company.zendesk.com** . Hieronder vindt u informatie over [het vinden van deze parameters](#finding-parameters).
   
   ![Verbinding maken met Zendesk](media/service-connect-to-zendesk/pbi_zendeskconnect.png)

5. Geef desgevraagd uw Zendesk-referenties op.  Selecteer **oAuth 2** als verificatiemethode en klik op **Aanmelden**. Volg de Zendesk-verificatieprocedure. (Als u al bent aangemeld bij Zendesk in uw browser, ontvangt u mogelijk geen prompt om referenties in te voeren.)
   
   > [!NOTE]
   > Voor deze sjabloon-app moet u verbinding maken met een Zendesk-beheerdersaccount. 
   > 
   
   ![Aanmelden met oAuth2](media/service-connect-to-zendesk/pbi_zendesksignin.png)
6. Klik op **Toestaan** om Power BI toegang te geven tot uw Zendesk-gegevens.
   
   ![Klik op Toestaan](media/service-connect-to-zendesk/zendesk2.jpg)
7. Klik op **Verbinding maken** om het importproces te starten. 
8. Nadat de gegevens in Power BI zijn geïmporteerd, ziet u de lijst met inhoud voor uw Zendesk-app: een nieuw dashboard, een nieuw rapport en een nieuwe gegevensset.
9. Selecteer het dashboard om het verkenningsproces te starten.

    ![Zendesk-dashboard](media/service-connect-to-zendesk/power-bi-zendesk-dashboard.png)
   
## <a name="modify-and-distribute-your-app"></a>Uw app wijzigen en distribueren

U hebt de Zendesk-sjabloon-app geïnstalleerd. Dit betekent dat u ook de Zendesk-werkruimte hebt gemaakt. In de werkruimte kunt u het rapport en dashboard wijzigen en deze vervolgens als een *app* naar collega's in uw organisatie distribueren. 

1. Als u alle inhoud van de nieuwe Zendesk-werkruimte wilt weergeven, selecteert u in het navigatievenster **Werkruimten** > **Zendesk**. 

    ![Zendesk-werkruimte in het navigatievenster](media/service-connect-to-zendesk/power-bi-zendesk-workspace-left-nav.png)

    Deze weergave is de inhoudslijst voor de werkruimte. In de rechterbovenhoek ziet u **App bijwerken**. Wanneer u klaar bent om uw app naar uw collega's te distribueren, kunt u beginnen. 

    ![Zendesk-inhoudslijst](media/service-connect-to-zendesk/power-bi-zendesk-content-list.png)

2. Selecteer **Rapporten** en **Gegevenssets** om de andere elementen in de werkruimte weer te geven.

    Meer informatie over [apps distribueren](../collaborate-share/service-create-distribute-apps.md) naar uw collega's.

## <a name="system-requirements"></a>Systeemvereisten
Een Zendesk-beheerdersaccount is vereist voor toegang tot de Zendesk-sjabloon-app. Als u een agent of een gebruiker bent en u wilt uw Zendesk-gegevens weergeven, voegt u een suggestie toe en controleert u de Zendesk-connector in de [Power BI Desktop](desktop-connect-to-data.md).

## <a name="finding-parameters"></a>Parameters zoeken
De URL van uw Zendesk is hetzelfde als de URL die u gebruikt bij het aanmelden bij uw Zendesk-account. Als u niet zeker weet wat uw Zendesk-URL is, kunt u de [hulp bij aanmelden](https://www.zendesk.com/login/) van Zendesk gebruiken.

## <a name="troubleshooting"></a>Problemen oplossen
Als u problemen ondervindt bij het maken van verbinding, controleer dan uw Zendesk-URL en bevestig dat u een Zendesk-beheerdersaccount gebruikt.

## <a name="next-steps"></a>Volgende stappen

* [De nieuwe werkruimten maken in Power BI](../collaborate-share/service-create-the-new-workspaces.md)
* [Apps in Power BI installeren en gebruiken](../consumer/end-user-apps.md)
* [Verbinding maken met Power BI-apps voor externe services](service-connect-to-services.md)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
