---
title: Power BI-gegevens beveiligen met apparaateigen identificatie
description: Lees hoe u uw iOS-app zo configureert dat er aanvullende identificatie wordt vereist voordat u toegang krijgt tot uw Power BI-gegevens
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: mshenhav
ms.openlocfilehash: b7418c9579a439a18a30a967947c15d58693fd44
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/16/2019
ms.locfileid: "66816818"
---
# <a name="protect-power-bi-app-with-face-id-touch-id-or-passcode"></a>De Power BI-app beveiligen met Face ID, Touch ID of een wachtwoordcode 

In veel gevallen zijn de gegevens die worden beheerd in Power BI vertrouwelijk. Deze gegevens moeten worden beveiligd en mogen alleen toegankelijk zijn voor geautoriseerde gebruikers. 

Met de Power BI-app voor iOS kunt u uw gegevens beschermen door extra identificatie te configureren. Elke keer dat u de app start of van de achtergrond naar de voorgrond haalt, moet u zich via Face ID, Touch ID of een wachtwoordcode identificeren.

| ![iPhone](./media/tutorial-mobile-apps-ios-qna/iphone-logo-50-px.png) | ![iPad](./media/tutorial-mobile-apps-ios-qna/ipad-logo-50-px.png) |
|:--- |:--- |
| iPhones |iPads |

## <a name="turn-on-face-id-touch-id-or-passcode-in-app-setting"></a>Face ID, Touch ID of een wachtwoordcode inschakelen in de app-instelling

Als u gebruik wilt maken van extra identificatie in Power BI, gaat u naar de app-instelling onder **Privacy en beveiliging**. Hier ziet u de optie voor het inschakelen van Face ID, Touch ID of een wachtwoordcode op basis van de mogelijkheden van uw apparaat.

![Instellingspagina van de Power BI-app voor iOS](./media/mobile-ios-native-secure-access/mobile-ios-native-secured-setting.png)

Zodra deze instelling is ingeschakeld, wordt u elke keer dat u Power BI start of van de achtergrond naar voren haalt, gevraagd om u te identificeren voordat u toegang krijgt tot de app. 

De beslissing om te vragen naar Face ID, Touch ID of een wachtwoordcode wordt uitgevoerd door iOS op basis van de mogelijkheden van het apparaat. Als uw apparaat Face ID ondersteunt, moet u Face ID gebruiken. Als uw apparaat Touch ID ondersteunt, moet u Touch ID gebruiken. Als geen van beide wordt ondersteund, moet u een wachtwoordcode opgeven.

![Face ID voor de Power BI-app voor iOS](./media/mobile-ios-native-secure-access/mobile-ios-native-secured-faceid.png)

## <a name="use-mdm-to-enforce-face-id-touch-id-or-passcode"></a>MDM gebruiken om Face ID, Touch ID of een wachtwoordcode af te dwingen

Sommige organisaties hebben beveiligingsbeleid en nalevingsvereisten die extra identificatie afdwingen voordat u toegang krijgt tot gevoelige bedrijfsgegevens. 

Met de mobiele Power BI-app voor iOS kunnen beheerders die instelling beheren door de configuratie-instellingen voor de app te pushen vanuit Microsoft Intune en andere MDM-oplossingen (Mobile Device Management). Beheerders kunnen het beveiligingsbeleid voor apps gebruiken om deze instelling in te schakelen voor alle gebruikers of voor een groep gebruikers.

|Sleutel  |Type  |Beschrijving  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Boolean | De standaardwaarde is Onwaar. <br>Als deze waarde is ingesteld op Waar, worden gebruikers via de app gedwongen zich te identificeren met Face ID, Touch ID of een wachtwoordcode voordat ze Power BI-gegevens kunnen bekijken in de app. Gebruikers die geen Face ID, Touch ID of een wachtwoordcode hebben geconfigureerd op hun apparaat, moeten dit configureren om toegang te krijgen tot Power BI.  |

## <a name="next-steps"></a>Volgende stappen

[MDM gebruiken om de Power BI-app voor iOS extern te configureren](mobile-app-configuration.md)
