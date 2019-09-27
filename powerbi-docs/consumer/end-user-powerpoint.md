---
title: Rapporten exporteren van Power BI naar PowerPoint
description: Leer hoe u een Power BI-rapport naar PowerPoint kunt exporteren.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/18/2019
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: 9a798afead16174f66fadba87c795d5377747e93
ms.sourcegitcommit: 200291eac5769549ba5c47ef3951e2f3d094426e
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71141399"
---
# <a name="export-reports-from-power-bi-to-powerpoint"></a>Rapporten exporteren van Power BI naar PowerPoint
Met Power BI kunt u uw rapport publiceren naar **Microsoft PowerPoint** en heel eenvoudig een presentatie op basis van uw Power BI-rapport maken. Wanneer u wilt **exporteren naar PowerPoint** gebeurt het volgende:

* Elke pagina in het Power BI-rapport wordt een afzonderlijke dia in PowerPoint
* Elke pagina in het Power BI-rapport wordt geëxporteerd als een enkele afbeelding met een hoge resolutie in PowerPoint
<!-- * The filters and slicers settings that you added to the report are preserved. -->
* In PowerPoint wordt een koppeling gemaakt die verwijst naar het Power BI-rapport 

Het ophalen van uw **Power BI-rapport** dat is geëxporteerd naar **PowerPoint** gaat snel. Volg de stappen in de volgende sectie.

## <a name="how-to-export-your-power-bi-report-to-powerpoint"></a>Uw Power BI-rapport naar PowerPoint exporteren
Selecteer in de Power BI-service een rapport om weer te geven op het canvas. U kunt ook een rapport selecteren via de pagina **Start**, **Apps** of een andere container in de linkernavigatiebalk.

Wanneer het rapport dat u wilt exporteren naar PowerPoint wordt weergegeven op het canvas, selecteert u **Exporteren > PowerPoint** in de menubalk.

![Selecteer Exporteren in de menubalk](media/end-user-powerpoint/power-bi-export.png)

   
Er wordt een pop-upvenster weergegeven waar u de mogelijkheid hebt om de **huidige waarden** of de **standaardwaarden** te selecteren.  Met **Huidige waarden** exporteert u het rapport in de huidige staat, inclusief de actieve wijzigingen die u in de slicer- en filterwaarden hebt aangebracht.  De meeste gebruikers selecteren deze optie.  U kunt ook **Standaardweergave** selecteren, waarmee u het rapport in de oorspronkelijke staat exporteert (zoals de auteur dit heeft gedeeld), en waarin geen wijzigingen zijn doorgevoerd die u aan de oorspronkelijke staat hebt aangebracht.

![Selecteer wat u wilt exporteren](media/end-user-powerpoint/power-bi-current-values.png)
    
Daarnaast is er een selectievakje dat u kunt in-/uitschakelen voor het wel of niet exporteren van de verborgen tabbladen van een rapport.  U hoeft alleen dit selectievakje in te schakelen als u alleen tabbladen van een rapport wilt exporteren die zichtbaar zijn in uw browser.  Als u liever alle verborgen tabbladen mee wilt krijgen als onderdeel van de export, kunt u dit beter uitgeschakeld laten.  Als het selectievakje grijs wordt weergegeven, zijn er geen verborgen tabbladen in het rapport.  Nadat u de selecties hebt gemaakt, selecteert u **Exporteren** om door te gaan.

Hier ziet u een meldingsbanner in de rechterbovenhoek van het browservenster van de Power BI-service die aangeeft dat het rapport wordt geëxporteerd naar PowerPoint. Dit kan enkele minuten duren; u kunt tijdens het exporteren van het rapport in Power BI blijven werken.

![Melding Exporteren naar PowerPoint wordt uitgevoerd](media/end-user-powerpoint/power-bi-export-progress.png)

Wanneer u klaar bent, wijzigt de meldingsbanner zodat u weet dat de Power BI-service het exportproces heeft voltooid. Het bestand is beschikbaar wanneer de gedownloade bestanden worden weergegeven in uw browser. In de volgende afbeelding wordt dit weergegeven als een downloadbanner langs de onderkant van het browservenster.

![Pijl wijst naar browsermelding onderaan het scherm](media/end-user-powerpoint/powerbi_to_powerpoint_4.png)

Zo eenvoudig werkt dat. U kunt het bestand downloaden, openen met PowerPoint en vervolgens wijzigen of bewerken zoals u met elke andere PowerPoint-presentatie zou doen.

## <a name="checking-out-your-exported-powerpoint-file"></a>Het geëxporteerde PowerPoint-bestand bekijken
Bij het openen van het PowerPoint-bestand dat door Power BI is geëxporteerd, ziet u enkele coole en nuttige elementen. Bekijk de volgende afbeelding en vervolgens de genummerde elementen hieronder die deze coole functies beschrijven.

![PowerPoint wordt geopend](media/end-user-powerpoint/powerbi_to_powerpoint_5.png)

