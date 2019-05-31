---
title: Een rapport insluiten in een beveiligde portal of website
description: De Power BI ingesloten functie kunnen gebruikers eenvoudig en veilig insluiten van rapporten in interne webportals.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
LocalizationGroup: Share your work
ms.openlocfilehash: bf9d7bcdf6ddaf7d0063843a5314233989b2dadd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222245"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>Een rapport insluiten in een beveiligde portal of website

Met de nieuwe **insluiten** optie voor Power BI-rapporten, kunt u eenvoudig en veilig insluiten rapporten in interne webportals. Deze portals kunnen worden **cloud-gebaseerde** of **on-premises gehost**, zoals SharePoint 2019. Ingesloten rapporten respecteren item gegevens en machtigingen voor de beveiliging van alle via [beveiliging op rijniveau (RLS)](service-admin-rls.md). Ze bieden zonder code insluiten in een portal die een URL of een iFrame accepteert. 

De **insluiten** optie ondersteunt [URL-Filters](service-url-filters.md) en URL-instellingen. Hiermee kunt u om te integreren met een code van laag niveau aanpak vereisen alleen HTML en JavaScript basiskennis met portals.

## <a name="how-to-embed-power-bi-reports-into-portals"></a>Power BI-rapporten **insluiten** in portals

1. De nieuwe optie **Insluiten** is beschikbaar in het menu **Bestand** voor rapporten in Power BI-service.

    ![Optie Beveiligd insluiten in vervolgkeuzelijst](media/service-embed-secure/secure-embed-drop-down-menu.png)

2. Selecteer de **insluiten** optie om een dialoogvenster waarmee een koppeling en een iFrame die u gebruiken kunt voor het rapport veilig insluiten te openen.

    ![Dialoogvenster met optie Insluiten](media/service-embed-secure/secure-embed-code-dialog.png)

3. Of een gebruiker een rapport-URL rechtstreeks opent of een in een webportal ingesloten, vereist toegang tot rapporten verificatie. Het volgende scherm wordt weergegeven als een gebruiker is niet aangemeld bij Power BI in hun browsersessie. Wanneer ze selecteren **aanmelden**, een nieuw browservenster of tabblad kan worden geopend. Hebben ze pop blockers controleren als ze niet wordt gevraagd aan te melden.

    ![Aanmelden om dit rapport weer te geven](media/service-embed-secure/secure-embed-sign-in.png)

4. Nadat de gebruiker is aangemeld, het rapport wordt geopend, waarin de gegevens en kunnen de Paginanavigatie en filter instellen. Alleen gebruikers die gemachtigd zijn weergave ziet het rapport in Power BI. Alle [beveiliging op rijniveau (RLS)](service-admin-rls.md) regels worden ook toegepast. Ten slotte moet de gebruiker over de juiste licentie beschikken: de gebruiker moet een licentie hebben voor Power BI Pro of het rapport moet zich bevinden in een werkruimte met Power BI Premium-capaciteit. De gebruiker moet zich aanmelden elke keer dat ze een nieuw browservenster opent. Echter, zodra u bent aangemeld, andere rapporten automatisch geladen.

    ![Rapport insluiten](media/service-embed-secure/secure-embed-report.png)

