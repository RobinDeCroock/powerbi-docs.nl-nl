---
title: Mobiele apps configureren met Microsoft Intune
description: Lees hoe u de mobiele Power BI-apps configureert met Microsoft Intune. U vindt hier informatie over het toevoegen en implementeren van de toepassing. Er wordt ook uitgelegd hoe u Mobile Application Management-beleid opstelt om de beveiliging te regelen.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: c7d1c9a29c95cb039c90fd339f6e6a38de111916
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563699"
---
# <a name="configure-mobile-apps-with-microsoft-intune"></a>Mobiele apps configureren met Microsoft Intune

Microsoft Intune stelt organisaties in staat hun apparaten en toepassingen te beheren. De mobiele apps van Power BI voor iOS en Android zijn geïntegreerd met Intune. Deze integratie maakt het mogelijk om de toepassing te beheren op uw apparaten en om de beveiliging te regelen. Met behulp van configuratiebeleid kunt u bijvoorbeeld een pincode voor toegang vereisen, beheren hoe gegevens door de toepassing worden verwerkt en zelfs toepassingsgegevens versleutelen wanneer de app niet wordt gebruikt.

## <a name="general-mobile-device-management-configuration"></a>Algemene configuratie van beheer van mobiele apparaten

In dit artikel wordt ervan uitgegaan dat Intune correct is geconfigureerd en dat er apparaten zijn ingeschreven bij Intune. Het artikel is niet bedoeld als uitgebreide configuratiehandleiding voor Microsoft Intune. Zie [Wat is Intune?](/intune/introduction-intune/) voor meer informatie over Intune.

Microsoft Intune kan naast een MDM-oplossing (beheer van mobiele apparaten) in Microsoft 365 worden gebruikt. Als u een MDM-oplossing gebruikt, wordt het apparaat weergegeven als ingeschreven bij de MDM-oplossing, maar is het beschikbaar voor beheer in Intune.

> [!NOTE]
> Nadat u Intune hebt geconfigureerd, wordt het op de achtergrond vernieuwen van gegevens uitgeschakeld voor de mobiele Power BI-app op uw iOS- of Android-apparaat. Power BI vernieuwt de gegevens vanuit de Power BI-service op het web wanneer u de app opent.

## <a name="step-1-get-the-url-for-the-application"></a>Stap 1: De URL voor de toepassing bepalen

Voordat we de toepassing in Intune gaan maken, moeten we de URL's voor de apps vaststellen. Voor iOS kan dit via iTunes. Voor Android gebruiken we hiervoor de pagina voor de mobiele Power BI-apps.

Sla de URL op, want u hebt deze nodig wanneer we de toepassing gaan maken.

### <a name="get-ios-url"></a>URL voor iOS bepalen

Als u de URL van de app voor iOS wilt bepalen, moeten we iTunes gebruiken.

1. Open iTunes.

1. Zoek naar *Power BI*.

1. **Microsoft Power BI** wordt als het goed is vermeld onder **iPhone-apps** en **iPad-apps**. Het maakt niet uit welke u kiest, want u krijgt dezelfde URL.

1. Selecteer de vervolgkeuzelijst **Ophalen** en selecteer **Kopieer koppeling** in de vervolgkeuzelijst.

    ![URL voor app in iTunes](media/service-admin-mobile-intune/itunes-url.png)

De URL moet er als volgt uitzien: *https://itunes.apple.com/us/app/microsoft-power-bi/id929738808?mt=8* .

### <a name="get-android-url"></a>URL voor Android bepalen

