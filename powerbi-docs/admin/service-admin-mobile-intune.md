---
title: Mobiele apps configureren met Microsoft Intune
description: Lees hoe u de mobiele Power BI-apps configureert met Microsoft Intune. U vindt hier informatie over het toevoegen en implementeren van de toepassing. Er wordt ook uitgelegd hoe u Mobile Application Management-beleid opstelt om de beveiliging te regelen.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/25/2020
LocalizationGroup: Administration
ms.openlocfilehash: 6ca9b241fe2d6f2914a603e722f2dd2c216e05df
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408775"
---
# <a name="configure-mobile-apps-with-microsoft-intune"></a>Mobiele apps configureren met Microsoft Intune

Microsoft Intune stelt organisaties in staat hun apparaten en toepassingen te beheren. De mobiele apps van Power BI voor iOS en Android zijn geïntegreerd met Intune. Deze integratie maakt het mogelijk om de toepassing te beheren op uw apparaten en om de beveiliging te regelen. Met behulp van configuratiebeleid kunt u bijvoorbeeld een pincode voor toegang vereisen, beheren hoe gegevens door de toepassing worden verwerkt en zelfs toepassingsgegevens versleutelen wanneer de app niet wordt gebruikt.

Met de mobiele app van Microsoft Power BI kunt u toegang krijgen tot uw belangrijke bedrijfsgegevens. U kunt uw dashboards en rapporten met betrekking tot de bedrijfsgegevens van alle beheerde apparaten en apps van uw organisatie weergeven en ermee werken. Zie [Beveiligde Microsoft Intune-apps](/intune/apps/apps-supported-intune-apps) voor meer informatie over ondersteunde Intune-apps.

## <a name="general-mobile-device-management-configuration"></a>Algemene configuratie van beheer van mobiele apparaten

In dit artikel wordt ervan uitgegaan dat Intune correct is geconfigureerd en dat er apparaten zijn ingeschreven bij Intune. Het artikel is niet bedoeld als uitgebreide configuratiehandleiding voor Microsoft Intune. Zie [Wat is Intune?](/intune/introduction-intune/) voor meer informatie over Intune.

Microsoft Intune kan naast een MDM-oplossing (beheer van mobiele apparaten) in Microsoft 365 worden gebruikt. Als u een MDM-oplossing gebruikt, wordt het apparaat weergegeven als ingeschreven bij de MDM-oplossing, maar is het beschikbaar voor beheer in Intune.

Voordat eindgebruikers de Power BI-app op hun apparaten kunnen gebruiken, moet een Intune-beheerder de app aan Intune toevoegen en de app ook toewijzen aan eindgebruikers.

> [!NOTE]
> Nadat u Intune hebt geconfigureerd, wordt het op de achtergrond vernieuwen van gegevens uitgeschakeld voor de mobiele Power BI-app op uw iOS- of Android-apparaat. Power BI vernieuwt de gegevens vanuit de Power BI-service op het web wanneer u de app opent.

## <a name="step-1-add-the-power-bi-app-to-intune"></a>Stap 1: De Power BI-app toevoegen aan Intune

Maak gebruik van de in de volgende onderwerpen opgegeven stappen om de Power BI-app toe te voegen aan Intune:
- [iOS Store-apps toevoegen aan Microsoft Intune](/intune/apps/store-apps-ios)
- [Android Store-apps aan Microsoft Intune toevoegen](/intune/apps/store-apps-android)

## <a name="step-2-assign-the-app-to-your-end-users"></a>Stap 2: De app aan uw eindgebruikers toewijzen

Nadat u de Power BI-app aan Microsoft Intune hebt toegevoegd, kunt u de app toewijzen aan gebruikers en apparaten. Het is belangrijk te weten dat u een app aan een apparaat kunt toewijzen, ongeacht of het apparaat wordt beheerd door Intune.

Maak gebruik van de in [Apps toewijzen aan groepen met Microsoft Intune](/intune/apps/apps-deploy) opgegeven stappen om de Power BI-app toe te wijzen aan gebruikers en apparaten.

## <a name="step-3-create-and-assign-app-protection-policies"></a>Stap 3: App-beveiligingsbeleid maken en toewijzen

Beleidsregels voor de beveiliging van apps (APP's) zijn regels die ervoor zorgen dat de bedrijfsgegevens die zijn opgenomen in een app, veilig of binnen de app blijven. Een beleidsregel kan een regel zijn die wordt afgedwongen wanneer de gebruiker bedrijfsgegevens probeert te openen of te verplaatsen, of een reeks acties die zijn verboden of worden gecontroleerd wanneer de gebruiker zich in de app bevindt. Een beheerde app is een app waarop app-beveiligingsbeleid is toegepast en die door Intune kan worden beheerd.

Met het beveiligingsbeleid voor MAM-apps (Mobile Application Management) kunt u de gegevens van uw organisatie beheren en beveiligen in een toepassing. Met MAM zonder registratie (MAM-WE) kunt u op bijna elk apparaat, inclusief persoonlijke apparaten in BYOD-scenario's (Bring-Your-Own-Device), een werk- of schoolgerelateerde app beheren die gevoelige gegevens bevat. Zie [Overzicht van beleid voor app-beveiliging](/intune/apps/app-protection-policy) voor meer informatie.

Als u beveiligingsbeleid voor apps wilt maken en toewijzen voor de Power BI-app, gebruikt u de in [Beveiligingsbeleid voor apps maken en toewijzen](/intune/apps/app-protection-policies) opgegeven stappen.

## <a name="step-4-use-the-application-on-a-device"></a>Stap 4: De toepassing op een apparaat inzetten

Beheerde apps zijn apps die door het ondersteuningsteam van het bedrijf kunnen worden ingesteld om de bedrijfsgegevens te beveiligen die toegankelijk zijn in de app. Wanneer u bedrijfsgegevens in een beheerde app op uw apparaat opent, merkt u wellicht dat de app iets anders werkt dan u verwacht. Zo kunt u beveiligde bedrijfsgegevens mogelijk niet kopiëren en plakken of op bepaalde locaties opslaan.

Raadpleeg de stappen in de volgende artikelen voor meer informatie over hoe uw eindgebruikers de Power BI-app op hun apparaat kunnen gebruiken:
- [Beheerde apps op uw iOS-apparaat gebruiken](/intune-user-help/use-managed-apps-on-your-device-ios#how-do-i-get-managed-apps)
- [Beheerde apps op uw Android-apparaat gebruiken](/intune-user-help/use-managed-apps-on-your-device-android)

## <a name="next-steps"></a>Volgende stappen

[App-beveiligingsbeleid maken en toewijzen](/intune/app-protection-policies) 

[Power BI-apps voor mobiele apparaten](../consumer/mobile/mobile-apps-for-mobile-devices.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)