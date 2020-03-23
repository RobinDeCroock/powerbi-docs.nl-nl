---
title: Knoppen gebruiken in Power BI
description: U kunt knoppen toevoegen aan Power BI-rapporten waarmee uw rapporten zich als apps gedragen en zo de betrokkenheid bij gebruikers verdiepen.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 6629165ec031fea0d1c1af443e1d7b311bc743aa
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79201597"
---
# <a name="use-buttons-in-power-bi"></a>Knoppen gebruiken in Power BI
Met behulp van **knoppen** in Power BI kunt u rapporten maken die zich als apps gedragen en daarmee voor een aantrekkelijke omgeving zorgen, zodat gebruikers met de muisaanwijzer over Power BI-inhoud kunnen bewegen, erop kunnen klikken en op andere manieren met deze inhoud kunnen communiceren. U kunt knoppen toevoegen aan rapporten in **Power BI Desktop** en in **Power BI-service**. Wanneer u uw rapporten in de Power BI-service deelt, bieden ze uw gebruikers een app-achtige ervaring.

![Knoppen in Power BI](media/desktop-buttons/power-bi-buttons.png)

## <a name="create-buttons-in-reports"></a>Knoppen maken in rapporten

### <a name="create-a-button-in-power-bi-desktop"></a>Een knop maken in Power BI Desktop

Als u een knop in **Power BI Desktop** wilt maken, selecteert u **Knoppen** op het lint **Invoegen**, waarna een vervolgkeuzelijst wordt weergegeven, waarin u de gewenste knop kunt selecteren uit een verzameling opties, zoals wordt weergegeven in de volgende afbeelding. 

![Een besturingsknop toevoegen in Power BI Desktop](media/desktop-buttons/power-bi-button-dropdown.png)

### <a name="create-a-button-in-the-power-bi-service"></a>Een knop maken in de Power BI-service

Als u een knop wilt maken in de **Power BI-service**, opent u het rapport in de Bewerkweergave. Selecteer **Knoppen** in de menubalk bovenaan en er wordt een vervolgkeuzelijst weergegeven. Hierin kunt u de gewenste knop selecteren uit een verzameling opties, zoals wordt weergegeven in de volgende afbeelding. 

![Een besturingsknop toevoegen in de Power BI-service](media/desktop-buttons/power-bi-button-service-dropdown.png)

## <a name="customize-a-button"></a>Een knop aanpassen

Of u de knop nu maakt in Power BI Desktop of de Power BI-service, de rest van het proces is hetzelfde. Wanneer u de knop selecteert op het rapportcanvas, toont het deelvenster **Visualisaties** u de vele manieren waarop u de knop aan uw behoeften kunt aanpassen. U kunt bijvoorbeeld de **knoptekst** in- of uitschakelen, door de schuifregelaar in deze kaart van het deelvenster **Visualisaties** om te schakelen. U kunt ook het pictogram van de knop, de opvulling van de knop, de titel en de actie wijzigen die moet worden uitgevoerd wanneer gebruikers de knop selecteren in een rapport of ander functies uitvoeren.

![Een knop opmaken in een Power BI-rapport](media/desktop-buttons/power-bi-button-properties.png)

## <a name="set-button-properties-when-idle-hovered-over-or-selected"></a>Knopeigenschappen instellen wanneer deze inactief is, een muisaanwijzer erover wordt bewogen of wanneer deze wordt geselecteerd

Knoppen in Power BI beschikken over drie statussen: standaard (zoals ze worden weergegeven wanneer u niet de muisaanwijzer erover beweegt of deze selecteert), wanneer u de muisaanwijzer erover beweegt, of wanneer u deze selecteert (vaak aangeduid met *erop geklikt*). Vele kaarten in het deelvenster **Visualisaties** kunnen afzonderlijk worden gewijzigd op basis van deze drie statussen, wat voor een grote mate van flexibiliteit zorgt om de knoppen aan te passen.

