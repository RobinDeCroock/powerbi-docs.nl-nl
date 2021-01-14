---
title: Een Q&A-visual maken in Power BI
description: Een Q&A-visual voor Power BI maken en opmaken in Power BI Desktop of de Power BI-service.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: rien
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 01/05/2021
ms.openlocfilehash: 1cf80593458c12a1bee07ed40202e3613fdcb5e9
ms.sourcegitcommit: c700e78dfedc34f5a74b23bbefdaef77e2a87f8a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/07/2021
ms.locfileid: "97961357"
---
# <a name="create-a-qa-visual-in-power-bi"></a>Een Q&A-visual maken in Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

Met de Q&A-visual kunnen gebruikers vragen in een natuurlijke taal stellen en antwoorden krijgen in de vorm van een visual. *Consumenten* kunnen deze gebruiken om snel antwoord te krijgen op hun gegevens. *Ontwerpers* kunnen dit ook gebruiken om snel visuals te maken. Als u een rapportontwerper bent, is dit artikel voor u. U kunt ergens in een rapport dubbelklikken en natuurlijke taal gebruiken om aan de slag te gaan. In dit artikel maakt u een Q&A-visual, past u de opmaak aan en past u deze aan. Deze biedt ook ondersteuning voor thema's en andere standaardindelingsopties die in Power BI beschikbaar zijn. Nadat u deze hebt gemaakt, gedraagt deze zich als een andere visual, die ondersteuning biedt voor kruislings filteren, kruismarkeringen en bladwijzers. 

Zoekt u meer achtergrondinformatie over Q&A in Power BI? Bekijk [Inleiding tot Q&A](../natural-language/q-and-a-intro.md). 

![Stapsgewijze instructies voor Q&A-visuals](../natural-language/media/qna-visual-walkthrough.gif)

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

De Q&A-visual bestaat uit vier kernonderdelen:

- Het vragenvak. Hier voeren gebruikers hun vraag in en zien ze suggesties om hun vraag aan te vullen.
- Een vooraf ingevulde lijst met voorgestelde vragen.
- Pictogram voor het omzetten van de Q&A-visual in een standaardvisual. 
- Pictogram voor het openen van het Q&A-hulpprogramma, waarmee ontwerpers de onderliggende engine voor natuurlijke taal kunnen configureren.

## <a name="prerequisites"></a>Vereisten

1. Download het [PBIX-bestand met een voorbeeld van verkoop en marketing](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix) om door te gaan.

1. Selecteer linksboven in Power BI Desktop **Bestand** > **Openen**.
   
2. Zoek uw kopie van het **PBIX-bestand met een voorbeeld van verkoop en marketing**.

