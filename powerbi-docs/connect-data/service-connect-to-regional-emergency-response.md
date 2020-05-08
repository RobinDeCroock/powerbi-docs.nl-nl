---
title: Verbinding maken met het Regional Emergency Response Dashboard
description: De sjabloon-app COVID-19-ondersteuningsdashboard voor regionale noodhulp ophalen en installeren en verbinding maken met gegevens
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/24/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 6af8568dc39544ce064643c8dfb80fa2932cf13a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82149665"
---
# <a name="connect-to-the-regional-emergency-response-dashboard"></a>Verbinding maken met het Regional Emergency Response Dashboard
Het Regional Emergency Response Dashboard is het rapportageonderdeel van de [Regional Emergency Response-oplossing voor Microsoft Power Platform](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview). Beheerders van regionale organisaties kunnen het dashboard weergeven in hun Power BI-tenant, zodat ze snel belangrijke (metrische) gegevens kunnen weergeven aan de hand waarvan ze efficiënt beslissingen kunnen nemen.

![Rapport Regional Emergency Response Dashboard-app](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-report.png)

In dit artikel leest u hoe u de Regional Emergency Response-app installeert met behulp van de sjabloon-app Regional Emergency Response Dashboard en hoe u verbinding maakt met de gegevensbronnen.

Zie [Inzichten verkrijgen](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights) voor gedetailleerde informatie over wat er in het dashboard wordt weergegeven.

Nadat u de sjabloon-app hebt geïnstalleerd en verbinding hebt gemaakt met de gegevensbronnen, kunt u het rapport aanpassen aan uw behoeften. Vervolgens kunt u deze als app distribueren naar collega's in uw organisatie.

## <a name="prerequisites"></a>Vereisten

Voordat u deze sjabloon-app installeert, moet u eerst de [Regional Emergency Response-oplossing](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy) installeren en instellen. Als u deze oplossing installeert, worden de gegevensbronverwijzingen gemaakt die nodig zijn om de app te vullen met gegevens.

Let bij het installeren van de Regional Emergency Response-oplossing op de [URL van uw Common Data Service-omgevingsinstantie](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-5-configure-and-publish-power-bi-dashboard). U hebt deze nodig om de sjabloon-app te verbinden met de gegevens.

## <a name="install-the-app"></a>De app installeren

1. Klik op de volgende koppeling om naar de app te gaan: [De sjabloon-app Regional Emergency Response Dashboard](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Selecteer [**NU DOWNLOADEN**](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response) op de AppSource-pagina voor de app.

    [![De Regional Emergency Response Dashboard-app in AppSource](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-appsource-get-it-now.png)](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Selecteer **Installeren**. 

    ![De Regional Emergency Response Dashboard-app installeren](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-select-install.png)

    Zodra de app is geïnstalleerd, ziet u deze op uw Apps-pagina.

   ![De Regional Emergency Response Dashboard-app op de Apps-pagina](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Verbinding maken met gegevensbronnen

1. Selecteer het pictogram op de Apps-pagina om de app te openen.

1. Selecteer **Verkennen** op het welkomstscherm.

   ![Welkomstscherm van de sjabloon-app](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-splash-screen.png)

   De app wordt geopend met voorbeeldgegevens.

1. Selecteer de koppeling **Uw gegevens koppelen** op de banner bovenaan de pagina.

   ![De Regional Emergency Response Dashboard-app - koppeling voor koppelen van uw gegevens](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-connect-data.png)

1. Typ in het weergegeven dialoogvenster de [URL van uw Common Data Service-omgevingsinstantie](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). Bijvoorbeeld: https://[mijnomgeving].crm.dynamics.com. Klik op **Volgende** als u klaar bent.

   ![Het dialoogvenster met de URL van de Regional Emergency Response Dashboard-app](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-url-dialog.png)

1. In het volgende dialoogvenster dat wordt weergegeven, stelt u de verificatiemethode in op **OAuth2**. U hoeft niets te doen met de instelling voor het privacyniveau.

   Selecteer **Aanmelden**.

   ![Verificatiedialoogvenster van de Regional Emergency Response Dashboard-app](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-authentication-dialog.png)

1. Meld u op het Microsoft-aanmeldingsscherm aan bij Power BI.

   ![Het Microsoft-aanmeldingsscherm](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-microsoft-login.png)

   Nadat u zich hebt aangemeld, wordt het rapport verbonden met de gegevensbronnen en wordt het gevuld met actuele gegevens. Gedurende deze periode wordt de activiteitsbewaking ingeschakeld.

   ![De Regional Emergency Response Dashboard-app wordt vernieuwd](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Vernieuwen van het rapport plannen

Wanneer het vernieuwen van gegevens is voltooid, [stelt u een vernieuwingsschema in](../refresh-scheduled-refresh.md) om de rapportgegevens up-to-date te houden.

1. Selecteer op de bovenste koptekstbalk **Power BI**.

   ![Power BI-breadcrumb](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-powerbi-breadcrumb.png)

1. Zoek in het linkernavigatiedeelvenster onder **Werkruimten** naar de werkruimte Regional Emergency Response Dashboard en volgt de instructies in het artikel [Configure scheduled refresh](../refresh-scheduled-refresh.md) (Geplande vernieuwing configureren).

## <a name="customize-and-share"></a>Aanpassen en delen

Zie [De app aanpassen en delen](../service-template-apps-install-distribute.md#customize-and-share-the-app) voor meer informatie. Zorg ervoor dat u de [rapportdisclaimers](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview#disclaimer) controleert voordat u de app publiceert of distribueert.

## <a name="next-steps"></a>Volgende stappen
* [Inzicht krijgen in de Regional Emergency Response Dashboard](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights)
* [De voorbeeldsjabloon Crisis Communication instellen en leren kennen in Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
* [Wat zijn Power BI-sjabloon-apps?](../service-template-apps-overview.md)
* [Sjabloon-apps in uw organisatie installeren en distribueren](../service-template-apps-install-distribute.md)