Bij de volgende kaarten in het deelvenster **Visualisaties** kunt u de opmaak of het gedrag van een knop aanpassen op basis van de drie statussen:

* Knoptekst
* Pictogram
* Omtrek
* Opvullen

Als u wilt selecteren hoe de knop moet worden weergegeven voor elke status, vouwt u een van deze kaarten open en selecteert u de vervolgkeuzelijst die wordt weergegeven aan de bovenkant van de kaart. In de volgende afbeelding ziet u de kaart **Pictogram** uitgevouwen met de vervolgkeuzelijst die is geselecteerd om de drie statussen te tonen.

![Drie statussen van een knop in een Power BI-rapport](media/desktop-buttons/power-bi-button-format.png)


## <a name="select-the-action-for-a-button"></a>De actie voor een knop selecteren

U kunt selecteren welke actie wordt uitgevoerd wanneer een gebruiker een knop in Power BI selecteert. U kunt de opties voor knopacties van de kaart **Actie** openen in het deelvenster **Visualisaties**.

![Actie voor een knop in Power BI](media/desktop-buttons/power-bi-button-action.png)

Dit zijn de opties voor knopacties:

- Met **Terug** keert de gebruiker terug naar de vorige pagina van het rapport. Dit is handig voor analysepagina's.
- Met **Bladwijzer** wordt de rapportpagina weergegeven die aan een bladwijzer is gekoppeld die is gedefinieerd voor het huidige rapport. Meer informatie over [bladwijzers in Power BI](desktop-bookmarks.md). 
- Met **Analyseren (preview)** navigeert de gebruiker naar een analysepagina die is gefilterd op zijn selectie, zonder gebruik van bladwijzers. Meer informatie over [analyseknoppen in rapporten](desktop-drill-through-buttons.md).
- Met **paginanavigatie** navigeert de gebruiker naar een andere pagina in het rapport, ook zonder bladwijzers te gebruiken. Zie [Paginanavigatie maken](#create-page-navigation) in dit artikel voor meer informatie.
- Met **Q&A** opent u een **Q&A Explorer**-venster. 

Bepaalde knoppen hebben een standaardactie die automatisch wordt geselecteerd. Bijvoorbeeld bij een knop van het type **Q & A** wordt automatisch **Q & A** als standaardactie geselecteerd. U kunt meer lezen over **Q & A Explorer** door [dit blogbericht](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer) te lezen.

U kunt de knoppen uitproberen of testen die u voor uw rapport hebt gemaakt door *CTRL + klik* in te toetsen op de knop die u wilt gebruiken. 

### <a name="create-page-navigation"></a>Paginanavigatie maken

Met het **Actie**-type **Paginanavigatie** kunt u snel een volledige navigatie-ervaring bouwen zonder dat u bladwijzers hoeft op te slaan of te beheren.

Als u een paginanavigatieknop wilt instellen, maakt u een knop met **Paginanavigatie** als actietype en selecteert u de pagina **Doel**.

![Actie paginanavigatie](media/desktop-buttons/power-bi-page-navigation.png)

U kunt snel een aangepast navigatiedeelvenster maken. U hoeft geen bladwijzers te bewerken en te beheren als u wilt wijzigen welke pagina's in het navigatiedeelvenster worden weergegeven.

![Een navigatiepagina maken](media/desktop-buttons/power-bi-build-navigation-pane.png)

Daarnaast kunt u de knopinfo voorwaardelijk opmaken zoals u ook kunt doen met andere knoptypen.

## <a name="next-steps"></a>Volgende stappen
Raadpleeg de volgende artikelen voor meer informatie over functies die vergelijkbaar zijn of samenwerken met knoppen:

* [Analyseren gebruiken in Power BI-rapporten](desktop-drillthrough.md)
* [Bladwijzers gebruiken om inzichten te delen en verhalen te vertellen in Power BI](desktop-bookmarks.md)

