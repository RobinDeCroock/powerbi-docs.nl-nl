---
title: Gegevenscategorisatie in Power BI Desktop
description: Gegevenscategorisatie in Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 733006c1fcec2b541e0f2e3011f4c1f631608698
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/06/2017
---
# <a name="data-categorization-in-power-bi-desktop"></a>Gegevenscategorisatie in Power BI Desktop
In **Power BI Desktop** kunt u de gegevenscategorie voor een kolom opgeven, zodat Power BI Desktop weet hoe de waarden ervan moeten worden behandeld in een visualisatie.

Wanneer Power BI Desktop gegevens importeert, krijgt het niet alleen de gegevens zelf, maar ook informatie als de tabel- en kolomnamen, of het een primaire sleutel betreft, enzovoort.  Met die informatie doet Power BI Desktop enkele veronderstellingen over hoe u een goede standaardervaring kunt krijgen bij het maken van een visualisatie. 

Hier volgt een voorbeeld: wanneer Power BI Desktop detecteert dat een kolom numerieke waarden bevat, wilt u deze waarschijnlijk op een bepaalde manier aggregeren en worden deze daarom in het gebied Waarden geplaatst. Of, voor een kolom met datum-/tijdwaarden, wordt aangenomen dat u deze waarschijnlijk als een tijdhiërarchie-as in een lijndiagram wilt gebruiken.

Maar een aantal gevallen vormt een grotere uitdaging, zoals geografie. Bekijk de volgende tabel uit een Excel-werkblad:

![](media/desktop-data-categorization/datacategorizationtable.png)

Moet Power BI Desktop de codes in de kolom GeoCode behandelen als een afkorting voor een land of een Amerikaanse staat?  Het is niet duidelijk omdat een code zoals deze beide kan betekenen.  AL kan bijvoorbeeld staan voor Alabama of Albanië, AR kan staan voor Arkansas of Argentinië, en CA kan staan voor Californië of Canada. Het maakt een verschil wanneer we ons GeoCode-veld op een kaart plaatsen.  Moet Power BI Desktop een afbeelding van de wereld weergeven met de landen gemarkeerd of een afbeelding van de Verenigde Staten met de staten gemarkeerd?  Voor gegevens zoals deze kunt u een gegevenscategorie opgeven. Gegevenscategorisatie biedt een verdere verfijning van de informatie die Power BI Desktop kan gebruiken om de beste visualisaties te verstrekken.  

**Een gegevenscategorie opgeven**

1. Selecteer in de rapportweergave of gegevensweergave in de lijst **Velden** het veld dat u op een andere categorisatie wilt sorteren.
2. Klik in het lint op het tabblad **Hulpmiddelen voor gegevens - Model maken** op de vervolgkeuzelijst **Gegevenscategorie:**.  Hier worden de mogelijke gegevenscategorieën weergegeven die u kunt kiezen voor uw kolom.  Sommige selecties zijn mogelijk uitgeschakeld als ze niet werken met het huidige gegevenstype van uw kolom.  Als een kolom bijvoorbeeld een binair gegevenstype is, staat Power BI Desktop u niet toe om geografische gegevenscategorieën te kiezen. 

![](media/desktop-data-categorization/datacategorization.gif)

Dat is alles!  Elk gedrag dat normaal gesproken tot een visueel element leidt, werkt nu automatisch.  

Mogelijk hebt u ook interesse voor informatie over [geografische filters voor mobiele Power BI-apps](desktop-mobile-geofiltering.md).
