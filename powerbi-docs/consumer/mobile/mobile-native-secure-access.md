---
title: Power BI-gegevens beveiligen met apparaateigen identificatie
description: Lees hoe u uw iOS- en Android-apps zo configureert dat er aanvullende identificatie wordt vereist voordat u toegang krijgt tot uw Power BI-gegevens
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/07/2020
ms.author: painbar
ms.openlocfilehash: ce7b3c3bc667023ef36650d8c551caaceab04c02
ms.sourcegitcommit: 9b806dfe62c2dee82d971bb4f89d983b97931b43
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80802796"
---
# <a name="protect-power-bi-app-with-face-id-touch-id-passcode-or-biometric-data"></a>De Power BI-app beveiligen met Face ID, Touch ID of biometrische gegevens 

In veel gevallen zijn de gegevens die worden beheerd in Power BI vertrouwelijk. Deze gegevens moeten worden beveiligd en mogen alleen toegankelijk zijn voor geautoriseerde gebruikers. 

Met de Power BI-apps voor iOS en Android kunt u uw gegevens beschermen door extra identificatie te configureren. Steeds wanneer de app wordt gestart of naar de voorgrond wordt gebracht, is identificatie vereist. In iOS betekent dit het aanbieden van Face ID, Touch ID of een wachtwoordcode. In Android betekent dit het aanbieden van biometrische gegevens (vingerafdruk-id).

Van toepassing op:

| ![iPhone](./media/mobile-native-secure-access/ios-logo-40-px.png) | ![iPads](./media/mobile-native-secure-access/ios-logo-40-px.png) | ![Android-telefoon](././media/mobile-native-secure-access/android-logo-40-px.png) | ![Android-tablet](././media/mobile-native-secure-access/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhones |iPads |Android-telefoons |Android-tablets |

## <a name="turn-on-face-id-touch-id-or-passcode-on-ios"></a>Face ID, Touch ID of een wachtwoordcode inschakelen in iOS

Als u gebruik wilt maken van extra identificatie in de mobiele Power BI-app voor iOS, gaat u naar de app-instelling onder **Privacy en beveiliging**. Hier ziet u de optie voor het inschakelen van Face ID, Touch ID of een wachtwoordcode. De opties die u ziet zijn afhankelijk van de mogelijkheden van uw apparaat.

![Instellingspagina van de Power BI-app voor iOS](./media/mobile-native-secure-access/mobile-ios-native-secured-setting.png)

Wanneer deze instelling is ingeschakeld, wordt u elke keer dat u de app start of naar de voorgrond brengt, gevraagd om uw id aan te bieden voordat u toegang krijgt tot de app.

Welk type id u moet opgeven is afhankelijk van de mogelijkheden van uw apparaat. Als uw apparaat Face ID ondersteunt, moet u Face ID gebruiken. Als uw apparaat Touch ID ondersteunt, moet u Touch ID gebruiken. Als geen van beide wordt ondersteund, moet u een wachtwoordcode opgeven. In de onderstaande afbeelding ziet u het Face ID-verificatiescherm.

![Face ID voor de Power BI-app voor iOS](./media/mobile-native-secure-access/mobile-ios-native-secured-faceid.png)

## <a name="turn-on-biometric-data-fingerprint-id-on-android"></a>Biometrische gegevens (vingerafdruk-id) inschakelen in Android

Als u gebruik wilt maken van extra identificatie in mobiele Power BI-app voor Android, gaat u naar de app-instelling onder **Privacy en beveiliging**. U ziet de optie om biometrische gegevens in te schakelen.

![Instellingspagina van de Power BI-app voor Android](./media/mobile-native-secure-access/mobile-android-native-secured-setting.png)

Wanneer deze instelling is ingeschakeld, wordt u elke keer dat u de app start of naar de voorgrond brengt, gevraagd om uw biometrische gegevens (vingerafdruk-id) aan te bieden voordat u toegang krijgt tot de app.

In de onderstaande afbeelding ziet u het vingerafdrukverificatiescherm.

![Face ID voor de Power BI-app voor iOS](./media/mobile-native-secure-access/mobile-android-native-secured-fingerprint-id.png)

>[!NOTE]
>Als u de instelling Biometrische verificatie vereisen van de mobiele app wilt gebruiken, moet u eerst biometrie op uw Android-apparaat instellen. Als uw apparaat geen biometrie ondersteunt, kunt u de toegang tot uw Power BI-gegevens niet beveiligen met behulp van deze instelling voor de mobiele app.
>
>Als uw beheerder [extern beveiligde toegang heeft ingeschakeld](#mdm-enforcement-of-secure-access-to-your-power-bi-mobile-app) voor de mobiele app, moet u biometrie op uw apparaat instellen om toegang te krijgen tot de app, als u dit nog niet hebt gedaan. Als uw apparaat geen biometrie ondersteunt, heeft de externe instelling geen invloed op u. De toegang tot uw mobiele app blijft onbeveiligd.

## <a name="mdm-enforcement-of-secure-access-to-your-power-bi-mobile-app"></a>MDM-afdwinging van beveiligde toegang tot uw mobiele Power BI-app.

Sommige organisaties hebben beveiligingsbeleid en nalevingsvereisten die extra identificatie afdwingen voordat u toegang krijgt tot gevoelige bedrijfsgegevens.

Met de mobiele Power BI-app voor iOS wordt dit ondersteund doordat beheerders de instelling voor veilige toegang van de mobiele app kunnen beheren door de configuratie-instellingen voor de app te pushen vanuit Microsoft Intune en andere MDM-oplossingen (Mobile Device Management). Beheerders kunnen het beveiligingsbeleid voor apps gebruiken om deze instelling in te schakelen voor alle gebruikers of voor een groep gebruikers. Zie [MDM gebruiken om de mobiele Power BI-app extern te configureren](mobile-app-configuration.md#data-protection-settings-ios-and-android) voor meer informatie.

## <a name="next-steps"></a>Volgende stappen
* [MDM gebruiken om de Power mobiele Power BI-app extern te configureren](mobile-app-configuration.md)