1. Open het bestand in de rapportweergave ![Schermopname van het pictogram Rapportweergave.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Het plusteken selecteren ![Schermopname van het gele tabblad.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) om een nieuwe pagina toe te voegen.

Als u een fout ziet wanneer u een Q&A-visual maakt, controleert u het artikel [Q&A-beperkingen](../natural-language/q-and-a-limitations.md) om te zien of de configuratie van de gegevensbron wordt ondersteund.    

> [!NOTE]
> Voor het delen van uw rapport met een Power BI-collega moet u beiden beschikken over een afzonderlijke Power BI Pro-licentie of moet het rapport zijn opgeslagen in een werkruimte met Premium-capaciteit. Zie [Rapporten delen](../collaborate-share/service-share-dashboards.md) voor meer informatie.

## <a name="create-a-qa-visual-using-a-suggested-question"></a>Een Q&A-visual maken met behulp van een voorgestelde vraag
In deze oefening selecteren we een van de voorgestelde vragen om onze Q&A-visual te maken. 

1. Begin op een lege rapportpagina en selecteer het pictogram van de Q&A-visual in het deelvenster Visualisaties.

    ![Het deelvenster Visualisaties, waarin het Q&A-visual-pictogram is gemarkeerd](media/power-bi-visualization-q-and-a/power-bi-icon.png)

2. Sleep de rand om de grootte van de visual te wijzigen.

    ![Q&A-visual op rapportcanvas](media/power-bi-visualization-q-and-a/power-bi-qna.png)

3. Voor het maken van de visual selecteert u een van de voorgestelde vragen of begint u met typen in het vraagvak. In dit voorbeeld hebben we **de belangrijkste geografische staten op totale omzet** geselecteerd. Power BI kiest zelf het beste type visualtype dat moet worden gebruikt. In dit geval is het een kaart.

    ![Kaart in Q&A-visual](media/power-bi-visualization-q-and-a/power-bi-map.png)

    Maar u kunt Power BI vertellen welk visualtype moet worden gebruikt door deze toe te voegen aan uw query in natuurlijke taal. Onthoud dat niet alle visualtypen goed werken of logisch zijn met betrekking tot uw gegevens. Deze gegevens leveren bijvoorbeeld geen nuttig spreidingsdiagram op. Maar het werkt wel als een choropletenkaart.

    ![Q&A-visual als een choropletenkaart](media/power-bi-visualization-q-and-a/power-bi-specify-map.png)

## <a name="create-a-qa-visual-using-a-natural-language-query"></a>Een Q&A-visual maken met behulp van een query in natuurlijke taal
In het bovenstaande voorbeeld hebben we een van de voorgestelde vragen geselecteerd om onze Q&A-visual te maken.  In deze oefening typen we onze eigen vraag. Wanneer we onze vraag invoeren, helpt Power BI ons met automatisch aanvullen, suggesties en feedback.

Als u niet zeker weet welk type vragen u wilt stellen of welke terminologie moet worden gebruikt, vouwt u **Alle suggesties weergeven** open of kijkt u in het deelvenster Velden, rechts naast het canvas. U kunt met het deelvenster Velden bekend raken met de termen en de inhoud van de gegevensset Verkoop en marketing.

![Canvas met Alle suggesties weergeven en het deelvenster Velden](media/power-bi-visualization-q-and-a/power-bi-terminology.png)


1. Typ een vraag in het Q&A-veld. Power BI voegt een rode onderstreping toe aan woorden die niet worden herkend. Waar mogelijk helpt Power BI u niet-herkende woorden te definiëren.  In het onderstaande eerste voorbeeld werkt het voor ons prima door een van de suggesties te selecteren.  

    ![Een vraag typen in het Q&A-vragenvak](media/power-bi-visualization-q-and-a/power-bi-red-suggest.png)

2. Naarmate we meer van de vraag typen, laat Power BI ons weten dat het de vraag niet begrijpt en probeert het programma ons te helpen. In het onderstaande voorbeeld vraagt Power BI ons: "Bedoelt u..." en krijgen we een suggestie om onze vraag anders te stellen, met behulp van terminologie uit onze gegevensset. 

    ![Q&A-visual met suggesties](media/power-bi-visualization-q-and-a/power-bi-define.png)

5. Met de hulp van Power BI kunnen we een vraag stellen met alle herkenbare termen. In Power BI worden de resultaten als een lijndiagram weergegeven. 

    ![Visuele resultaten van Q&A](media/power-bi-visualization-q-and-a/power-bi-type.png)


6. Laten we de visual nu wijzigen in een kolomdiagram. 

    ![Q&A-visual waarbij 'als kolomdiagram' aan de vraag is toegevoegd](media/power-bi-visualization-q-and-a/power-bi-specify-visual.png)

7.  Voeg meer visuals toe aan de rapportpagina en bekijk hoe de Q&A-visual samenwerkt met de andere visuals op de pagina. In dit voorbeeld heeft de Q&A-visual het lijndiagram en de kaart kruislings gefilterd en het staafdiagram kruislings gemarkeerd.

    ![Q&A-visual met één balk geselecteerd en de invloed op de andere drie visuals op de rapportpagina](media/power-bi-visualization-q-and-a/power-bi-filters.png)

## <a name="format-and-customize-the-qa-visual"></a>De Q&A-visual opmaken en aanpassen
De Q&A-visual kan worden aangepast met behulp van het deelvenster Opmaak en door een thema toe te passen. 

### <a name="apply-a-theme"></a>Een thema toepassen
Wanneer u een thema selecteert, wordt dat thema toegepast op de gehele rapportpagina. U kunt uit talloze thema's kiezen, dus probeer ze gerust tot u de gewenste vormgeving hebt. 

1. Selecteer het tabblad **Start** op de menubalk en kies **Thema wisselen**. 

    ![Bureaublad waarop Thema wisselen is geselecteerd](media/power-bi-visualization-q-and-a/power-bi-themes.png)

    
    
2. In dit voorbeeld hebben we **Meer thema's** > **Geschikt voor kleurenblinden** geselecteerd.

    ![Q&A-visual waarop het speciale thema voor kleurenblinden is toegepast](media/power-bi-visualization-q-and-a/power-bi-color-blind.png)

### <a name="format-the-qa-visual"></a>De Q&A-visual opmaken
Configureer de opmaak van de Q&A-visual, het vraagveld en de manier waarop suggesties worden weergegeven. U kunt alles wijzigen, van de achtergrond van een titel tot de kleur van de cursor waarmee over niet-herkende woorden wordt bewogen. Hier hebben we een grijze achtergrond aan het vraagvak toegevoegd en de onderstreping gewijzigd in geel en groen. De titel is gecentreerd en heeft een gele achtergrond. 

![Q&A-visual met onze opmaakresultaten](media/power-bi-visualization-q-and-a/power-bi-q-and-a-format.png)

## <a name="convert-your-qa-visual-into-a-standard-visual"></a>Uw Q&A-visual omzetten naar een standaardvisual
We hebben de opmaak van onze visual met kolomdiagram en de optie Geschikt voor kleurenblinden enigszins aangepast: We hebben een titel en een rand toegevoegd. We kunnen de visual nu omzetten naar een standaardvisual in ons rapport en de visual bovendien vastmaken aan een dashboard.

Selecteer het ![tandwielpictogram](media/power-bi-visualization-q-and-a/power-bi-convert-icon.png) om de optie **Dit Q&A-resultaat omzetten in een standaardvisual** uit te voeren.

![Q&A-visual met pijl richting het pictogram Standaardvisual](media/power-bi-visualization-q-and-a/power-bi-visual-convert.png)

Deze visual is niet langer een Q&A-visual maar een standaardkolomdiagram. Deze visual kan worden vastgemaakt aan een dashboard. In het rapport gedraagt deze visual zich op dezelfde manier als andere standaardvisuals. U ziet dat in het deelvenster Visualisaties een kolomdiagrampictogram is geselecteerd in plaats van het Q&A-visualpictogram.

Als u de **_Power BI-service_* _ gebruikt, kunt u de visual nu vastmaken aan een dashboard door het pictogram Vastmaken te selecteren. 


![De Power BI-service met daarin het pictogram Vastmaken](media/power-bi-visualization-q-and-a/power-bi-pin.png)


## <a name="advanced-features-of-the-qa-visual"></a>Geavanceerde functies van de Q&A-visual
Door het tandwielpictogram te selecteren, opent u het deelvenster Hulpprogramma's van de Q&A-visual. 

![Q&A-visual waarbij het pictogram Hulpprogramma's is geselecteerd](media/power-bi-visualization-q-and-a/power-bi-q-and-a-tooling.png)

Gebruik het deelvenster Hulpprogramma's om Q&A-termen te trainen die niet worden herkend, die termen te beheren en de voorgestelde vragen voor deze gegevensset en dit rapport te beheren. In het deelvenster Hulpprogramma's kunt u ook vragen controleren die gebruikers hebben gesteld in deze Q&A-visual en vragen zien die door gebruikers zijn gemarkeerd. Zie [Inleiding tot Q&A-hulpprogramma's om Power BI Q&A te trainen](../natural-language/q-and-a-tooling-intro.md) voor meer informatie.

![Het deelvenster Q&A-hulpprogramma's](media/power-bi-visualization-q-and-a/power-bi-q-and-a-tooling-pane.png)

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing
De Q&A-visual kan worden geïntegreerd met Office en Bing om niet-herkende gangbare woorden te vergelijken met velden in uw gegevensset.  

## <a name="next-steps"></a>Volgende stappen

U kunt natuurlijke taal op verschillende manieren integreren. Raadpleeg voor meer informatie de volgende artikelen:

_ [Q&A-hulpprogramma's](../natural-language/q-and-a-tooling-intro.md)
* [Best practices voor Q&A](../natural-language/q-and-a-best-practices.md)
