---
title: Titels op basis van een expressie in Power BI Desktop
description: Dynamische titels maken in Power BI Desktop die veranderen op basis van programmatische expressies met programmatische voorwaardelijke opmaak
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b90ef66d2c118a70f1b18ed4fe302ce1db23e45c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769739"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Titels op basis van een expressie in Power BI Desktop

U kunt dynamisch is, maakt aangepaste titels voor visuele elementen in uw Power BI. Als u Data Analysis Expressions (DAX) op basis van velden, variabelen of andere programmatische elementen maakt, aanpassen uw visuals titels automatisch naar wens. Deze wijzigingen zijn gebaseerd op de filters, selecties, of andere gebruikersinteracties en configuraties.

![Schermafbeelding van de Power BI Desktop-optie voor voorwaardelijke opmaak](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

Het maken van dynamische titels, ook wel genoemd *titels op basis van een expressie*, is eenvoudig. 

## <a name="create-a-field-for-your-title"></a>Maken van een veld voor de titel

De eerste stap bij het maken van een titel op basis van een expressie is het maken van een veld in het model moet worden gebruikt voor de titel. 

Er zijn allerlei soorten creatieve manieren om de titel van uw visual weer wat u wilt deze om in te spreken, of wat u wilt express. Laten we eens een paar voorbeelden bekijken.

U kunt een expressie die wijzigingen op basis van de filtercontext die het visuele element voor de naam van het product ontvangt. De volgende afbeelding ziet u de DAX-formule voor een dergelijk veld.

![Schermafbeelding van de DAX-formule](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Een ander voorbeeld maakt gebruik van een dynamische titel die wijzigingen die zijn gebaseerd op de taal of de cultuur van de gebruiker. U kunt taalspecifieke titels in een DAX-meting maken met behulp van de `USERCULTURE()` functie. Deze functie retourneert de cultuurcode voor de gebruiker, op basis van hun besturingssysteem of de browserinstellingen. U kunt de volgende DAX-switch-instructie gebruiken om de juiste vertaalde waarde te selecteren. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

Of u kunt de tekenreeks ophalen uit een lookup-tabel met alle vertalingen. U plaatst die tabel in uw model. 

Dit zijn slechts een paar voorbeelden die kunt u dynamische, op basis van een expressie titels voor visuele elementen maken in Power BI Desktop. Wat u kunt doen met uw titels zijn beperkt tot alleen uw eigen verbeelding en het model.


## <a name="select-your-field-for-your-title"></a>Selecteer het veld voor de titel

Nadat u de DAX-expressie voor het veld dat u in het model maakt hebt gemaakt, moet u wilt toepassen op de titel van uw visuele element.

Selecteer het veld en pas deze toe, gaat u naar de **visualisaties** deelvenster. In de **indeling** gedeelte **titel** om de opties voor titel voor het visuele element weer te geven. 

Wanneer u met de rechtermuisknop **titeltekst**, een snelmenu weergegeven waarmee u selecteren ***fx * voorwaardelijke opmaak**. Wanneer u dat menu-item selecteert een **titeltekst** in het dialoogvenster wordt weergegeven. 

![Schermafbeelding van de titel van het dialoogvenster tekst](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

In dit venster kunt u het veld dat u hebt gemaakt als u wilt gebruiken voor de titel.

## <a name="limitations-and-considerations"></a>Beperkingen en overwegingen

Er zijn enkele beperkingen met betrekking tot de huidige implementatie van op basis van een expressie titels voor visuele elementen:

* Opmaak op basis van een expressie wordt momenteel niet ondersteund op visuele elementen voor Python, R-visuals of de sleutel testteam visual.
* Het veld dat u voor de titel maakt moet een tekenreeksgegevenstype zijn. Metingen die resulteren in getallen of datum/tijd (of een ander gegevenstype) worden momenteel niet ondersteund.

## <a name="next-steps"></a>Volgende stappen

Dit artikel wordt beschreven hoe u DAX-expressies die de titels van uw visuele elementen in dynamische velden deze veranderen omzetten kunnen wanneer gebruikers met rapporten werken maakt. Mogelijk vindt u de volgende artikelen handig ook.

* [Cross-rapport drillthrough gebruiken in Power BI Desktop](desktop-cross-report-drill-through.md)
* [Drillthrough gebruiken in Power BI Desktop](desktop-drillthrough.md)