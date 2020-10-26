---
title: Mobiele ontwikkeling
description: Mobiel-vriendelijke Power BI-visuals maken
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/12/2019
ms.openlocfilehash: dca16fd29dc89fc2e67ce1e8f5c6abfc0adcb9a6
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "92049287"
---
# <a name="how-to-create-mobile-friendly-power-bi-visuals"></a>Mobiel-vriendelijke Power BI-visuals maken
Het mobiele verbruik speelt een belangrijke rol in Power BI. Een van de sterke punten is dat het altijd en overal verbinding houdt met uw gegevens.

Als ontwikkelaar die Power BI-visuals maakt, moet u de unieke beperkingen van elk mobiel apparaat zoveel mogelijk oplossen, zodat u zoveel mogelijk gebruikers bereikt en de beste mobiele ervaring biedt.

Gebruik de [Power BI-app voor Windows, iOS en Android](../../consumer/mobile/mobile-apps-for-mobile-devices.md) waarmee uw zakelijke gebruikers onderweg een uitgebreid overzicht van hun gegevens paraat hebben.

## <a name="requirements"></a>Vereisten

De volgende vereisten zijn essentieel voor een mobiel-vriendelijke ontwikkeling van visuals:

- Renderen

  Uw Power BI-visuals moeten worden weergegeven op alle ondersteunde mobiele apparaten, waaronder ondersteunde browsers en toepassingen, zonder fouten in rapporten, dashboards of wanneer ze worden uitgevoerd in de modus **Focus**. 

- Interactief

  Interactieve functies moeten op dezelfde manier worden ingesteld als voor desktopapparaten. Alle gebeurtenissen die worden verwerkt op desktopbrowsers moeten worden ondersteund of vergelijkbare gebeurtenis-handlers hebben voor mobiele apparaten.
  
  Bijvoorbeeld: basisnavigatie en de selectie van gegevenspunten moeten dezelfde functionaliteit hebben als in desktopbrowsers. Als een visual ondersteuning biedt voor meervoudige selectie met **Ctrl**, kan de ontwikkelaar een soortgelijke gebeurtenis-handler toevoegen voor mobiele apparaten.

  De volgende tabel bevat een lijst met corresponderende gebeurtenissen op mobiele apparaten.

  | Naam van de muisgebeurtenis | Naam van de aanraakgebeurtenis |
  |:----------------:|:----------------:|
  | `click` | `click` |
  | `mousemove` | `touchmove` |
  | `mousedown` | `touchstart` |
  | `mouseup` | `touchend` |
  | `dblclick` | externe bibliotheek gebruiken |
  | `contextmenu` | externe bibliotheek gebruiken |
  | `mouseover` | `touchmove` |
  | `mouseout` | `touchmove` (of externe bibliotheek) |
  | `wheel` | `NaN` |

  > [!NOTE]
  > Niet alle mobiele apparaten of apparaten met aanraakscherm ondersteunen de muis- (of door de *muis* voorafgegane) gebeurtenissen. In dergelijke gevallen moet u tegelijk *muis-* en *aanraak*gebeurtenissen afhandelen.

## <a name="optional"></a>Optioneel
Het volgende wordt aangemerkt als optioneel en wordt gebruikt om een betere eindgebruikerservaring te creëren.

- Renderen

  Als u visuals met kleinere afmetingen wilt ondersteunen, voegt u opmaakopties toe die de gebruiker kan wijzigen om de grootte van elk element aan te passen. U kunt bijvoorbeeld opmaakopties toevoegen aan labels, voor gebruik in rapporten en dashboards. Hiermee kunnen gebruikers een visual specifiek aanpassen voor hun mobiele apparaat.
  
  Dezelfde instellingen kunnen ook worden toegepast op de visuals in desktopbrowsers, en desgewenst worden overschreven om de visual aan te passen aan kleinere schermen.

  > [!NOTE]
  > Als u een visual in de modus **Focus** wilt optimaliseren, moet u rekening houden met de staande en liggende stand van de schermformaat. Zie [Inhoud weergeven in de modus Focus](../../consumer/end-user-focus.md).

- Interactief

  U kunt specifieke gebeurtenis-handlers toevoegen voor mobiele apparaten, zoals slepen en schuiven.

- Failover

  Een visual moet een beschrijvende fout bevatten als deze niet op het mobiele apparaat kan worden weergegeven.

## <a name="supported-browsers-and-devices"></a>Ondersteunde browsers en apparaten
De Power BI-visual moet worden weergegeven op alle apparaten die Power BI-apps ondersteunen. Zie [Ondersteunde browsers voor Power BI](../../fundamentals/power-bi-browsers.md) en [Mobiele Power BI-apps](../../consumer/mobile/mobile-apps-for-mobile-devices.md) voor meer informatie.

Bij het testen op de nieuwste modellen van Windows-, iOS-en Android-apparaten moet de ontwikkelaar over de meeste van deze kwaliteitsaspecten nadenken.

## <a name="next-steps"></a>Volgende stappen
Zie [Een aangepaste visual met cirkelkaart voor Power BI ontwikkelen](./develop-circle-card.md) om aan de slag te gaan.