---
title: Classificatie van dashboardgegevens
description: Hier leest u alles over de classificatie van dashboardgegevens, onder andere hoe een beheerder dit instelt en hoe de eigenaar van een dashboard de classificatie kan aanpassen.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 08/10/2017
LocalizationGroup: Dashboards
ms.openlocfilehash: e576cb5c0092d61d8c4b30fd180f66cef2922b0e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96388788"
---
# <a name="dashboard-data-classification"></a>Classificatie van dashboardgegevens
Elk dashboard is anders en afhankelijk van de gegevensbron waarmee u verbinding maakt, zult u waarschijnlijk merken dat u en de collega's met wie u het dashboard deelt, verschillende voorzorgsmaatregelen zullen moeten nemen, afhankelijk van de vertrouwelijkheid van de gegevens. Sommige dashboards mogen nooit worden afgedrukt of worden gedeeld met personen buiten uw bedrijf, terwijl andere zonder beperkingen kunnen worden gedeeld. Door gegevens in het dashboard te classificeren, kunt u anderen die het dashboard raadplegen, bewust maken van de mate van beveiliging die vereist is. U kunt uw dashboards voorzien van classificatietags die zijn opgesteld door de IT-afdeling van uw bedrijf, zodat iedereen die de inhoud bekijkt, weet hoe het staat met de vertrouwelijkheid van de gegevens.

![Schermopname van een dashboard, waarin gegevensclassificatie uit een voorbeeld wordt weergegeven.](media/service-data-classification/dashboard_tagged_as_hbi.png)

## <a name="data-classification-tags"></a>Tags voor gegevensclassificatie
Tags voor gegevensclassificatie worden weergegeven naast de naam van het dashboard, zodat iedereen direct kan zien welk beveiligingsniveau moet worden toegepast op het dashboard en de daarin opgenomen gegevens.

![Schermopname van een dashboard, met een tag voor gegevensclassificatie naast de naam van het dashboard.](media/service-data-classification/tag_next_to_title.png)

Labels worden ook weergegeven naast de dashboardtegel in de lijst met favorieten.

![Schermopname van de lijst met favorieten, met een tag voor gegevensclassificatie naast de dashboardtegel in de lijst met favorieten.](media/service-data-classification/tag_on_dashboard_tile.png)

Wanneer u een tag aanwijst met de muis, ziet u de volledige naam van de classificatie.

![Schermopname van de HBI-tag, waarin de volledige naam van de classificatie wordt weergegeven wanneer u de muisaanwijzer over de tag beweegt. ](media/service-data-classification/tag_tooltip.png)

Beheerders kunnen ook een URL instellen voor een tag om extra informatie te bieden.

> [!NOTE]
> Afhankelijk van de classificatie-instellingen die de beheerder heeft geselecteerd, is het mogelijk dat bepaalde typen classificatie niet als een tag worden weergegeven op het dashboard. Als u de eigenaar van een dashboard bent, kunt u het type classificatie van het dashboard altijd controleren in de instellingen van het dashboard.
> 
> 

## <a name="setting-a-dashboards-classification"></a>De classificatie van een dashboard instellen
Als gegevensclassificatie is ingeschakeld voor uw bedrijf, hebben alle dashboards een standaardtype classificatie. Als de eigenaar van een dashboard, kunt u de classificatie echter aanpassen aan het gewenste beveiligingsniveau voor uw dashboard.

Ga als volgt te werk om het type classificatie te wijzigen:

1. Ga naar de instellingen van het dashboard door de **drie puntjes** naast de naam van het dashboard te selecteren en **Instellingen** te kiezen.
   
    ![Schermopname van een dashboard, waarbij Instellingen is geselecteerd.](media/service-data-classification/dashboard_settings.png)
2. In het deelvenster met instellingen kunt u de huidige classificatie voor het dashboard zien en via de vervolgkeuzelijst het type classificatie wijzigen.
   
    ![Schermopname van de instellingen van het dashboard met de huidige classificatie, waarbij de vervolgkeuzelijst Gegevensclassificatie is geselecteerd.](media/service-data-classification/classification_setting_dropdown.png)
3. Selecteer **Toepassen** wanneer u klaar bent.

Nadat u de wijziging hebt toepast, ziet iedereen met wie u het dashboard hebt gedeeld de nieuwe classificatie wanneer ze het dashboard opnieuw laden.

## <a name="working-with-data-classification-tags-as-an-admin"></a>Werken met tags voor gegevensclassificatie als beheerder
Gegevensclassificatie wordt ingesteld door de globale beheerder voor uw organisatie. Ga als volgt te werk om gegevensclassificatie in te schakelen:

1. Selecteer het pictogram Instellingen (tandwiel) en selecteer **Beheerportal**.
   
    ![Schermopname van het pictogram Instellingen, waarbij Beheerportal is geselecteerd.](media/service-data-classification/admin_portal_in_settings.png)
2. Ga naar het tabblad **Tenantinstellingen** en zet **Gegevensclassificatie voor dashboards** op *Ingeschakeld* .
   
    ![Schermopname van Beheerportal, met daarin de Tenantinstellingen en de selectie van de gegevensclassificatie voor dashboards en rapporten.](media/service-data-classification/data_classification_switch_location.png)

Er wordt nu een formulier weergegeven voor het maken van de verschillende classificaties in uw organisatie.

![Schermopname van een formulier met daarin veldvermeldingen voor verschillende classificaties in uw organisatie.](media/service-data-classification/blank_classification_form.png)

Voor elke classificatie kunt u een **naam** en **steno** (verkorte schrijfwijze) opgeven, die beide worden weergegeven op het dashboard. Voor elke classificatie kunt u via het selectievakje **Label weergeven** bepalen of de verkorte schrijfwijze al dan niet wordt weergegeven op het dashboard. Als u besluit het type classificatie niet weer te geven op het dashboard, kan de eigenaar het type nog steeds zien door de dashboardinstellingen te controleren. U kunt eventueel ook een **URL** toevoegen die aanvullende informatie bevat over de richtlijnen en gebruiksvereisten die binnen uw gelden voor classificatie.  

Het laatste wat u moet beslissen, is welke classificatie standaard moet worden toegewezen.  

Als u het formulier helemaal hebt ingevuld, selecteert u **Toepassen** om de wijzigingen op te slaan.

![Schermopname van een formulier, waarin ingevulde vermeldingen worden weergegeven met de toe te passen typen classificaties.](media/service-data-classification/filled_in_classification_form.png)

Op dit punt wordt aan alle dashboards de standaardclassificatie toegewezen. Dashboardeigenaren kunnen nu het classificatietype bijwerken naar het juiste type voor hun inhoud. U kunt hier altijd terugkomen om classificatietypen toe te voegen of te verwijderen of om de standaardinstelling wijzigen.  

> [!NOTE]
> Er zijn een paar dingen die belangrijk zijn als u hier terugkeert om wijzigingen aan te brengen:
> 
> * Als u gegevensclassificatie uitschakelt, wordt geen van de tags onthouden. U moet dus helemaal opnieuw beginnen als u deze functie later weer wilt inschakelen.  
> * Als u een type classificatie verwijdert, krijgen dashboards met dit type classificatie automatisch de standaardclassificatie totdat de eigenaar dit wijzigt.  
> * Als u de standaardclassificatie wijzigt, krijgen alle dashboards die nog geen classificatie van de eigenaar hebben gekregen, de nieuwe standaardclassificatie.
> 
> 

