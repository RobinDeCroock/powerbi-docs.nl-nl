---
title: Maak een koppeling naar een specifieke locatie in de Power BI - Mobiel-apps
description: Informatie over het maken van de dieptekoppeling naar een specifiek dashboard, tegel of rapport in de Power BI - Mobiel-app met een uniform resource identifier (URI).
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 11/16/2020
ms.author: painbar
ms.openlocfilehash: 08ddac0cf407444b4a4c135494c5951bab515cdd
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94669041"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Maak een koppeling naar een specifieke locatie in de Power BI - Mobiel-apps
U kunt koppelingen gebruiken om direct toegang te krijgen tot Power BI-inhoud, zoals een specifiek rapport, een rapportpagina, dashboard, tegel, enzovoort.

Er zijn hoofdzakelijk twee scenario's voor het gebruik van koppelingen voor toegang tot inhoud in de mobiele Power BI-apps: 

* Power BI kan van **buiten de mobiele app** worden geopend, waarna u bij specifieke inhoud belandt. Dit is doorgaans een integratiescenario, waarbij u de mobiele Power BI-app opent vanuit een andere app. 
* Door te **navigeren** in Power BI. Dit is meestal het geval als u een aangepaste navigatie wilt maken in Power BI.

In dit artikel komen de volgende gevallen aan bod:
* Koppelingen gebruiken om specifieke Power BI-inhoud te openen van buiten de mobiele app. Er worden twee koppelingsindelingen beschreven. De ene maakt gebruik van een omleidingsmethode en kan worden gebruikt, ongeacht waar Power BI wordt geopend. De andere wordt rechtstreeks in de mobiele Power BI-app geopend en werkt alleen op mobiele apparaten waarop de mobiele app is geïnstalleerd.
* Koppelingen binnen Power BI gebruiken om te navigeren naar specifieke Power BI-inhoud.

## <a name="use-links-from-outside-the-mobile-app"></a>Koppelingen van buiten de mobiele app gebruiken
Wanneer u een koppeling wilt maken naar een specifiek item in Power BI van buiten de mobiele app, zijn er twee opties, afhankelijk van waar de koppeling wordt geopend:

* Als u wilt dat de koppeling correct wordt geopend, ongeacht of er wordt geklikt in een computerbrowser of op een mobiel apparaat, kunt u een koppeling maken die ervoor zorgt dat deze correct wordt geopend, ongeacht waar op de koppeling wordt geklikt. Deze koppeling heeft een speciale omleidingssyntaxis om dit slimme gedrag in te schakelen.

* Als u weet dat de koppeling alleen wordt geopend op een mobiel apparaat waarop de Power BI Mobile-app is geïnstalleerd, kunt u de overhead voor omleiding van de bovenstaande methode vermijden en een andere koppelingssyntaxis gebruiken om de koppeling rechtstreeks in de mobiele Power BI-app op het mobiele apparaat te openen. Het is belangrijk te weten dat hoewel met deze koppeling de overhead voor omleiding van de eerste methode wordt vermeden, deze niet werkt als de koppeling ergens anders wordt geopend dan op een mobiel apparaat waarop de mobiele Power BI-app is geïnstalleerd.

### <a name="create-a-link-that-works-anywhere"></a>Een koppeling maken die overal kan worden gebruikt
De indeling van de koppeling die in deze sectie wordt beschreven, maakt gebruik van omleiding om te controleren of de koppeling werkt, ongeacht waar deze wordt geklikt.
* Als op de koppeling wordt geklikt op een mobiel apparaat, zorgt dit ervoor dat het apparaat de mobiele Power BI-app gebruikt om de koppeling te openen. Als de mobiele app niet op het apparaat is geïnstalleerd, wordt aan de gebruiker voorgesteld om naar de Store te gaan om deze te downloaden.
* Als op de koppeling wordt geklikt op een pc, wordt het relevante item in de Power BI-webportal geopend.

De koppeling moet beginnen met een speciaal voorvoegsel, gevolgd door queryparameters:

https<nolink>://app.powerbi.com/Redirect? **[QUERYPARAMETERS]** </code>

> [!IMPORTANT]
> Als uw inhoud wordt gehost in een speciaal datacentrum, zoals Government, China, enzovoort, moet de koppeling beginnen met het juiste Power BI-adres, zoals **app.powerbigov.us** of **app.powerbi.cn**.

Dit zijn de queryparameters:

|Parameter  | Waarde  | Beschrijving |
|---------|---------|---------|
|**actie** (verplicht)    | OpenApp<br>OpenReport<br>OpenDashboard<br>OpenTile | |
|**appId**| GUID van 36 tekens | Moet worden opgegeven als u een rapport of dashboard wilt openen dat onderdeel is van een app.<br>Voorbeeld: **appId=baf4b16d-b5bd-4360-8a3a-51d11242c09b** |
|**groupObjectId**| GUID van 36 tekens | Hiermee geeft u de werkruimte op als u een rapport of dashboard wilt openen dat geen onderdeel is van Mijn werkruimte.<br>Voorbeeld: **groupObjectId=9a3841c6-74b3-46f1-85fd-bdd78f27b30e** |
| **dashboardObjectId** | GUID van 36 tekens | Id van dashboardobject (als de actie OpenDashboard of OpenTile is)<br>Voorbeeld: **dashboardObjectId=033bb049-5b68-4392-b3ef-ae9a43738a4a** |
| **reportObjectId** | GUID van 36 tekens | Id van rapportobject (als de actie OpenReport is)<br>Voorbeeld: **reportObjectId=6114cec7-78e1-4926-88ff-0bc5338452cf** |
| **tileObjectId** | GUID van 36 tekens | Id van tegelobject (als de actie OpenTile is)<br>Voorbeeld: **tileObjectId=a845dcb8-a289-43a8-94ea-67a8c0a068f9** |
| **reportPage** | ReportSection&lt;num&gt; | Paginanaam als u een specifieke rapportpagina wilt openen. (als de actie OpenReport is)<br>Voorbeeld: **reportPage=ReportSection6**  |
| **bookmarkGuid** | GUID van 36 tekens | Id van een bladwijzer als u een specifieke weergave met bladwijzers wilt openen. (als de actie OpenReport is)<br>Voorbeeld: **bookmarkGuid=18e8872f-6db8-4cf8-8298-3b2ab254cc7f** |
| **ctid** | GUID van 36 tekens | Id van itemorganisatie (relevant voor B2B-scenario's. Deze kan worden weggelaten als het item tot de organisatie van de gebruiker behoort)<br>Voorbeeld: **ctid=5367c770-09d0-4110-bf6a-d760cb5ef681**. |
||||

**Voorbeelden:**

In de volgende voorbeelden worden tijdelijke aanduidingen voor de parameterwaarden vet gemarkeerd. Als u de werkelijke waarden wilt ophalen, gaat u naar de Power BI-service, opent u het item waarmee u een koppeling wilt maken en extraheert u de waarden die u nodig hebt uit de URL van het item.

* **Een app openen**

    https<nolink>://app.powerbi.com/Redirect?action=OpenApp&appId= **&lt;appid-guid&gt;** &ctid= **&lt;ctid-guid&gt;**
   
* **Een dashboard openen dat onderdeel is van een app**

    https<nolink>://app.powerbi.com/Redirect?action=OpenDashboard&appId= **&lt;appid-guid&gt;** &dashboardObjectId= **&lt;dashboardid-guid&gt;** &ctid= **&lt;ctid-guid&gt;**

* **Een rapport openen dat deel uitmaakt van een andere werkruimte dan Mijn werkruimte**

    https<nolink>://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId= **&lt;reportid-guid&gt;** &groupObjectId= **&lt;groupobjectid-guid&gt;** &reportPage=**ReportSection&lt;num&gt;**

### <a name="how-to-get-the-correct-link-format"></a>De correcte indeling van de koppeling verkrijgen

#### <a name="links-to-apps-and-items-in-apps"></a>Koppelingen naar apps en items in apps

De gemakkelijkste manier om een koppeling te verkrijgen voor **apps en rapporten en dashboards die onderdeel zijn van een app** is door naar de app-werkruimte te gaan en **App bijwerken** te kiezen. Hiermee wordt de ervaring App publiceren geopend. Open het tabblad Machtigingen en vouw het gedeelte Koppelingen uit om de koppelingen naar de app en de inhoud ervan weer te geven. U kunt deze koppelingen van buiten Power BI gebruiken om rechtstreeks toegang te krijgen tot de app en de inhoud ervan.

![Power BI-koppelingen voor het publiceren van de app ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-to-items-that-are-not-in-an-app"></a>Koppelingen naar items die zich niet in een app bevinden 

Voor rapporten en dashboards die geen onderdeel van een app zijn, moet u de object-id's die u nodig hebt extraheren uit de URL van het item. Hiervoor gaat u naar de Power BI-service, gaat u naar het item waarmee u een koppeling wilt maken en zoekt u naar de waarden die u nodig hebt in de URL die in de adresbalk van de browser wordt weergegeven.

In de onderstaande voorbeelden ziet u waar u de id's kunt vinden die u nodig hebt in de URL's van de items waarnaar u een koppeling wilt maken.

* Als u een dashboard-object-id van 36 tekens wilt vinden, gaat u naar het specifieke dashboard waarnaar u een koppeling wilt maken in de Power BI-service en zoekt u de object-id van het dashboard en eventuele andere vereiste id's op de hieronder vermelde locaties:

    https<nolink>://app.powerbi.com/groups/me/dashboards/ **&lt;dashboard-object-id&gt;** ?ctid= **&lt;org-object-id&gt;**

* Als u een rapport object-id van 36 tekens wilt vinden, gaat u naar het specifieke rapport waarnaar u een koppeling wilt maken in de Power BI-service en zoekt u de benodigde id's, zoals hieronder wordt beschreven. Dit voorbeeld bevat een verwijzing naar een specifieke rapportpagina en een specifieke bladwijzer.

    https<nolink>://app.powerbi.com/groups/me/reports/ **&lt;report-object-id&gt;** /**ReportSection&lt;num&gt;** ?bookmarkGuid= **&lt;bookmark-id&gt;**

* Als u een koppeling wilt maken naar een item in een andere werkruimte dan Mijn werkruimte, moet u de groepsobject-id extraheren. In dit voorbeeld wordt een rapport uit een andere werkruimte dan Mijn werkruimte weergegeven.

    https<nolink>://app.powerbi.com/groups/ **&lt;group-object-id&gt;** /reports/ **&lt;report-object-id&gt;** /**ReportSection&lt;report-section-num&gt;** ?ctid= **&lt;org-object-id&gt;**

### <a name="create-a-link-that-opens-only-on-a-device-that-has-the-power-bi-mobile-app-installed"></a>Een koppeling maken die alleen wordt geopend op een apparaat waarop de mobiele Power BI-app is geïnstalleerd

De indeling van de koppeling die in deze sectie wordt beschreven, is een koppeling naar een specifieke locatie in de mobiele Power BI-apps op alle mobiele platforms: iOS, Android-apparaten en Windows 10. Met deze koppelingsindeling wordt de locatie direct geopend, zonder een van de omleidingen die van toepassing zijn op de methode die is beschreven in de vorige sectie. **Deze indeling kan alleen worden geopend op mobiele apparaten waarop de mobiele Power BI-app is geïnstalleerd**.

Koppelingen met deze indeling kunnen rechtstreeks verwijzen naar dashboards, tegels en rapporten. De bestemming van de dieptekoppeling bepaalt de indeling. Volg deze stappen om dieptekoppelingen naar verschillende locaties te maken. 

* **De Power BI - Mobiel-app openen**

    Gebruik deze koppeling om de mobiele Power BI-app te openen op elk apparaat:

    mspbi://app/

* **Naar een specifiek dashboard openen**

    Met deze koppeling wordt de mobiele Power BI-app geopend naar een specifiek dashboard:

    mspbi://app/OpenDashboard?DashboardObjectId= **<36-character-dashboard-id>**

    Ga naar het specifieke dashboard in de Power BI-service om de object-id van het dashboard met 36 tekens op te halen en deze te extraheren uit de URL. De object-id van het dashboard wordt bijvoorbeeld gemarkeerd in de volgende URL van de Power BI-service:

    https<nolink>://app.powerbi.com/groups/me/dashboards/ **&lt;61b7e871-cb98-48ed-bddc-6572c921e270&gt;**

    Als het dashboard zich niet in Mijn werkruimte bevindt, moet u de id van het groepsobject ook toevoegen vóór of na de dashboard-id. De hieronder weergegeven dieptekoppeling heeft de id van het parametergroepsobject toegevoegd na de object-id van het dashboard:

    mspbi://app/OpenDashboard?DashboardObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**</code>

    Let op het en-teken (&) tussen de twee parameters.

* **Een specifieke tegel in focus openen**

    Met deze koppeling wordt een specifieke tegel in de focusmodus geopend in de mobiele Power BI-app:

    mspbi://app/OpenTile?DashboardObjectId= **<36-character-dashboard-id>** &TileObjectId= **<36-character-tile-id>**

    Ga naar het specifieke dashboard in de Power BI-service en open de tegel in de focusmodus om de dashboard- en tegelobject-id met 36 tekens op te halen. In het voorbeeld hieronder worden de id's van het dashboard en de tegel gemarkeerd.

    https<nolink>://app.powerbi.com/groups/me/dashboards/**3784f99f-b460-4d5e-b86c-b6d8f7ec54b7**/tiles/**565f9740-5131-4648-87f2-f79c4cf9c5f5**/infocus

    Als u de tegel direct wilt openen, zou de koppeling er als volgt uitzien:

    mspbi://app/OpenTile?DashboardObjectId=3784f99f-b460-4d5e-b86c-b6d8f7ec54b7&TileObjectId=565f9740-5131-4648-87f2-f79c4cf9c5f5

    Let op het en-teken (&) tussen de twee parameters.

    Als het dashboard zich niet in Mijn werkruimte bevindt, voegt u de parameter GroupObjectId toe, bijvoorbeeld &GroupObjectId = <36-character-group-id >

* **Naar een specifiek rapport openen**

    Met deze koppeling wordt een specifiek rapport geopend in de mobiele Power BI-app:

    mspbi://app/OpenReport?ReportObjectId= **<36-character-report-id>**

    Ga naar het specifieke rapport in de Power BI-service om de id van 36 tekens voor het rapport op te halen. De volgende URL uit de Power BI-service illustreert de rapport-id die u moet extraheren.

    https<nolink>://app.powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**

    Als het rapport zich niet in Mijn werkruimte bevindt, moet u **&GroupObjectId=<36-character-group-id>** ook toevoegen vóór of na de rapport-id. In dit geval zou de diepe koppeling er bijvoorbeeld als volgt uitzien:

    mspbi://app/OpenReport?ReportObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**

    Let op het en-teken (&) tussen de twee parameters.

* **Een specifieke rapportpagina openen**

    Met deze koppeling wordt een specifieke rapportpagina geopend in de mobiele Power BI-app:

    mspbi://app/OpenReport?ReportObjectId= **<36-character-report-id>** &reportPage=**ReportSection&lt;number&gt;**

    De rapportpagina heet **ReportSection**, gevolgd door een getal. Als u de gewenste waarden wilt vinden, opent u het rapport in de Power BI-service, gaat u naar de specifieke rapportpagina en extraheert u de waarden die u nodig hebt uit de URL. De gemarkeerde secties van deze URL vertegenwoordigen bijvoorbeeld de waarden die u moet openen voor een specifieke rapportpagina:

    https<nolink>://app.powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**/**ReportSection11**</code>

* **Openen in de modus Volledig scherm (alleen voor Windows-apparaten)**

    Voor Windows-apparaten kunt u ook de parameter **openFullScreen** toevoegen om een specifiek rapport te openen in de modus Volledig scherm. In het volgende voorbeeld wordt een rapportpagina geopend in de modus Volledig scherm:

    mspbi://app/OpenReport?ReportObjectId=500217de-50f0-4af1-b345-b81027224033&**openFullScreen=true**

* **Context toevoegen** (optioneel)

    U kunt ook context toevoegen aan de tekenreeks. Deze context kan worden gebruikt om onze relevante gegevens naar uw app te filteren als u contact met ons moet opnemen. Als u context wilt toevoegen, voegt u de parameter **context=&lt;app-name&gt;** toe aan de koppeling:

    In het volgende voorbeeld ziet u bijvoorbeeld een koppeling die een contextparameter bevat: 

    mspbi://app/OpenReport?ReportObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**&**context=SlackDeepLink**

## <a name="use-links-inside-power-bi"></a>Koppelingen gebruiken in Power BI

In de mobiele Power B-apps werken koppelingen in Power BI net zoals ze in de Power BI-service werken.

Als u aan uw rapport een koppeling wilt toevoegen die naar een ander Power BI-item verwijst, kunt u gewoon de URL van dat item kopiëren in de adresbalk van de browser. Lees meer over het [toevoegen van een hyperlink aan een tekstvak in een rapport](https://docs.microsoft.com/power-bi/service-add-hyperlink-to-text-box).

## <a name="next-steps"></a>Volgende stappen
Op basis van uw feedback kunnen we bepalen wat in de toekomst moet worden geïmplementeerd. Vergeet dus niet op andere functies te stemmen die u graag in de mobiele Power BI-apps zou willen zien. 

* [Power BI-apps voor mobiele apparaten](mobile-apps-for-mobile-devices.md)
* Volg @MSPowerBI op Twitter
* Deelnemen aan conversaties in de [Power BI-community](http://community.powerbi.com/)
* [Wat is Power BI?](../../power-bi-overview.md)