U kunt de URL voor Google Play verkrijgen via de [pagina met mobiele Power BI-apps](https://powerbi.microsoft.com/mobile/). Selecteer **Download from Google Play** om naar de pagina van de app te gaan. U kunt de URL nu uit de adresbalk van de browser kopiëren. De URL moet er als volgt uitzien: *https://play.google.com/store/apps/details?id=com.microsoft.powerbim* .

## <a name="step-2-create-a-mobile-application-management-policy"></a>Stap 2: Een Mobile Application Management-beleid opstellen

Via het Mobile Application Management-beleid kunt u beveiliging afdwingen zoals het invoeren van een pincode om toegang te krijgen. U kunt een beleid opstellen in de Intune-portal.

U kunt de toepassing of het beleid eerst maken. De volgorde waarin u dit doet, is niet van belang. Ze moeten alleen beide bestaan om de implementatiestap te kunnen uitvoeren.

1. Selecteer in de Intune-portal **Beleid** > **Configuratiebeleid**.

    ![Intune-portal](media/service-admin-mobile-intune/intune-policy.png)

1. Selecteer **Toevoegen…** .

1. Onder **Software** kunt u Mobile Application Management selecteren voor Android of iOS. Om snel aan de slag te gaan, kunt u **Een aangepast beleid met de aanbevolen instellingen maken** selecteren of u kunt een aangepast beleid maken.

1. Bewerk het beleid om de beperkingen te configureren die u wilt instellen voor de toepassing.

## <a name="step-3-create-the-application"></a>Stap 3: De toepassing maken

De toepassing is een verwijzing (ook wel pakket genoemd) die in Intune wordt opgeslagen voor implementatie. We moeten een toepassing maken en verwijzen naar de URL van de app die we eerder hebben opgehaald via Google Play of iTunes.

U kunt de toepassing of het beleid eerst maken. De volgorde waarin u dit doet, is niet van belang. Ze moeten alleen beide bestaan om de implementatiestap te kunnen uitvoeren.

1. Ga naar de Intune-portal en selecteer **Apps** in het menu links.

1. Selecteer **App toevoegen**. Het onderdeel de **Software toevoegen** wordt nu gestart.

### <a name="create-for-ios"></a>Maken voor iOS

1. Selecteer **Beheerde iOS-app uit de App Store** in de vervolgkeuzelijst.

1. Voer de URL van de app uit [Stap 1](#step-1-get-the-url-for-the-application) in en selecteer **Volgende**.

    ![Configuratie van software: iOS](media/service-admin-mobile-intune/intune-add-software-ios1.png)

1. Geef waarden op voor **Uitgever**, **Naam** en **Beschrijving**. U kunt desgewenst ook een**pictogram** kiezen. **Categorie** is voor de bedrijfsportal-app. Selecteer **Volgende** als u klaar bent.

1. U kunt aangeven of u de app wilt publiceren als **Elke** (standaard), **iPad** of **iPhone**. Standaard wordt **Elke** weergegeven en dit werkt voor beide typen apparaten. De Power BI-app heeft dezelfde URL voor iPhone en iPad. Selecteer **Volgende**.

1. Selecteer **Uploaden**.

1. Als u de app niet in de lijst ziet staan, vernieuwt u de pagina: Ga naar **Overzicht** en vervolgens terug naar **Apps**.

    ![Het tabblad Apps](media/service-admin-mobile-intune/intune-add-software-ios2.png)

### <a name="create-for-android"></a>Maken voor Android

1. Selecteer **Externe koppeling** in de vervolgkeuzelijst.

1. Voer de URL van de app uit [Stap 1](#step-1-get-the-url-for-the-application) in en selecteer **Volgende**.

    ![Software instellen: Android](media/service-admin-mobile-intune/intune-add-software-android1.png)

1. Geef waarden op voor **Uitgever**, **Naam** en **Beschrijving**. U kunt desgewenst ook een**pictogram** kiezen. **Categorie** is voor de bedrijfsportal-app. Selecteer **Volgende** als u klaar bent.

1. Selecteer **Uploaden**.

1. Als u de app niet in de lijst ziet staan, vernieuwt u de pagina: Ga naar **Overzicht** en vervolgens terug naar **Apps**.

    ![Het tabblad Apps](media/service-admin-mobile-intune/intune-add-software-android2.png)

## <a name="step-4-deploy-the-application"></a>Stap 4: De toepassing implementeren

Nadat u de toepassing hebt toegevoegd, moet u deze implementeren zodat uw eindgebruikers ermee aan de slag kunnen. Dit is de stap waarin u het beleid toepast dat u hebt gemaakt met de app.

### <a name="deploy-for-ios"></a>Implementeren voor iOS

1. Selecteer de app die u hebt gemaakt op het scherm met apps. Selecteer vervolgens de koppeling **Implementatie beheren**.

    ![Implementatie beheren](media/service-admin-mobile-intune/intune-deploy-ios1.png)

1. Op het scherm **Groepen selecteren** kunt u kiezen in welke groepen u deze app wilt implementeren. Selecteer **Volgende**.

1. Op het scherm **Implementatieactie** kunt u kiezen in welke groepen u deze app wilt implementeren. Selecteer **Beschikbare installatie** of **Vereiste installatie** om de app beschikbaar te maken in de bedrijfsportal, zodat gebruikers deze op aanvraag kunnen installeren. Selecteer **Volgende** als u een keuze hebt gemaakt.

    ![Implementatieactie](media/service-admin-mobile-intune/intune-deploy-ios2.png)

1. Op het scherm **Mobile App Management** kunt u het Mobile Application Management-beleid selecteren dat we hebben gemaakt in [Stap 2](#step-2-create-a-mobile-application-management-policy). Hier wordt standaard het beleid geselecteerd dat u hebt opgesteld, als dat het enige beschikbare iOS-beleid is. Selecteer **Volgende**.

    ![Mobiele app beheren](media/service-admin-mobile-intune/intune-deploy-ios3.png)

1. Op het scherm **VPN-profiel** kunt u een beleid selecteren, als er een beleid bestaat voor uw organisatie. De standaardinstelling is **Geen**. Selecteer **Volgende**.

1. Op het scherm **Configuratie van mobiele apps** kunt u een **app-configuratiebeleid** selecteren als u dat hebt gemaakt. De standaardinstelling is **Geen**. Dit is niet vereist. Selecteer **Voltooien**.

Nadat u de app hebt geïmplementeerd, wordt op de pagina met apps **Ja** weergegeven voor Geïmplementeerd.

### <a name="deploy-for-android"></a>Implementeren voor Android

1. Selecteer de app die u hebt gemaakt op het scherm met apps. Selecteer vervolgens de koppeling **Implementatie beheren**.

    ![Implementatie beheren](media/service-admin-mobile-intune/intune-deploy-android1.png)
1. Op het scherm **Groepen selecteren** kunt u kiezen in welke groepen u deze app wilt implementeren. Selecteer **Volgende**.

1. Op het scherm **Implementatieactie** kunt u kiezen in welke groepen u deze app wilt implementeren. Selecteer **Beschikbare installatie** of **Vereiste installatie** om de app beschikbaar te maken in de bedrijfsportal, zodat gebruikers deze op aanvraag kunnen installeren. Selecteer **Volgende** als u een keuze hebt gemaakt.

    ![Implementatieactie](media/service-admin-mobile-intune/intune-deploy-android2.png)

1. Op het scherm **Mobile App Management** kunt u het Mobile Application Management-beleid selecteren dat we hebben gemaakt in [Stap 2](#step-2-create-a-mobile-application-management-policy). Hier wordt standaard het beleid geselecteerd dat u hebt opgesteld, als dat het enige beschikbare Android-beleid is. Selecteer **Voltooien**.

    ![Mobiele app beheren](media/service-admin-mobile-intune/intune-deploy-android3.png)

Nadat u de app hebt geïmplementeerd, wordt op de pagina met apps **Ja** weergegeven voor Geïmplementeerd.

## <a name="step-5-install-the-application-on-a-device"></a>Stap 5: De toepassing op een apparaat installeren

U installeert de toepassing via de *bedrijfsportal-app*. Als u de bedrijfsportal nog niet hebt geïnstalleerd, kunt u deze downloaden via de App Store van iOS of Android. U moet de referenties van uw organisatie gebruiken om u aan te melden bij de bedrijfsportal.

1. Open de bedrijfsportal-app.

1. Als de Power BI-app niet wordt weergegeven als een aanbevolen app, selecteert u **Bedrijfsapps**.

    ![Bedrijfsapps](media/service-admin-mobile-intune/intune-companyportal1.png)

1. Selecteer de Power BI-app die u hebt geïmplementeerd.

    ![Power BI-app](media/service-admin-mobile-intune/intune-companyportal2.png)

1. Selecteer **Installeren**.

    ![App installeren](media/service-admin-mobile-intune/intune-companyportal3.png)

1. Als u iOS gebruikt, wordt de app naar uw apparaat gepusht. Selecteer **Installeer** in het dialoogvenster van de push-melding.

    ![App-installatie](media/service-admin-mobile-intune/intune-companyportal5.png)

1. Nadat de app is geïnstalleerd, ziet u de status **Beheerd door uw bedrijf**. Als u toegang met een pincode hebt ingeschakeld, ziet u het volgende.

    ![Pincode invoeren](media/service-admin-mobile-intune/intune-powerbi-pin.png)

## <a name="next-steps"></a>Volgende stappen

[Mobile Application Management-beleid configureren en implementeren in de Microsoft Intune-console](/intune/app-protection-policies/)  

[Power BI-apps voor mobiele apparaten](../consumer/mobile/mobile-apps-for-mobile-devices.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)  
