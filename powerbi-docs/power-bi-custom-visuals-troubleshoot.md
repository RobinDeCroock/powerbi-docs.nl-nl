---
title: Problemen oplossen die zich voordoen bij het ontwikkelen van Power BI-visuals
description: In dit artikel worden enkele veelvoorkomende problemen besproken die kunnen optreden tijdens de ontwikkeling van een aangepaste visual voor Power BI.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: troubleshooting
ms.date: 11/06/2018
ms.openlocfilehash: 6fce02a4707d12859286f85073222b498a1a59f4
ms.sourcegitcommit: e5cf19e16112c7dad1591c3b38d232267ffb3ae1
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72543887"
---
# <a name="troubleshoot-power-bi-power-bi-visuals"></a>Problemen met Power BI-visuals oplossen

## <a name="debug"></a>Fouten opsporen

**Kan de opdracht pbiviz niet vinden (of een vergelijkbare fouten)**

Als u `pbiviz` uitvoert vanaf de opdrachtregel in uw terminal wordt het Help-scherm weergegeven. Als dat niet het geval is, is de installatie niet goed verlopen. Zorg ervoor dat u hebt minimaal versie 4.0 van NodeJS hebt geïnstalleerd.

**Kan de foutopsporingsvisual niet vinden op het tabblad Visualisaties**

De foutopsporingsvisual ziet eruit als een promptpictogram en bevindt zich op het tabblad **Visualisaties**.

![Selectie van visual](media/power-bi-custom-visuals-troubleshoot/powerbi-developer-visual-selection.png)

Als de visual niet wordt weergegeven, controleert u of u deze hebt ingeschakeld in de instellingen van Power BI.

> [!NOTE]
> De foutopsporingsvisual is momenteel alleen beschikbaar in de Power BI-service en niet in Power BI Desktop of de mobiele app. De verpakte visual werkt wel overal.

**Kan geen contact maken met de server van het visuele element**

Gebruik de opdracht `pbiviz start` vanaf de opdrachtregel in uw terminal vanuit de hoofdmap van het visualproject om de server van de visual uit te voeren. Als de server niet wordt uitgevoerd, zijn uw SSL-certificaten waarschijnlijk niet goed geïnstalleerd.

U kunt contact opnemen met het ondersteuningsteam voor Power BI-visuals: *pbicvsupport@microsoft.com*  bij vragen, opmerkingen of problemen.

## <a name="next-steps"></a>Volgende stappen

Ga naar [Veelgestelde vragen over Power BI-visuals](power-bi-custom-visuals-faq.md#organizational-visuals) voor meer informatie.