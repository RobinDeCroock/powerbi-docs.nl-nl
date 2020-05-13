---
title: Verbinding maken met Aanwezigheidsrapport voor Crisis Communication
description: Informatie over het ophalen en installeren van de sjabloon-app COVID-19-aanwezigheidsrapport voor Crisis Communication en het maken van verbinding met gegevens
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: fef6bc5c396ccaf89ff4cd0e5a449cb9d01ce75b
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83275496"
---
# <a name="connect-to-the-crisis-communication-presence-report"></a>Verbinding maken met Aanwezigheidsrapport voor Crisis Communication

Deze Power BI-app is het rapport/dashboard-artefact in de Microsoft Power Platform-oplossing voor Crisis Communication. Hiermee wordt de locatie van werknemers bijgehouden voor gebruikers van de app Crisis Communication. De oplossing biedt een combinatie van de mogelijkheden van Power Apps, Power Automate, Teams, SharePoint en Power BI. Deze oplossing kan worden gebruikt op internet, op mobiele apparaten of in Teams.

![Het app-rapport Aanwezigheidsrapport voor Crisis Communication](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report.png)

Op het dashboard wordt weergegeven dat managers voor noodsituaties gegevens van hun zorgsystemen aggregeren om tijdige, juiste beslissingen te kunnen nemen.

In dit artikel leest u hoe u de app installeert en hoe u verbinding maakt met de gegevensbronnen. Zie [De voorbeeldsjabloon Crisis Communication instellen en leren kennen in Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app) voor meer informatie over de app Crisis Communication

Nadat u de sjabloon-app hebt geïnstalleerd en verbinding hebt gemaakt met de gegevensbronnen, kunt u het rapport aanpassen aan uw behoeften. Vervolgens kunt u deze als app distribueren naar collega's in uw organisatie.

## <a name="prerequisites"></a>Vereisten

Voordat u deze sjabloon-app installeert, moet u eerst het [Crisis Communication-voorbeeld](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app) installeren en instellen. Als u deze oplossing installeert, worden de gegevensbronverwijzingen gemaakt die nodig zijn om de app te vullen met gegevens.

Let bij het installeren van het Crisis Communication-voorbeeld op het [SharePoint-lijstmappad van CI_Employee Status en de lijst-id](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi).

## <a name="install-the-app"></a>De app installeren

1. Klik op de volgende koppeling om naar de app te gaan: [De sjabloon-app Aanwezigheidsrapport voor Crisis Communication](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. Selecteer [**NU DOWNLOADEN**](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms) op de AppSource-pagina voor de app.

    [![De rapport-app Aanwezigheidsrapport voor Crisis Communication in AppSource](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-appsource-get-it-now.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. Lees de informatie in **Nog iets...** en selecteer **Doorgaan**.

    ![De rapport-app Aanwezigheidsrapport voor Crisis Communication, Nog iets...](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-1-more-thing.png)

1. Selecteer **Installeren**. 

    ![De app Aanwezigheidsrapport voor Crisis Communication installeren](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-select-install.png)

    Zodra de app is geïnstalleerd, ziet u deze op uw Apps-pagina.

   ![De rapport-app Aanwezigheidsrapport voor Crisis Communication op de App-pagina](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Verbinding maken met gegevensbronnen

1. Selecteer het pictogram op de Apps-pagina om de app te openen.

1. Selecteer **Verkennen** op het welkomstscherm.

   ![Welkomstscherm van de sjabloon-app](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-splash-screen.png)

   De app wordt geopend met voorbeeldgegevens.

1. Selecteer de koppeling **Uw gegevens koppelen** op de banner bovenaan de pagina.

   ![De koppeling Uw gegevens verbinden van de rapport-app Aanwezigheidsrapport voor Crisis Communication op de App-pagina](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-connect-data.png)

1. Ga als volgt te werk in het dialoogvenster:
   1. Voer in het veld SharePoint_Folder uw [CI_Employee Status van het SharePoint-lijstpad](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi) in.
   1. Voer in het veld List_ID de lijst-id in die u hebt verkregen via de lijstinstellingen. Klik op **Volgende** als u klaar bent.

   ![URL-dialoogvenster van de app Aanwezigheidsrapport voor Crisis Communication](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-url-dialog.png)

1. In het volgende dialoogvenster dat wordt weergegeven, stelt u de verificatiemethode in op **OAuth2**. U hoeft niets te doen met de instelling voor het privacyniveau.

   Selecteer **Aanmelden**.

   ![Verificatiedialoogvenster van de app Aanwezigheidsrapport voor Crisis Communication](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-authentication-dialog.png)

1. Meld u op het Microsoft-aanmeldingsscherm aan bij Power BI.

   ![Het Microsoft-aanmeldingsscherm](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-microsoft-login.png)

   Nadat u zich hebt aangemeld, wordt het rapport verbonden met de gegevensbronnen en wordt het gevuld met actuele gegevens. Gedurende deze periode wordt de activiteitsbewaking ingeschakeld.

   ![De app Aanwezigheidsrapport voor Crisis Communication wordt vernieuwd](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Vernieuwen van het rapport plannen

Wanneer het vernieuwen van gegevens is voltooid, [stelt u een vernieuwingsschema in](../connect-data/refresh-scheduled-refresh.md) om de rapportgegevens up-to-date te houden.

1. Selecteer op de bovenste koptekstbalk **Power BI**.

   ![Power BI-breadcrumb](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-powerbi-breadcrumb.png)

1. Zoek in het linkernavigatiedeelvenster onder **Werkruimten** naar de werkruimte Ondersteuningsdashboard voor Hospital Emergency Response en volgt de instructie in het artikel [Geplande vernieuwing configureren](../connect-data/refresh-scheduled-refresh.md).

## <a name="customize-and-share"></a>Aanpassen en delen

Zie [De app aanpassen en delen](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app) voor meer informatie. Zorg ervoor dat u de [rapportdisclaimers](../create-reports/sample-covid-19-us.md#disclaimers) controleert voordat u de app publiceert of distribueert.

## <a name="next-steps"></a>Volgende stappen
* [De voorbeeldsjabloon Crisis Communication instellen en leren kennen in Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
* [Wat zijn Power BI-sjabloon-apps?](../connect-data/service-template-apps-overview.md)
* [Sjabloon-apps in uw organisatie installeren en distribueren](../connect-data/service-template-apps-install-distribute.md)
