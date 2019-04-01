---
title: Rapporten naar PDF exporteren
description: Leer hoe u een Power BI-rapport naar PDF kunt exporteren.
author: mihart
manager: kvivek
ms.custom: ''
ms.reviewer: cmfinlan
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 02/14/2019
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: e15cb6e09ff493512bb1b87939004c851b31fa10
ms.sourcegitcommit: 9f31cd41bd92e398717da5a69a074273e8c6f8a6
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58473724"
---
# <a name="export-reports-from-power-bi-to-pdf"></a>Rapporten exporteren van Power BI naar PDF
Met Power BI kunt u uw rapport publiceren naar PDF-indeling en heel eenvoudig een document op basis van uw Power BI-rapport maken. Wanneer u **naar PDF exporteert**, wordt elke pagina in het Power BI-rapport een afzonderlijke pagina in het PDF-document.

## <a name="how-to-export-your-power-bi-report-to-pdf"></a>Uw Power BI-rapport naar PDF exporteren
Selecteer in de Power BI-service een rapport om weer te geven op het canvas. U kunt ook een rapport selecteren via de pagina Start, Apps of een andere sectie in het linkernavigatievenster.

1. Selecteer **Bestand** > **Exporteren naar PDF** in de menubalk.

    ![Selecteer Bestand in de menubalk, de pijl wijst naar Exporteren naar PDF](media/end-user-pdf/power-bi-export-pdf.png)

    Er wordt een pop-upvenster weergegeven waar u de mogelijkheid hebt om **Huidige weergave** of **Standaardweergave** te selecteren.  Met **Huidige weergave** exporteert u het rapport in de huidige staat, inclusief de actieve wijzigingen die u in de slicer- en filterwaarden hebt aangebracht.  De meeste gebruikers selecteren deze optie.  U kunt ook **Standaardweergave** selecteren, waarmee u het rapport in de oorspronkelijke staat exporteert (zoals de auteur dit heeft gedeeld), en waarin geen wijzigingen zijn weergegeven die u aan de oorspronkelijke staat hebt aangebracht.
    
    Daarnaast is er een selectievakje dat u kunt in-/uitschakelen voor het wel of niet exporteren van de verborgen tabbladen van een rapport.  U hoeft enkel dit selectievakje in te schakelen als u alleen tabbladen van een rapport wilt exporteren die voor u in uw browser zichtbaar zijn.  Als u liever alle verborgen tabbladen mee wilt krijgen als onderdeel van de export, kunt u dit beter uitgeschakeld laten.  Als het selectievakje grijs wordt weergegeven, zijn er geen verborgen tabbladen in het rapport.  Nadat u uw selecties hebt gemaakt, klikt u op de knop Exporteren om door te gaan.
    
    Er wordt een voortgangsbalk weergegeven in de rechterbovenhoek. Het exporteren kan enkele minuten duren; u kunt tijdens het exporteren van het rapport in Power BI blijven werken.

    ![Bericht over voortgang van exporteren](media/end-user-pdf/power-bi-export-message.png)

    Wanneer u klaar bent, wijzigt de meldingsbanner zodat u weet dat de Power BI-service het exportproces heeft voltooid.

2. Het bestand is beschikbaar wanneer de gedownloade bestanden worden weergegeven in uw browser. In de volgende afbeelding wordt dit weergegeven als een downloadbanner langs de onderkant van het browservenster.

    ![Locatie van het gedownloade bestand](media/end-user-pdf/power-bi-save-file.png)

Zo eenvoudig werkt dat. U kunt het bestand downloaden en openen met een PDF-viewer, zoals de viewer in Microsoft Edge.


## <a name="limitations-and-considerations"></a>Beperkingen en overwegingen
Er zijn enkele overwegingen en beperkingen waarmee u rekening moet houden bij het werken met de functie **Exporteren naar PDF**.

* **R-visualisaties** worden momenteel niet ondersteund. Deze visuals zijn in de PDF leeg en er wordt een foutbericht weergegeven.  

* **Aangepaste visuele elementen** die zijn **gecertificeerd** worden ondersteund. Voor meer informatie over gecertificeerde aangepaste visuele elementen, inclusief een certificatie verkrijgen voor een aangepast visueel element, zie [Een certificatie verkrijgen voor een aangepast visueel element](../power-bi-custom-visuals-certified.md). Aangepaste visuals die niet zijn gecertificeerd, worden niet ondersteund. Deze worden in de PDF met een foutbericht weergegeven.   

* Rapporten met meer dan 30 rapportpagina's kunnen momenteel niet worden geëxporteerd.

* Het proces van het exporteren van een rapport naar PDF kan enkele minuten duren. Factoren die de benodigde tijd kunnen beïnvloeden zijn onder meer de structuur van het rapport en de huidige belasting van de Power BI-service.

* Als het menu-item **Exporteren naar PDF** niet beschikbaar is in de Power BI-service, heeft uw tenantbeheerder de functie waarschijnlijk uitgeschakeld. Neem contact op met uw tenantbeheerder voor meer informatie.

* Achtergrondafbeeldingen worden bijgesneden binnen het begrenzingsgebied van de grafiek. Het wordt ten zeerste aanbevolen om achtergrondafbeeldingen te verwijderen voordat u naar PDF exporteert.

* Rapporten die eigendom zijn van een gebruiker buiten uw Power BI-tenantdomein (zoals een rapport dat eigendom is van iemand buiten uw organisatie en dat met u wordt gedeeld) kunnen niet naar PDF worden gepubliceerd.

* Als u een dashboard deelt met iemand buiten uw organisatie (en daarmee een gebruiker die geen deel uitmaakt van uw Power BI-tenant), dan kan die gebruiker de aan het gedeelde dashboard gekoppelde rapporten niet exporteren naar PDF. Als u bijvoorbeeld aaron@contoso.com bent, kunt u delen met cassie@cohowinery.com. Maar cassie@cohowinery.com kan de gekoppelde rapporten niet exporteren naar PDF.

* Wanneer u rapporten met een achtergrondafbeelding exporteert naar PDF, ziet u in de export mogelijk een vervormde afbeelding als u de optie Normaal of Opvullen kiest voor de pagina-achtergrond.  Voor het beste resultaat gebruikt u de optie Aanpassen. Zo voorkomt u problemen met uw geëxporteerde document.

* De Power BI-service gebruikt uw taalinstelling voor Power BI als taal voor het geëxporteerde PDF-bestand. Als u uw voorkeurstaal wilt zien of instellen, selecteert u het tandwielpictogram > **Instellingen** > **Algemeen** > **Taal**.

* URL-filters worden momenteel niet gerespecteerd als Huidige waarden wordt gekozen voor uw export.

## <a name="next-steps"></a>Volgende stappen
[Een rapport afdrukken](end-user-print.md)
