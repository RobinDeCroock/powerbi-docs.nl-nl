---
title: Basisconcepten voor ontwerpers in de Power BI-service
description: Werkruimten, dashboard, rapporten, gegevenssets en werkmappen in de Power BI-service.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: ff962335b573c6dd2a03ae5ab4633c1042a77059
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770773"
---
# <a name="basic-concepts-for-designers-in-the-power-bi-service"></a>Basisconcepten voor ontwerpers in de Power BI-service

Het doel van dit artikel is om u wegwijs te maken in de Power BI-service: wat zijn de verschillende elementen, hoe werken deze samen en hoe kunt u ermee werken? In dit artikel wordt ervan uitgegaan dat u [zich al hebt aangemeld voor de Power BI-service](service-self-service-signup-for-power-bi.md) en [enkele gegevens hebt toegevoegd](service-get-data.md). Als ontwerper begint uw workflow doorgaans met het maken van rapporten in Power BI Desktop. Vervolgens publiceert u deze in de Power BI-service, waar u ze verder kunt aanpassen. In de Power BI-service maakt u ook de dashboards op basis van uw rapporten. 

Voor dit artikel geldt: als u nog geen eigen rapporten hebt, kunt een [pakket met voorbeeldinhoud voor Power BI](sample-datasets.md#the-power-bi-samples-as-content-packs) installeren.

![Startscherm van de Power BI-service in een browser](media/service-basic-concepts/power-bi-home-screen.png)

Wanneer u de Power BI-service in een browser opent, start u bij het startscherm. Dit zijn de elementen die u mogelijk te zien krijgt:

1. Navigatiedeelvenster (linkernavigatie)
2. Startprogramma voor de Office 365-app
3. Knop voor de startpagina van Power BI
4. Pictogramknoppen, inclusief instellingen, help en feedback
5. Zoekvak
6. Tegels van een favoriet dashboard
7. Favoriete en frequente dashboards en rapporten

De eindgebruikers van uw rapporten en dashboards hebben dezelfde startervaring in de Power BI-service in een browser.

Meer informatie over deze functies volgt later, maar laten we eerst enkele concepten van Power BI bekijken. Of bekijk eerst deze video.  In de video bespreekt Will de basisconcepten aan de hand van een rondleiding door de Power BI-service.

<iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>


## <a name="power-bi-concepts"></a>Power BI-concepten
De vier primaire bouwstenen van Power BI zijn: **_dashboards_** , **_rapporten_** , **_werkmappen_** en **_gegevenssets_** . Deze zijn ingedeeld in **_werkruimten_** . Het is belangrijk om te begrijpen hoe werkruimten werken voordat we ons verdiepen in de vier bouwstenen. Laten we dus bij het begin beginnen.

## <a name="workspaces"></a>Werkruimten
Werkruimten zijn containers voor dashboards, rapporten, werkmappen en gegevenssets in Power BI. Er zijn twee typen werkruimten: *Mijn werkruimte* en *app-werkruimten*. Wat is een *app* nu precies? Een Power BI-*app* is een verzameling dashboards en rapporten die is gebouwd om belangrijke metrische gegevens te leveren aan de Power BI-eindgebruikers in uw organisatie. Apps zijn interactief, maar eindgebruikers kunnen ze niet bewerken.

- *Mijn werkruimte* is de persoonlijke werkruimte voor een klant van Power BI om met de eigen inhoud te kunnen werken. Alleen u hebt toegang tot uw Mijn werkruimte. U kunt dashboards en rapporten delen vanuit uw Mijn werkruimte. Als u wilt samenwerken aan dashboards en rapporten, of een app wilt maken, gaat u naar een app-werkruimte.      
-  *App-werkruimten* worden gebruikt om te samen te werken en inhoud te delen met collega’s. Het is ook de plek om apps voor uw organisatie te maken, publiceren en beheren. U kunt ze beschouwen als tijdelijke locaties en containers voor de inhoud die straks een Power BI-app zullen vormen. U kunt collega's toevoegen aan uw app-werkruimten en samenwerken aan dashboards, rapporten, werkmappen en gegevenssets. Power BI Pro-licenties nodig zijn voor leden van alle app-werkruimte. App-gebruikers, de collega's die toegang tot de apps hebben nodig niet per se Pro-licenties. Meer informatie over de [nieuwe werkruimten](service-create-the-new-workspaces.md).  

Voor meer informatie over het delen van in het algemeen, beginnen met [manieren om uw werk delen van dashboards](service-how-to-collaborate-distribute-dashboards-reports.md).

Laten we het nu hebben over de bouwstenen van Power BI. U kunt geen dashboards of rapporten maken zonder gegevens (u kunt uiteraard lege dashboards en rapporten maken, maar deze zijn pas bruikbaar wanneer ze gegevens bevatten). Laten we beginnen met **gegevenssets**.

## <a name="datasets"></a>Gegevenssets
Een *gegevensset* is een verzameling gegevens die u *importeert* of waar u *verbinding* mee maakt. Met Power BI kunt u diverse soorten gegevenssets importeren of hier verbinding mee maken en alle gegevens samen te brengen op één locatie.  

Gegevenssets zijn gekoppeld aan *werkruimten* en één gegevensset kan deel uitmaken van veel werkruimten. Wanneer u een werkruimte opent, worden de bijbehorende gegevenssets vermeld op het tabblad **Gegevenssets**. Elke vermelde gegevensset vertegenwoordigt één bron van gegevens, bijvoorbeeld een Excel-werkmap in OneDrive, een on-premises SSAS-gegevensset in tabelvorm of een Salesforce-gegevensset. Er worden diverse verschillende gegevensbronnen ondersteund en er worden voortdurend nieuwe bronnen toegevoegd. Overzicht van de [typen in de gegevensset die u met Power BI gebruiken kunt](service-get-data.md).

In het onderstaande voorbeeld heb ik de app-werkruimte 'Verkoop en marketing' geselecteerd en op het tabblad **Gegevenssets** geklikt.

![Gegevenssets worden geselecteerd](media/service-basic-concepts/power-bi-datasets.png)

**Eén** dataset

* kan herhaaldelijk worden gebruikt in een of in veel werkruimten.
* kan worden in tal van verschillende rapporten.
* De visualisatie uit die ene gegevensset kunnen worden weergegeven op een groot aantal verschillende dashboards.

  ![Diagram met gegevensset](media/service-basic-concepts/drawing2.png)

Als u [verbinding met een gegevensset wilt maken of een gegevensset wilt importeren](service-get-data.md), selecteert u **Gegevens ophalen** onderaan het linkernavigatiegedeelte. Volg de instructies om verbinding te maken met de specifieke bron of om deze te importeren en de gegevensset aan de actieve werkruimte toe te voegen. Nieuwe gegevenssets zijn gemarkeerd met een geel sterretje. Uw werkzaamheden in Power BI zijn niet van invloed op de onderliggende gegevensset. Deze blijft ongewijzigd.

Gegevenssets die worden toegevoegd door een lid van de werkruimte zijn beschikbaar voor de andere leden van de werkruimte met een *admin*, *lid*, of *Inzender* rol.

U kunt gegevenssets vernieuwen, een andere naam geven, verkennen en verwijderen. U kunt een gegevensset gebruiken om een nieuw rapport maken of door [snelle inzichten](service-insights.md) uit te voeren.  Als u wilt zien welke rapporten en dashboards al een gegevensset gebruiken, selecteert u **Verwante items weergeven**. Selecteer een gegevensset om deze te verkennen In werkelijkheid opent de gegevensset in de rapporteditor, waar u de gegevens echt kunt doorspitten en visualisaties kunt maken. Laten we doorgaan met het volgende onderwerp: rapporten.

### <a name="dig-deeper"></a>Dieper graven
* [Wat is Power BI Premium?](service-premium-what-is.md)
* [Gegevens ophalen voor Power BI](service-get-data.md)
* [Voorbeeldgegevenssets voor Power BI](sample-datasets.md)

## <a name="reports"></a>Rapporten
Een Power BI-rapport bestaat uit een of meer pagina’s met visualisaties zoals lijndiagrammen, toewijzingen en treemaps. Visualisaties worden ook wel **_visuals_** genoemd. Alle visualisaties in een rapport zijn afkomstig uit één gegevensset. U kunt rapporten maken in Power BI maken, deze importeren met dashboards die collega's met u delen, of Power BI kunt ze maken wanneer u verbinding met gegevenssets in Excel, Power BI Desktop, databases en SaaS-toepassingen maken.  Als u bijvoorbeeld verbinding maakt met een Excel-werkmap die Power View-werkbladen bevat, wordt er een rapport in Power BI gemaakt op basis van die werkbladen. En als u verbinding met een SaaS-toepassing maakt, wordt er een vooraf samengestelde rapport in Power BI geïmporteerd.

Er zijn twee modi om rapporten weer te geven en om met rapporten te werken: *Leesweergave* en *Bewerkweergave*. Als u een rapport opent, wordt deze geopend in de leesweergave. Als u over bewerkingsmachtigingen beschikt, wordt er **rapport bewerken** in de linkerbovenhoek en u kunt het rapport weergeven in de bewerkingsweergave.  Als een rapport in een werkruimte iedereen met is een *admin*, *lid*, of *Inzender* rol kunt bewerken. Ze hebben toegang tot alle Verken, het ontwerpen, bouwen en het delen van de mogelijkheden van bewerken voor dat rapport weergeven. Het rapport wordt gedeeld met mensen kunt verkennen en gebruiken in het rapport in de leesweergave.   

Wanneer u een werkruimte opent, worden de bijbehorende rapporten vermeld op het tabblad **Rapporten**. Elk rapport dat wordt vermeld, vertegenwoordigt een of meer pagina's met visualisaties die zijn gebaseerd op een van de onderliggende gegevenssets. Selecteer een rapport om dit te openen.

Wanneer u een app opent, krijgt u een dashboard.  Voor toegang tot een onderliggend rapport selecteert u een dashboardtegel (later meer over tegels) die vanuit een rapport is vastgemaakt. Houd er rekening mee dat niet alle tegels vanuit rapporten zijn vastgemaakt. Mogelijk moet u dus op een aantal tegels klikken om een rapport te vinden.

Het rapport wordt standaard geopend in de leesweergave.  Selecteer **Rapport bewerken** om het rapport te openen in bewerkweergave (als u over de benodigde machtigingen beschikt).

In het onderstaande voorbeeld ik de 'Verkoop en marketing' app-werkruimte hebt geselecteerd en op het tabblad voor geklikt **rapporten**.

![Rapporten geselecteerd](media/service-basic-concepts/power-bi-reports.png)

**Eén** rapport

* is opgenomen in één werkruimte.
* kan worden gekoppeld aan meerdere dashboards in die werkruimte. Tegels vastgemaakt vanuit dat rapport kan worden weergegeven in meerdere dashboards.
* kan worden gemaakt van gegevens uit één gegevensset. Power BI Desktop meer dan één gegevensbron in een enkele gegevensset in een rapport kan combineren en dat rapport kan worden geïmporteerd in Power BI.

  ![Diagram met rapporten](media/service-basic-concepts/drawing3new.png)

### <a name="dig-deeper"></a>Dieper graven
- [Een rapport maken in Power BI-service door een gegevensset te importeren](service-report-create-new.md)
- [Rapporten voor de mobiele Power BI-apps te optimaliseren](desktop-create-phone-report.md)

## <a name="dashboards"></a>Dashboards
Een *dashboard* is een element dat u maakt **in de Power BI-service** of dat een collega maakt **in de Power BI-service** en met u deelt. Het dashboard bestaat uit één canvas dat nul of meer tegels en widgets bevat. Elke tegel die vanuit een rapport of vanuit [Q&A](power-bi-q-and-a.md) is vastgemaakt, geeft één [visualisatie](power-bi-report-visualizations.md) weer die is gemaakt van een gegevensset en die is vastgemaakt aan het dashboard. Volledige rapportpagina's kunnen ook als één tegel worden vastgemaakt aan een dashboard. Er zijn tal van manieren om tegels aan uw dashboard toe te voegen. Teveel om in dit overzichtsonderwerp te bespreken. Zie [Dashboardtegels in Power BI](service-dashboard-tiles.md) voor meer informatie.

Waarom zou ik dashboards willen maken?  Hier volgen slechts enkele van de redenen:

* U kunt in één oogopslag alle benodigde informatie weergeven om een beslissing te nemen.
* U kunt de belangrijkste informatie over uw bedrijf bewaken.
* U kunt er met dashboards voor zorgen dat alle collega's hetzelfde voor ogen hebben en allemaal dezelfde informatie zien en gebruiken.
* U kunt met dashboards de status van een bedrijf, product, afdelingen of marketingcampagne, enzovoort in de gaten houden.
* U kunt een gepersonaliseerde weergave van een groter dashboard maken met alle metrische gegevens die voor u belangrijk zijn.

Wanneer u een werkruimte opent, worden de bijbehorende dashboards vermeld op het tabblad **Dashboards**. Selecteer een dashboard om het te openen. Wanneer u een app opent, krijgt u een dashboard te zien.  Elk dashboard vertegenwoordigt een aangepaste weergave of een subset van de onderliggende gegevensset(s).  Als u de eigenaar van het dashboard bent, hebt u ook bewerktoegang tot de onderliggende gegevensset(s) en rapporten.  Als het dashboard met u is gedeeld, kunt u interactief met het dashboard en eventuele onderliggende rapporten werken, maar u kunt geen wijzigingen opslaan.

Er zijn veel verschillende manieren waarop u of een collega [een dashboard kan delen](service-share-dashboards.md). U hebt Power BI Pro nodig om dashboard te kunnen delen, maar mogelijk ook om een gedeeld dashboard weer te geven.

**Eén** dashboard

* is gekoppeld aan één werkruimte
* kan visualisaties weergeven uit diverse gegevenssets,
* uit verschillende rapporten en
* kan visualisaties weergeven die zijn vastgemaakt vanuit andere hulpprogramma's (bijvoorbeeld Excel)

  ![Dashboard geselecteerd](media/service-basic-concepts/drawing1.png)

### <a name="dig-deeper"></a>Dieper graven
* [Een leeg dashboard maken en vervolgens enkele gegevens](service-dashboard-create.md) .
* [Een dashboard dupliceren](service-dashboard-copy.md)
* [Een telefoonweergave van een dashboard maken](service-create-dashboard-mobile-phone-view.md)


## <a name="workbooks"></a>Werkmappen
Werkmappen zijn een speciaal type gegevensset. Als u het bovenstaande gedeelte over **gegevenssets** hebt gelezen, weet u vrijwel alles wat u over werkmappen moet weten. Maar u vraagt zich misschien af waarom Power BI een Excel-werkmap in sommige gevallen als een **gegevensset** en op andere momenten als een **werkmap** classificeert.

Als u de optie **Gegevens ophalen** gebruikt met Excel-bestanden, hebt u de mogelijkheid om het bestand te *Importeren* of om *verbinding te maken* met het bestand. Wanneer u de optie Verbinden kiest, wordt uw werkmap weergegeven in Power BI, precies zoals in Excel Online. Maar anders dan in Excel Online hebt u een aantal handige functies waarmee u elementen uit uw werkbladen direct aan uw dashboards kunt vastmaken.

U kunt uw werkmap niet in Power BI bewerken. Maar als u wijzigingen wilt aanbrengen, kunt u op Bewerken klikken en uw werkmap vervolgens bewerken in Excel Online of openen in Excel op uw computer. Eventuele wijzigingen worden opgeslagen in de werkmap op OneDrive.

### <a name="dig-deeper"></a>Dieper graven
* [Gegevens ophalen uit Excel-werkmappen](service-excel-workbook-files.md)
* [Vanuit Excel publiceren naar Power BI](service-publish-from-excel.md)


## <a name="a-dashboard-in-my-workspace"></a>Een dashboard in Mijn werkruimte
We hebben werkruimten en bouwstenen besproken. Laten we nu alle onderdelen van de dashboardervaring in de Power BI-service combineren en controleren.

![Power BI-service in een browser](media/service-basic-concepts/completenewest.png)

### <a name="1-navigation-pane-left-nav"></a>1. **Navigatiedeelvenster** (linkernavigatie)
Gebruik het navigatiedeelvenster om werkruimten te zoeken en tussen werkruimten en de Power BI-bouwblokken te schakelen: dashboards, rapporten, werkboeken en gegevenssets.  

  ![Navigatiedeelvenster](media/service-basic-concepts/power-bi-navigation.png)

* Selecteer **Gegevens ophalen** om [gegevenssets, rapporten en dashboards toe te voegen aan Power BI](service-get-data.md).
* Gebruik dit pictogram om het navigatiedeelvenster uit en samen te vouwen ![pictogram navigatiedeelvenster](media/service-basic-concepts/expand-icon.png).
* Open of beheer uw favoriete inhoud door **Favorieten** te selecteren.
* Bekijk en open de laatst bezochte inhoud door **Recent** te selecteren.
* Bekijk, open of verwijder een app door **Apps** te selecteren.
* Heeft een collega inhoud met u gedeeld? Selecteer **Gedeeld met mij** om die inhoud te zoeken en te sorteren om te vinden wat u nodig hebt.
* Toon en open uw werkruimten door **Werkruimten** te selecteren.

Klik éénmaal op deze elementen:

* op een pictogram of kop om in de inhoudsweergave te openen
* op een pijl naar rechts (>) om een uitvouwmenu te openen voor Favorieten, Recent en Werkruimten.
* op een dubbele punthaak om de doorbladerbare lijst **Mijn werkruimte** met dashboards, rapporten, werkboeken en gegevenssets weer te geven.

### <a name="2-canvas"></a>2. **Canvas**
Omdat we een dashboard hebben geopend, worden in het tekengebied visualisatietegels weergegeven. Als we bijvoorbeeld de rapporteditor hadden geopend, zou in het tekengebied een rapportpagina worden weergegeven.

Dashboards bestaan uit [tegels](service-dashboard-tiles.md).  Tegels worden gemaakt in een rapport in de bewerkweergave, in Q&A of in andere dashboards en kunnen worden vastgemaakt vanuit Excel, SSRS en meer. Een speciaal type tegel, een [widget](service-dashboard-add-widget.md), wordt rechtstreeks aan het dashboard toegevoegd. De tegels die worden weergegeven op een dashboard, daar bewust neergezet door een maker of eigenaar van een rapport.  De bewerking waarmee een tegel wordt toegevoegd aan een dashboard, noemen we *vastmaken*.

![Power BI-dashboardcanvas](media/service-basic-concepts/canvas.png)

Zie [Dashboards](#dashboards) (hierboven) voor meer informatie.

### <a name="3-qa-question-box"></a>3. **Q&A-vragenvak**
U kunt uw gegevens onder andere verkennen door vragen te stellen die door Power BI Q&A worden beantwoord de vorm van een visualisatie. Met Q&A kunt u inhoud aan een dashboard of rapport toevoegen.

U zoekt met Q&A naar antwoorden in een of meer gegevenssets die zijn verbonden met het dashboard.  Een verbonden gegevensset is een gegevensset waarvoor ten minste één tegel is vastgemaakt aan het desbetreffende dashboard.

![Q&A-vragenvak](media/service-basic-concepts/power-bi-qna.png)

Zodra u een vraag begint te typen, wordt u door Q&A omgeleid naar Q&A-pagina. Terwijl u typt, helpt Q&A u de juiste vraag te stellen en het antwoord te zoeken met herformuleringen, automatisch doorvoeren en suggesties. Wanneer u een gewenste visualisatie (antwoord) hebt gevonden, kunt u deze vastmaken aan uw dashboard. Zie [Q&A in Power BI](power-bi-q-and-a.md) voor meer informatie.

### <a name="4-icon-buttons"></a>4. **Pictogramknoppen**
De pictogrammen in de rechterbovenhoek zijn uw resources voor instellingen, meldingen, downloads, hulp en feedback aan het Power BI-team. Selecteer de dubbele pijl om het dashboard te open in een **volledig scherm**.  

![pictogramknoppen](media/service-basic-concepts/power-bi-icons.png)

### <a name="5-dashboard-title-navigation-path-or-breadcrumbs"></a>5. **De titel van dashboard** (navigatiepad, of ' breadcrumbs ')
Het is niet altijd gemakkelijk te achterhalen welke werkruimte en welk dashboard actief zijn, dus Power BI maakt een navigatiepad voor u.  In dit voorbeeld ziet u de werkruimte (Mijn werkruimte) en de titel van het dashboard (Voorbeeld van een retailanalyse).  Als we een rapport hebben geopend, wordt de naam van het rapport aan het einde van het navigatiepad toegevoegd.  Elke sectie van het pad is een actieve hyperlink.  

Let op het pictogram 'C' na de titel van het dashboard. Dit dashboard bevat de [gegevensclassificatietag](service-data-classification.md) ‘Vertrouwelijk’. De tag identificeert de gevoeligheid en het beveiligingsniveau van de gegevens. Als uw beheerder gegevensclassificatie heeft ingeschakeld, beschikt elk dashboard over een standaardtagset. Dashboardeigenaren moeten de tag wijzigen zodat deze overeenkomt met het goede beveiligingsniveau van hun dashboard.

![Pictogram gegevensclassificatie](media/service-basic-concepts/power-bi-title.png)

### <a name="6-office-365-app-launcher"></a>6. **Startprogramma voor de Office 365-app**
Met het startprogramma voor apps zijn al uw Office 365-apps met één klik beschikbaar. Hier kunt u snel uw e-mail, documenten, agenda enzovoort openen.

![Startprogramma voor Office-apps](media/service-basic-concepts/power-bi-waffle.png)

### <a name="7-power-bi-home"></a>7. **Power BI-startknop**
Als u **Power BI** selecteert, keert u terug naar de Power BI-startpagina.

   ![Power BI in de service](media/service-basic-concepts/version-new.png)

### <a name="8-labeled-icon-buttons"></a>8. **Gelabelde pictogramknoppen**
Dit gedeelte van het scherm bevat aanvullende opties voor interactie met de inhoud (in dit geval met het dashboard).  Als u het beletselteken naast de gelabelde pictogrammen die u ziet selecteert, worden er onder andere opties weergegeven waarmee u het dashboard kunt dupliceren, afdrukken en vernieuwen.

   ![Gelabelde pictogramknoppen](media/service-basic-concepts/power-bi-labeled-icons.png)

## <a name="next-steps"></a>Volgende stappen
- [Wat is Power BI?](power-bi-overview.md)  
- [Power BI-video's](videos.md)  
- [De rapporteditor... Een rondleiding](service-the-report-editor-take-a-tour.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
