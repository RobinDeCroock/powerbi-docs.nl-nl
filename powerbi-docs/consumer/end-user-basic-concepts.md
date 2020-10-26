---
title: De Power BI-service - basisconcepten voor zakelijke gebruikers
description: Apps, werkruimten, dashboards, rapporten, gegevenssets en werkmappen in de Power BI-service.
author: mihart
ms.reviewer: mihart
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.custom: seodec18
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/08/2020
ms.author: mihart
LocalizationGroup: Get started
ms.openlocfilehash: 5c534436b93205d40251c26830be4d6acdfa034d
ms.sourcegitcommit: 6b436f6ed872cbc040ed6e2d3ac089c08fc78daf
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928357"
---
# <a name="basic-concepts-for-the-power-bi-service-consumers"></a>Basisconcepten voor consumenten van de Power BI-service

[!INCLUDE[consumer-appliesto-ynnm](../includes/consumer-appliesto-ynnm.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

In dit artikel wordt ervan uitgegaan dat u het [overzicht van Power BI](../fundamentals/power-bi-overview.md) al hebt gelezen en dat u voldoet aan de kenmerken van een [zakelijke gebruiker van Power BI](end-user-consumer.md). *Zakelijke gebruikers* ontvangen Power BI-inhoud, zoals dashboards, rapporten en apps, van collega's. *Zakelijke gebruikers* werken met de Power BI-service (app.powerbi.com), de browserversie van Power BI.

U kunt alleen inhoud van anderen ontvangen als aan een van de volgende voorwaarden wordt voldaan:
- U hebt een licentie op Power BI Pro
- Uw organisatie heeft een abonnement op Power BI Premium en de inhoud die met u wordt gedeeld, bevindt zich in een Premium-capaciteit. [Zoek het type licentie en abonnement op](end-user-license.md).

U hebt ongetwijfeld al gehoord van de term ‘Power BI Desktop’ of gewoon ‘Desktop’. Dit is het zelfstandige hulpprogramma dat wordt gebruikt door *ontwerpers* die dashboards bouwen en rapporten samenstellen, en deze met u delen. Het is belangrijk om te weten dat er ook andere Power BI-hulpprogramma’s beschikbaar zijn. Als zakelijk gebruiker** werkt u alleen met de Power BI-service. Dit artikel is alleen van toepassing op de Power BI-service.

## <a name="terminology-and-concepts"></a>Termen en concepten

Dit artikel is geen visuele rondleiding door Power BI en ook geen praktische zelfstudie. Het is in plaats hiervan een overzichtsartikel om u vertrouwd te maken met de termen en concepten van Power BI. U leert hiermee het jargon en de grondbeginselen kennen. Ga naar [Quickstart: navigeren in de Power BI-service](end-user-experience.md) voor een rondleiding van de Power BI-service en de bijbehorende navigatie.

## <a name="open-the-power-bi-service-for-the-first-time"></a>De Power BI-service voor het eerst openen

De meeste *zakelijke gebruikers* van Power BI krijgen de beschikking over de Power BI-service omdat 1) hun bedrijf licenties koopt en 2) een beheerder de licenties aan werknemers toewijst.

Als u wilt beginnen, opent u een browser en typt u **app.powerbi.com**. De eerste keer dat u de Power BI-service opent, ziet u iets dat vergelijkbaar is met het volgende:

![Een schermopname van het welkomstscherm voor de Power BI-service.](media/end-user-basic-concepts/power-bi-home-open.png)

Als u de Power BI-service gebruikt, kunt u aanpassen wat u ziet wanneer u de website in het vervolg opent. Sommige mensen willen graag dat Power BI wordt geopend met de **Startpagina**, terwijl anderen een favoriet dashboard hebben dat ze het eerst willen zien. Maak u zich geen zorgen. In deze twee artikelen leert u hoe u uw ervaring kunt aanpassen.

