---
title: Het deelvenster Analyse
description: Dynamische referentielijnen maken in Power BI Visuals
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b3b50f8dbcf40a3923e86422e24f8ed020894445
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425523"
---
# <a name="analytics-pane-in-power-bi-visuals"></a>Het deelvenster Analyse in Power BI Visuals

In november 2018 is het **deelvenster Analyse** [geïntroduceerd voor native visuals](https://docs.microsoft.com/power-bi/desktop-analytics-pane).
Aangepaste visuals met API versie 2.5.0 kunnen hun eigenschappen in het **deelvenster Analyse** presenteren en beheren.

![Het deelvenster Analyse](./media/visualization-pane-analytics-tab.png)

Dit wordt gedaan op vergelijkbare wijze als [het beheren van eigenschappen in het opmaakvenster](https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial-format-options), door het definiëren van een object in het bestand capabilities.json van de visual. 

De verschillen zijn als volgt:

1. Voeg onder de definitie van de `object` een `objectCategory`-veld toe met de waarde 2.

    > [!NOTE]
    > Het `objectCategory`-veld is een optioneel veld dat is geïntroduceerd in API 2.5.0. Hiermee wordt het aspect van de visual gedefinieerd dat door het object wordt bestuurd (1 = opmaak, 2 = analyse). 'Opmaak' wordt gebruikt voor uiterlijk, kleuren, assen, labels enz. 'Analyse' wordt gebruikt voor prognoses, trendlijnen, referentielijnen, vormen enz.
    >
    > Als het wordt weggelaten, is `objectCategory` standaard 'Opmaak'.

2. Het object moet de volgende twee eigenschappen hebben:
    1. `show` van het type bool, met de standaardwaarde false.
    2. `displayName` van het type text. De standaardwaarde die u kiest, wordt de aanvankelijke weergavenaam van de instantie.

```json
{
  "objects": {
    "YourAnalyticsPropertiesCard": {
      "displayName": "Your analytics properties card's name",
      "objectCategory": 2,
      "properties": {
        "show": {
          "type": {
            "bool": true
          }
        },
        "displayName": {
          "type": {
            "text": true
          }
        },
      ... //any other properties for your Analytics card
      }
    }
  ...
  }
}
```

Andere eigenschappen kunnen worden gedefinieerd op dezelfde manier als bij opmaak-objecten. Objectinventarisatie gaat precies hetzelfde als in het **Opmaakvenster**.

***Bekende beperkingen en problemen***

  1. Er is nog geen ondersteuning voor meerdere instanties. Objecten kunnen geen andere [selector](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties/#selector) hebben dan static (dat wil zeggen "selector": null), en aangepaste visuals kunnen geen door de gebruiker gedefinieerde meerdere instanties van een kaart hebben.
  2. Eigenschappen van het type `integer` worden niet correct weergegeven. Als tijdelijke oplossing kunt u in plaats daarvan het type `numeric` gebruiken.

> [!NOTE]
> Gebruik het deelvenster Analyse alleen voor objecten die nieuwe informatie toevoegen of nieuw licht werpen op de gepresenteerde informatie. Bijvoorbeeld dynamische referentielijnen die belangrijke trends illustreren.
> Opties die het uiterlijk en de werking van de visual bepalen, dat wil zeggen opmaak, moeten in het deelvenster Opmaak worden gehouden.