5. Wanneer u een iFrame gebruikt, moet u mogelijk bewerken de **hoogte** en **breedte** te passen op de webpagina van de portal.

    ![Hoogte en breedte instellen](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-report-access"></a>Verlenen van toegang tot rapporten

De **insluiten** optie wordt niet automatisch dat gebruikers om het rapport weer te geven. Weergavemachtigingen zijn ingesteld in de Power BI-service.

U kunt in Power BI-service, ingesloten rapporten delen met gebruikers die toegang moeten hebben. Als u een Office 365-groep, kunt u de gebruiker weergeven als een lid van de app-werkruimte. Zie voor meer informatie over het [beheren van uw app-werkruimte in Power BI en Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md).

## <a name="licensing"></a>Licentieverlening

Als u wilt weergeven van het ingesloten rapport, gebruikers hebben een Power BI Pro licentie nodig of moet de inhoud zich in een werkruimte die zich in een [Power BI Premium-capaciteit (EM of P-SKU)](service-admin-premium-purchase.md).

## <a name="customize-your-embed-experience-using-url-settings"></a>Uw insluitervaring aanpassen met behulp van URL-instellingen

U kunt de gebruikerservaring met behulp van de ingesloten URL invoer instellingen aanpassen. U kunt de URL's bijwerken in de opgegeven iFrame **src** instellingen.

| Eigenschap  | Beschrijving  |  |  |  |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| pageName  | U kunt de **pageName** query-tekenreeksparameter om in te stellen welke pagina van het rapport te openen. U vindt deze waarde aan de rapport-URL einde wanneer u een rapport in Power BI-service, zoals hieronder wordt weergegeven. |  |  |  |
| URL-filters  | U kunt [URL-Filters](service-url-filters.md) in de ingesloten URL die u hebt ontvangen van de gebruikersinterface van Power BI voor het filteren van de inhoud insluiten. Op deze manier kunt u integraties bouwen met slechts weinig programmacode en alleen basiskennis van HTML en JavaScript.  |  |  |  |

## <a name="set-which-page-opens-for-an-embedded-report"></a>Welke pagina wordt geopend voor een ingesloten rapport instellen 

U vindt de **pageName** waarde achter de rapport-URL wanneer u een rapport in Power BI-service.

1. Het rapport openen vanuit de Power BI-service in uw webbrowser en kopieer vervolgens de URL van de balk adres.

    ![Rapportsectie](media/service-embed-secure/secure-embed-report-section.png)

2. Voeg de waarde van **pageName** toe aan de URL.

    ![pageName toevoegen](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>Rapportinhoud filteren met behulp van URL-filters 

U kunt [URL-Filters](service-url-filters.md) voor andere rapportweergaven. Met bijvoorbeeld de onderstaande URL wordt het rapport zo gefilterd dat alleen gegevens voor de energiesector worden weergegeven.

Het gebruik van de combinatie van **pageName** en [URL-filters](service-url-filters.md) kan zeer handig zijn. Met basiskennis van HTML en JavaScript kunt u ervaringen bouwen.

Dit is bijvoorbeeld een knop die u aan een HTML-pagina toevoegen kunt:

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

Als u selecteert, roept de knop een functie voor het bijwerken van de iFrame met een bijgewerkte-URL, waaronder het filter van de branche energie.

```javascript
function show(pageName, filterValue)

{

var newUrl = baseUrl + "&pageName=" + pageName;

if(null != filterValue && "" != filterValue)

{

newUrl += "&$filter=Industries/Industry eq '" + filterValue + "'";

}

//Assumes there’s an iFrame on the page with id=”iFrame”

var report = document.getElementById("iFrame")

report.src = newUrl;

}
```

![Filter](media/service-embed-secure/secure-embed-filter.png)

U kunt zo veel knoppen toevoegen als u wilt, om met weinig programmacode een aangepaste ervaring te maken. 

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

* Biedt geen ondersteuning voor externe gastgebruikers met Azure B2B (business to business).

* Beveiligd insluiten werkt voor rapporten die zijn gepubliceerd naar de Power BI-service.

* De gebruiker moet zich het rapport zien wanneer ze een nieuw browservenster opent.

* Sommige browsers moeten u de pagina vernieuwen na aanmelding, met name wanneer u InPrivate- of Incognito-modus.

* Een ervaring voor eenmalige aanmelding te bereiken, de insluiten in SharePoint Online-optie gebruiken of bouw een aangepaste integratie met de [gebruiker is eigenaar van gegevens](developer/embed-sample-for-your-organization.md) methode insluiten. 

* De mogelijkheid van automatische verificatie die bij de optie **Insluiten** wordt verstrekt, werkt niet met de Power BI JavaScript-API. Voor de Power BI JavaScript-API, gebruikt u de [gebruiker is eigenaar van gegevens](developer/embed-sample-for-your-organization.md) methode insluiten. 

## <a name="next-steps"></a>Volgende stappen

* [Manieren om uw werk in Power BI te delen](service-how-to-collaborate-distribute-dashboards-reports.md)

* [Een rapport filteren met queryreeksparameters in de URL](service-url-filters.md)

* [Insluiten met webonderdeel rapport in SharePoint Online](service-embed-report-spo.md)

* [Publiceren op Internet vanuit Power BI](service-publish-to-web.md)