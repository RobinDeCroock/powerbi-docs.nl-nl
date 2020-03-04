---
title: Verbinding maken met Snowflake in Power BI
description: Snowflake met SSO voor Power BI
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: gepopell
LocalizationGroup: Connect to services
ms.openlocfilehash: 5e5519e30be30d6367791d1b6822196b407a21b1
ms.sourcegitcommit: 4d98274aa0b9aa09db99add2dda91a3ba8fed40b
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576863"
---
#  <a name="connecting-to-snowflake-in-power-bi-service"></a>Verbinding maken met Snowflake in de Power BI-service

## <a name="introduction"></a>Inleiding

Verbinding maken met Snowflake in de Power BI-service verschilt slechts op één manier van het maken van verbinding met andere connectors, namelijk dat er een extra capaciteit wordt aangeboden voor AAD (met een optie voor SSO). Voor verschillende delen van de integratie zijn verschillende beheerdersrollen vereist binnen Snowflake, Power BI en Azure. U kunt er ook voor kiezen om AAD-verificatie in te schakelen zonder SSO te gebruiken. Basisverificatie werkt op dezelfde manier voor andere connectors in de service.

Als u geïnteresseerd bent in het configureren van AAD-integratie en optionele inschakeling van SSO:
* Als u de Snowflake-beheerder bent, raadpleegt u het artikel [Power BI SSO met Snowflake - aan de slag](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html) in de Snowflake-documentatie.
* (SSO) Als u een Power BI-beheerder bent, raadpleegt u de sectie Power BI-serviceconfiguratie - beheerportal
* (SSO) Als u een maker van Power BI-gegevenssets bent, raadpleegt u de sectie Power BI-serviceconfiguratie - een gegevensset inschakelen

## <a name="power-bi-service-configuration"></a>Power BI-serviceconfiguratie

### <a name="admin-portal"></a>Beheerportal

Als u SSO wilt inschakelen, moet de tenantbeheerder naar de beheerportal gaan en het verzenden van Power BI AAD-referenties naar Snowflake goedkeuren.

![Tenantbeheerdersinstelling voor Snowflake-SSO](media/service-connect-snowflake/snowflakessotenant.png)

Ga naar uw beheerportal, selecteer het zijbalkitem Tenantinstellingen en schuif omlaag naar Integratie-instellingen. Nu ziet u een optie voor Snowflake-SSO.

Zoals eerder is opgemerkt, moet u deze optie handmatig instellen om toestemming te geven voor het verzenden van uw AAD-token naar de Snowflake-servers. Als u deze wilt inschakelen, klikt u op de wisselknop Uitgeschakeld, drukt u op Toepassen en wacht u tot de instellingswijziging van kracht is geworden. Het kan maximaal een uur duren voordat de configuratie is doorgegeven.

Als dit is gebeurd, kunt u rapporten gebruiken met SSO.

### <a name="configuring-a-dataset-with-aad"></a>Een gegevensset met AAD configureren

Zodra een rapport op basis van de Snowflake-connector is gepubliceerd op internet, moet de gegevenssetmaker naar de juiste werkruimte in de Power BI-webservice navigeren, Gegevenssets selecteren en Instellingen selecteren (onder het menu ... voor aanvullende acties naast de relevante gegevensset).

Door de manier waarop Power BI werkt, werkt SSO alleen wanneer er geen gegevensbronnen door de on-premises gegevensgateway worden geleid.

* Als u alleen een Snowflake-bron in uw gegevensmodel gebruikt, kunt u SSO gebruiken als u ervoor kiest de on-premises gegevensgateway niet te gebruiken
* Als u een Snowflake-bron naast een andere bron gebruikt, kunt u SSO gebruiken als geen van de bronnen gebruikmaakt van de on-premises gegevensgateway
* Als u een Snowflake-bron gebruikt via de on-premises gegevensgateway: AAD-referenties worden momenteel niet ondersteund. Dit kan relevant zijn voor als u probeert toegang te krijgen tot een VNet vanuit een enkel IP-adres waarop de gateway is geïnstalleerd, in plaats van vanuit het gehele IP-bereik van Power BI.
* Als u een Snowflake-bron gebruikt naast een andere bron waarvoor een gateway is vereist, moet u Snowflake ook via de on-premises gegevensgateway gebruiken en kunt u SSO niet gebruiken.

Zie het artikel [Wat is een on-premises gegevensgateway?](https://docs.microsoft.com/power-bi/service-gateway-onprem) voor meer informatie over het gebruik van de on-premises gegevensgateway

Als u de gateway niet wilt gebruiken, bent u klaar. Als u Snowflake-referenties hebt geconfigureerd in uw on-premises gegevensgateway, maar alleen die gegevensbron gebruikt in uw model, kunt u klikken op de wisselknop op de pagina Gegevenssetinstellingen om de gateway uit te schakelen voor dat gegevensmodel.

![Gegevenssetinstelling om de gateway uit te schakelen](media/service-connect-snowflake/snowflake_gateway_toggle_off.png)

De gegevenssetmaker moet Gegevensbronreferenties selecteren en zich aanmelden. De gegevensset kan worden aangemeld bij Snowflake met basisreferenties of OAuth2-referenties (AAD). Als u ervoor kiest om AAD te gebruiken, kan het gebruik van eenmalige aanmelding worden ingeschakeld voor de gegevensset. Wanneer deze eerste gebruiker zich aanmeldt bij Snowflake voor de gegevensset, moet deze de optie selecteren dat voor andere gebruikers hun Aauth2-referenties worden gebruikt om gegevens op te halen. Hiermee wordt AAD-SSO ingeschakeld. Voor SSO worden de AAD-referenties verzonden, ongeacht of de eerste gebruiker zich aanmeldt via basisverificatie of via OAuth2 (AAD). 

![Gegevenssetinstelling voor Snowflake-SSO](media/service-connect-snowflake/snowflakessocredui.png)

Als dit is gebeurd, wordt voor alle aanvullende gebruikers automatisch hun AAD-verificatie gebruikt om verbinding te maken met gegevens van deze Snowflake-gegevensset.

Als u ervoor kiest eenmalige aanmelding niet in te schakelen, worden voor gebruikers die het rapport vernieuwen de referenties gebruikt van de gebruiker die zich heeft aangemeld, zoals bij de meeste andere Power BI-rapporten.

### <a name="troubleshooting"></a>Problemen oplossen

Als u problemen ondervindt met de integratie, raadpleegt u de [Gids voor probleemoplossing](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html#troubleshooting) van Snowflake.