- [Inleiding tot de Power BI-startpagina en de algemene zoekopdracht](https://powerbi.microsoft.com/blog/introducing-power-bi-home-and-global-search)

- [Aanbevolen dashboards in de Power BI-service](end-user-featured.md)

![Een schermopname waarop de Startpagina en het dashboard worden weergegeven.](media/end-user-basic-concepts/power-bi-dash-home.png)

Maar voordat we verdergaan, doen we eerst een stapje terug en nemen we de bouwstenen van de Power BI-service door.

_______________________________________________________

## <a name="power-bi-content"></a>Power BI-inhoud

### <a name="introduction-to-building-blocks"></a>Inleiding tot bouwstenen

Dit zijn de vijf bouwstenen voor een *zakelijke gebruiker* van Power BI: **_visualisaties_**, **_dashboards_**, **_rapporten_**, **_apps_** en **_gegevenssets_** . Deze worden soms aangeduid als **_inhoud_** van *Power BI*. *Inhoud* bevindt zich in **_werkruimten_**. Een gebruikelijke werkstroom omvat alle bouwstenen: Een Power BI-*ontwerper* (geel in het onderstaande diagram) verzamelt gegevens uit *gegevenssets*, brengt deze over naar Power BI voor analyse, maakt *rapporten* met allerlei *visualisaties* die interessante feiten en inzichten benadrukken, maakt visualisaties uit rapporten vast aan *dashboards*, en deelt de rapporten en dashboards met *zakelijke gebruikers* zoals u (zwart in het onderstaande diagram). De *ontwerper* deelt ze in de vorm van dashboards, rapporten of apps.

![Een eenvoudig diagram voor een Power BI-werkstroom.](media/end-user-basic-concepts/power-bi-workflow.png)

In de eenvoudigste vorm:

- ![Een schermopname van het visualisatiepictogram.](media/end-user-basic-concepts/visual.png) een **_visualisatie_** (of *visual*), is een type diagram dat is gebouwd door Power BI-*ontwerpers*. In de visuals worden gegevens uit *rapporten* en *gegevenssets* weergegeven. Gewoonlijk maken *ontwerpers* de visuals in Power BI Desktop.

    Zie [Werken met visuals in rapporten, op dashboards en in apps](end-user-visualizations.md) voor meer informatie.

- ![Een schermopname van het databasepictogram](media/end-user-basic-concepts/power-bi-dataset-icon.png). Een *gegevensset* is een container net gegevens. Dit kan bijvoorbeeld een Excel-bestand zijn van de Wereldgezondheidsorganisatie. Het kan ook een database met gebruikers zijn die eigendom zijn van een bedrijf, of een Salesforce-bestand. Gegevenssets worden beheerd door *ontwerpers*.

- ![Een schermopname van het dashboardpictogram](media/end-user-basic-concepts/dashboard.png). Een *dashboard* is één scherm met interactieve visuals, tekst en grafische weergaven. Op een dashboard worden uw belangrijkste metrische gegevens op één scherm bij elkaar gebracht om een boodschap over te brengen of een vraag te beantwoorden. De inhoud van het dashboard komt uit een of meer rapporten en een of meer gegevenssets.

    Zie [Dashboards voor zakelijke gebruikers van de Power BI-service](end-user-dashboards.md) voor meer informatie.

- ![Een schermopname van het rapportpictogram](media/end-user-basic-concepts/report.png) Een *rapport* bevat een of meer pagina's met interactieve visuals, tekst en grafische weergaven die samen één geheel vormen. Een rapport in Power BI is gebaseerd op één gegevensset. *Ontwerpers* delen rapportpagina’s vaak zo in dat ze een gemeenschappelijke invalshoek of één vraagstuk behandelen.

    Zie [Rapporten in Power BI](end-user-reports.md) voor meer informatie.

- ![Een schermopname van het app-pictogram.](media/end-user-basic-concepts/app.png) Een *app* is een manier waarop *ontwerpers* gerelateerde dashboards en rapporten bundelen en delen. *Zakelijke gebruikers* ontvangen sommige apps automatisch, maar kunnen ook zoeken naar andere apps die zijn gemaakt door collega's of de community. Zo zijn er kant-en-klare apps beschikbaar voor externe services die u misschien al gebruikt, zoals Google Analytics of Microsoft Dynamics CRM.

Voor de duidelijkheid: als u een nieuwe gebruiker bent en u zich voor het eerst aanmeldt bij Power BI-service, ziet u waarschijnlijk nog geen dashboards, apps of rapporten.

_______________________________________________________

## <a name="datasets"></a>Gegevenssets

Een *gegevensset* is een verzameling gegevens die *ontwerpers* importeren of waar ze verbinding mee maken en die ze vervolgens gebruiken om rapporten en dashboards mee te maken. Als *zakelijke gebruiker* hebt u geen directe interactie met gegevenssets, maar het is wel handig om te weten hoe ze in het grotere geheel passen.  

Elke gegevensset vertegenwoordigt één gegevensbron. Voorbeelden van bronnen: een Excel-werkmap in OneDrive, een on-premises tabulaire gegevensset van SQL Server Analysis Services, of een Salesforce-gegevensset. Power BI biedt ondersteuning voor veel verschillende gegevensbronnen.

Wanneer een ontwikkelaar een app met u deelt, kunt u opzoeken welke gegevenssets worden gebruikt door de app. Dit doet u door **Gerelateerde inhoud** te openen.  U kunt echter niets in de gegevensset toevoegen of wijzigen. Als de ontwerper u echter machtigingen geeft, kunt u het rapport downloaden, zoeken naar [inzichten in de gegevens](end-user-insights.md) of zelfs [uw eigen rapport](../create-reports/service-report-create-new.md) maken op basis van de gegevensset.  

![Schermopname van de Power BI-gebruikersinterface en een pijl die wijst naar de sectie Gegevenssets op het canvas.](media/end-user-basic-concepts/power-bi-datasets.png)

Eén gegevensset...

- Kan steeds opnieuw worden gebruikt door een rapportontwerper om dashboards en rapporten te maken

- Kan worden gebruikt in tal van verschillende rapporten

- Visuals uit deze ene gegevensset kunnen worden weergegeven op een groot aantal verschillende dashboards

  ![Een afbeelding van een gegevensset met veel-op-een-relaties](media/end-user-basic-concepts/drawing2.png)

Nu over naar de volgende bouwsteen: visualisaties.

_______________________________________________________

## <a name="visualizations"></a>Visualisaties

Visualisaties (ook wel visuals genoemd) zijn voorstellingen van inzichten die door Power BI zijn gedetecteerd in de gegevens. Met visualisaties kunnen inzichten gemakkelijker worden geïnterpreteerd, omdat uw hersenen een afbeelding sneller kunnen doorgronden dan een spreadsheet met getallen.

Enkele voorbeelden van visualisaties die u in Power BI kunt tegenkomen: watervalgrafieken, linten, treemaps, cirkeldiagrammen, trechterdiagrammen, kaarten, spreidingsdiagrammen en meters.

   ![Een schermopname van acht voorbeelden van visuals.](media/end-user-basic-concepts/power-bi-visuals.png)

Zie de [volledige lijst met visualisaties in Power BI](end-user-visual-type.md).

Via de community zijn ook speciale visualisaties beschikbaar, die *aangepaste visuals* worden genoemd. Als u een rapport ontvangt met een visual die u niet herkent, is het waarschijnlijk een aangepaste visual. Als u hulp nodig hebt bij het interpreteren van de aangepaste visual, zoekt u de naam van de *ontwerper* van het rapport of dashboard, en neemt u contact met hem of haar op. Contactgegevens kunt u weergeven door de titel te selecteren in de bovenste menubalk.

Eén visualisatie in een rapport...

- Kan meerdere keren worden weergegeven in hetzelfde rapport

- Kan worden weergegeven op veel verschillende dashboards

_______________________________________________________

## <a name="reports"></a>Rapporten

Een Power BI-rapport bestaat uit een of meer pagina's met visualisaties, grafische weergaven en tekst. Alle visualisaties in een rapport zijn afkomstig uit één gegevensset. *Ontwerpers* bouwen rapporten en delen deze met anderen, hetzij individueel of als onderdeel van een app.  *Zakelijke gebruikers* hebben meestal [interactie met rapporten in de *leesweergave*](end-user-reading-view.md).

![Schermopname van een rapport met tabbladen.](media/end-user-basic-concepts/power-bi-report.png)

Eén rapport...

- Kan worden gekoppeld aan meerdere dashboards (tegels die zijn vastgemaakt vanuit dat rapport, kunnen worden weergegeven in meerdere dashboards).

- Kan worden gemaakt met gegevens uit slechts één gegevensset.  

- Kan deel uitmaken van meerdere apps.

  ![Een afbeelding waarop de relaties voor een rapport worden weergegeven.](media/end-user-basic-concepts/drawing5.png)

_______________________________________________________

## <a name="dashboards"></a>Dashboards

Een dashboard vertegenwoordigt een aangepaste grafische weergave van een subset van de onderliggende gegevensset(s). *Ontwerpers* bouwen dashboards en delen deze met *zakelijke gebruikers*, individueel of als onderdeel van een app. Een dashboard is een enkel canvas dat *tegels*, grafische weergaven en tekst bevat.

  ![Schermopname van een voorbeelddashboard](media/end-user-basic-concepts/power-bi-dashboard.png)

Een tegel is een weergave van een visual die een *ontwerper* *vastmaakt*, bijvoorbeeld vanuit een rapport aan een dashboard. Op elke vastgemaakte tegel wordt een [visualisatie](end-user-visualizations.md) weergegeven die door een ontwerper is gemaakt vanuit een gegevensset en vastgemaakt aan dit dashboard. Een tegel kan ook een volledige rapportpagina, live gestreamde gegevens of een video bevatten. Er zijn allerlei manieren waarop *ontwerpers* tegels aan een dashboard kunnen toevoegen. Het zijn er teveel om in dit overzichtsartikel te behandelen. Zie [Dashboardtegels in Power BI](end-user-tiles.md) voor meer informatie.

*Zakelijke gebruikers* kunnen dashboards niet bewerken. U kunt echter wel opmerkingen toevoegen, gerelateerde gegevens weergeven, een dashboard instellen als favoriet, u erop abonneren en meer.

Wat voor doelen hebben dashboards?  Hier volgen er slechts enkele:

- U kunt in één oogopslag alle benodigde informatie weergeven om een beslissing te nemen.

- U kunt de belangrijkste informatie over uw bedrijf bewaken

- U kunt er met dashboards voor zorgen dat alle collega's hetzelfde voor ogen hebben en allemaal dezelfde informatie zien en gebruiken

- de status in de gaten houden van een bedrijf, product, afdeling, marketingcampagne, enzovoort

- U kunt een gepersonaliseerde weergave van een groter dashboard maken met alle metrische gegevens die voor u belangrijk zijn

**Eén** dashboard

- kan visualisaties weergeven uit diverse gegevenssets,

- uit verschillende rapporten en

- kan visualisaties weergeven die zijn vastgemaakt vanuit andere hulpprogramma's (bijvoorbeeld Excel)

  ![Een afbeelding van relaties voor een dashboard.](media/end-user-basic-concepts/drawing1.png)

_______________________________________________________

## <a name="apps"></a>Apps

Met deze verzamelingen van dashboards en rapporten hebt u gerelateerde inhoud bij elkaar in één pakket. Power BI-*ontwerpers* bouwen ze in werkruimten en delen apps met personen, groepen, een hele organisatie of openbaar. Als *zakelijke gebruiker* kunt u er zeker van zijn dat uw collega's en u met dezelfde gegevens werken: één vertrouwde, onomstreden versie.

Soms wordt de werkruimte van de app zelf gedeeld en kunnen er veel personen samenwerken en zowel de werkruimte als de app bijwerken. Wat u met een app kunt doen, wordt bepaald door de machtigingen en toegang die u hebt gekregen.

![Schermopname van het scherm met machtigingen voor een app.](media/end-user-basic-concepts/power-bi-app-permissions.png)

> [!NOTE]
> Er is een Power BI Pro-licentie vereist om apps te gebruiken of de app-werkruimte moet zijn opgeslagen in een Premium-capaciteit. [Meer informatie over licenties](end-user-license.md).



Apps zijn gemakkelijk te vinden en te installeren in de [Power BI-service](https://powerbi.com) en op uw mobiele apparaat. Nadat u een app hebt geïnstalleerd, is het niet meer nodig om de namen van allerlei verschillende dashboards en rapporten te onthouden. U vindt deze allemaal samen in één app, in uw browser, of op uw mobiele apparaat.

Deze app heeft twee dashboards en twee rapporten die gezamenlijk één app vormen. Als u de pijl rechts van een rapportnaam selecteert, ziet u een lijst met pagina's waaruit dat rapport is opgebouwd.

![Schermopname van gerelateerde inhoud voor de geselecteerde app.](media/end-user-basic-concepts/power-bi-app-display.png)

Wanneer de app wordt bijgewerkt, ziet u automatisch de wijzigingen. De ontwerper bepaalt ook het schema voor het vernieuwen van de gegevens door Power BI. U hoeft u geen zorgen te maken over het up-to-date houden van deze gegevens.

U kunt apps op een aantal verschillende manieren verkrijgen:

- De app-ontwerper kan de app automatisch installeren in uw Power BI-account.

- De app-ontwerper kan u een directe koppeling naar een app sturen.

- U kunt vanuit de Power BI-service zoeken naar apps die aan u beschikbaar zijn gesteld door uw organisatie of door de community. U kunt ook naar [Microsoft AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi) gaan, waar u alle apps ziet die u kunt gebruiken.

In Power BI op uw mobiele apparaat kunt u apps alleen installeren via een rechtstreekse koppeling, niet vanuit AppSource. Als de app-ontwerper de app automatisch installeert, ziet u deze in uw lijst met apps.

Nadat de app is geïnstalleerd, hoeft u deze alleen maar te selecteren in de lijst met apps. Vervolgens kunt u selecteren welk dashboard of rapport u het eerst wilt openen en verkennen.

![Schermopname van apps die zijn geselecteerd in het linkerdeelvenster van Power BI.](media/end-user-basic-concepts/power-bi-apps-card.png)

Hopelijk hebt u met dit artikel een goed beeld gekregen van de bouwstenen waaruit de Power BI-service voor zakelijke gebruikers is samengesteld.

## <a name="next-steps"></a>Volgende stappen

- Bekijk de [Woordenlijst](end-user-glossary.md) en voeg deze toe aan favorieten

- Volg een [rondleiding door de Power BI-service](end-user-experience.md)

- Lees het [overzicht van Power BI dat speciaal is bedoeld voor zakelijke gebruikers](end-user-consumer.md)

- Bekijk een video waarin Will de basisconcepten bespreekt en een rondleiding door de Power BI-service geeft.

    <iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>