1. De eerste pagina van de presentatie bevat de naam van uw rapport en een koppeling zodat u het rapport waarop de presentatie is gebaseerd, kunt **Weergeven in Power BI**.
2. U krijgt zo ook handige informatie over het rapport, zoals de *laatste gegevensvernieuwing* waarop het geëxporteerde rapport is gebaseerd en de *gedownload op* -tijd en -datum. Dit is het tijdstip en de datum waarop het Power BI-rapport naar een PowerPoint-bestand is geëxporteerd.
3. Elke rapportpagina is een afzonderlijke dia, zoals wordt weergegeven in het navigatiedeelvenster links. 
4. Uw gepubliceerde rapport wordt gerenderd in de taal die is geselecteerd in uw instellingen voor Power BI. Anders wordt de taal bepaald door de landinstelling van uw browser. Als u uw voorkeurstaal wilt zien of instellen, selecteert u het tandwielpictogram ![tandwielpictogram](media/end-user-powerpoint/power-bi-settings-icon.png) **> Instellingen > Algemeen > Taal**. Raadpleeg [Ondersteunde talen en landen/regio's voor Power BI](../supported-languages-countries-regions.md) voor informatie over landinstellingen.
5. Op de titeldia van de PowerPoint-presentatie staat het tijdstip van de export in de juiste tijdzone.

Wanneer u naar een afzonderlijke dia gaat, zult u merken dat elke rapportpagina een onafhankelijke afbeelding is.

>[!NOTE]
> Het gebruik van één visual per rapportpagina is nieuw gedrag. Het vorige gedrag, waarbij voor elke visual een aparte afbeelding werd gebruikt, is niet meer geïmplementeerd. 
 

![Afbeelding waarin wordt laten zien dat elke visual een afzonderlijke afbeelding is](media/end-user-powerpoint/powerbi_to_powerpoint_6.png)

Wat u verder doet met uw PowerPoint-presentatie, of met de afbeeldingen met hoge resolutie, is geheel aan u!

## <a name="limitations"></a>Beperkingen
Er zijn enkele overwegingen en beperkingen waar u rekening mee moet houden bij het werken met de functie **Exporteren naar PowerPoint**.

* **R-visualisaties** worden momenteel niet ondersteund. Dergelijke visuele elementen worden als een blanco afbeelding naar PowerPoint geëxporteerd met een foutmelding die aangeeft dat het visuele element niet wordt ondersteund.
* **Aangepaste visuele elementen** die zijn **gecertificeerd** worden ondersteund. Voor meer informatie over gecertificeerde aangepaste visuele elementen, inclusief een certificatie verkrijgen voor een aangepast visueel element, zie [Een certificatie verkrijgen voor een aangepast visueel element](../power-bi-custom-visuals-certified.md). Aangepaste visuele elementen die niet gecertificeerd zijn, worden niet ondersteund. Dergelijke visuele elementen worden als een blanco afbeelding naar PowerPoint geëxporteerd met een foutmelding die aangeeft dat het visuele element niet wordt ondersteund.
* Rapporten met meer dan 30 rapportpagina's kunnen momenteel niet worden geëxporteerd.
* Het proces van het exporteren van een rapport naar PowerPoint kan enkele minuten duren. Factoren die de benodigde tijd kunnen beïnvloeden zijn onder meer de structuur van het rapport en de huidige belasting van de Power BI-service.
* Als het menu-item **Exporteren naar PowerPoint** niet beschikbaar is in de Power BI-service, heeft uw tenantbeheerder de functie waarschijnlijk uitgeschakeld. Neem contact op met uw tenantbeheerder voor meer informatie.
* Achtergrondafbeeldingen worden bijgesneden binnen het begrenzingsgebied van de grafiek. Het wordt ten zeerste aanbevolen om achtergrondafbeeldingen te verwijderen voordat u naar PowerPoint exporteert.
* Pagina's in PowerPoint worden altijd aangemaakt in het standaard 9:16-formaat, ongeacht de oorspronkelijke paginaformaten of afmetingen in het Power BI-rapport.
* Rapporten die eigendom zijn van een gebruiker buiten uw Power BI-tenantdomein (zoals een rapport dat eigendom is van iemand buiten uw organisatie en dat met u wordt gedeeld) kunnen niet worden gepubliceerd naar PowerPoint.
* Als u een dashboard deelt met iemand buiten uw organisatie (en daarmee een gebruiker die niet in uw Power BI-tenant is) dan kan die gebruiker de aan het gedeelde dashboard gekoppelde rapporten niet exporteren naar PowerPoint. Als u bijvoorbeeld aaron@contoso.com bent, kunt u delen met david@cohowinery.com. Maar david@cohowinery.com kan de gekoppelde rapporten niet exporteren naar PowerPoint.
* Mogelijk kunt u met oudere versies van PowerPoint geen exports uitvoeren.
* Zoals eerder vermeld, wordt elke rapportpagina geëxporteerd als één afbeelding in het PowerPoint-bestand.
* De Power BI-service gebruikt uw taalinstelling voor Power BI als taal voor het exportbestand van PowerPoint. Als u uw voorkeurstaal wilt zien of instellen, selecteert u het tandwielpictogram ![tandwielpictogram](media/end-user-powerpoint/power-bi-settings-icon.png) **> Instellingen > Algemeen > Taal**.
* Het **Gedownload op**-tijdstip op de titeldia van het geëxporteerde PowerPoint-bestand is ingesteld op de tijdzone van uw computer op het moment van de export.
* URL-filters worden momenteel niet gerespecteerd als Huidige waarden wordt gekozen voor uw export.

## <a name="next-steps"></a>Volgende stappen
[Een rapport afdrukken](end-user-print.md)
