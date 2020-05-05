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
ms.openlocfilehash: 38e6ac3be143381304f1fdfc8e1427b91f398a9a
ms.sourcegitcommit: 1059c6222458f189fb5301dcb689dad2b2c00bc1
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196624"
---
# <a name="how-to-create-mobile-friendly-power-bi-visuals"></a>Mobiel-vriendelijke Power BI-visuals maken
Het mobiele verbruik speelt een belangrijke rol in Power BI. Een van de sterke punten is dat het altijd en overal verbinding houdt met uw gegevens.

Als ontwikkelaar die Power BI-visuals maakt, moet u de unieke beperkingen van elk mobiel apparaat zoveel mogelijk oplossen, zodat u zoveel mogelijk gebruikers bereikt en de beste mobiele ervaring biedt.

Gebruik de [Power BI-app voor Windows, iOS en Android](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices) waarmee uw zakelijke gebruikers onderweg een uitgebreid overzicht van hun gegevens paraat hebben.

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
  > Als u een visual in de modus **Focus** wilt optimaliseren, moet u rekening houden met de staande en liggende stand van de schermformaat. Zie [Inhoud weergeven in de modus Focus](/power-bi/consumer/end-user-focus).

- Interactief

  U kunt specifieke gebeurtenis-handlers toevoegen voor mobiele apparaten, zoals slepen en schuiven.

- Failover

  Een visual moet een beschrijvende fout bevatten als deze niet op het mobiele apparaat kan worden weergegeven.

## <a name="supported-browsers-and-devices"></a>Ondersteunde browsers en apparaten
De Power BI-visual moet worden weergegeven op alle apparaten die Power BI-apps ondersteunen. Zie [Ondersteunde browsers voor Power BI](/power-bi/power-bi-browsers) en [Mobiele Power BI-apps](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices) voor meer informatie.

Bij het testen op de nieuwste modellen van Windows-, iOS-en Android-apparaten moet de ontwikkelaar over de meeste van deze kwaliteitsaspecten nadenken.

## <a name="next-steps"></a>Volgende stappen
Als u aan de slag wilt gaan, raadpleegt u [Zelfstudie: Een Power BI-visual ontwikkelen](/power-bi/developer/visuals/custom-visual-develop-tutorial).
