---
title: Gegevensmeldingen instellen in de mobiele Power BI-apps
description: Leer hoe u meldingen instelt in de mobiele Power BI-apps, zodat u wordt gewaarschuwd als de wijzigingen van gegevens in een dashboard de door u ingestelde beperkingen overschrijden.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 12/11/2019
ms.openlocfilehash: 4e9820b8ebff411434d9d6c408f36a36a644ea9d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417998"
---
# <a name="set-data-alerts-in-the-power-bi-mobile-apps"></a>Gegevensmeldingen instellen in de mobiele Power BI-apps
Van toepassing op:

| ![iPhone](./media/mobile-set-data-alerts-in-the-mobile-apps/iphone-logo-50-px.png) | ![iPad](./media/mobile-set-data-alerts-in-the-mobile-apps/ipad-logo-50-px.png) | ![Android-telefoon](./media/mobile-set-data-alerts-in-the-mobile-apps/android-phone-logo-50-px.png) | ![Android-tablet](./media/mobile-set-data-alerts-in-the-mobile-apps/android-tablet-logo-50-px.png) | ![Windows 10-apparaat](./media/mobile-set-data-alerts-in-the-mobile-apps/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhones |iPads |Android-telefoons |Android-tablets |Windows 10-apparaten |

U kunt meldingen voor dashboards instellen in de mobiele Power BI-apps en in de Power BI-service. Door middel van meldingen wordt u gewaarschuwd als wijzigingen aan de gegevens in een tegel de limieten overschrijden die u hebt ingesteld. Meldingen worden gebruikt voor tegels met een enkel getal, zoals kaarten en meters, maar niet voor het streamen van gegevens. U kunt gegevensmeldingen instellen voor uw mobiele apparaat en deze zien in de Power BI-service, en vice versa. Alleen u ziet de gegevensmeldingen die u hebt ingesteld, zelfs als u een dashboard of een momentopname van een tegel deelt.

U kunt waarschuwingen instellen voor tegels als u over de Power BI Pro-licentie beschikt of als het gedeelde dashboard zich in een Premium-capaciteit bevindt. 

> [!WARNING]
> Gegevensgestuurde meldingen bieden informatie over uw gegevens. Als uw apparaat wordt gestolen, wordt aangeraden de Power BI-service te gebruiken om alle gegevensgestuurde meldingsregels uit te schakelen. 
> 
> Meer informatie over het [beheren van gegevensmeldingen in de Power BI-service](../../create-reports/service-set-data-alerts.md).
> 
> 

## <a name="data-alerts-on-an-iphone-or-ipad"></a>Gegevensmeldingen op een iPhone of iPad
### <a name="set-an-alert-on-an-iphone-or-ipad"></a>Een melding instellen op een iPhone of iPad
1. Tik op een getal- of metertegel in een dashboard om deze te openen in de focusmodus.  
   
   ![Schermopname van een dashboard met de metertegel in de focusmodus.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual.png)
2. Tik op het belpictogram :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-icon.png" border="false"::: om een melding toe te voegen.  
3. Tik op **Meldingsregel toevoegen**.
   
   ![Schermopname van de waarschuwingsregel zonder ingestelde waarschuwingen.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-alert-rule.png)
4. Kies ervoor om meldingen boven of onder een bepaalde waarde te ontvangen en stel vervolgens de waarde in.
   
   ![Schermopname van de waarschuwingsinstellingen met de titel en waarde van de waarschuwing die u wilt instellen](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-set-alert-threshold.png)
5. Bepaal of per uur of per dag meldingen wilt ontvangen, en of u ook een e-mailbericht wilt ontvangen wanneer u de melding krijgt.
   
   > [!NOTE]
   > U ontvangt niet elk uur of elke dag meldingen, tenzij de gegevens daadwerkelijk zijn vernieuwd in die tijd.
   > 
   > 
6. U kunt de titel van de melding ook wijzigen.
7. Tik op **Opslaan**.
8. Eén tegel kan meldingen hebben voor waarden zowel boven als beneden bepaalde drempelwaarden. Tik in **Meldingen beheren** op **Meldingsregel toevoegen**.
   
   ![Schermopname van de waarschuwing voor beheer met een aanwijzer naar het toevoegen van een waarschuwingsregel.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-another-alert-rule.png)

### <a name="manage-alerts-on-your-iphone-or-ipad"></a>Meldingen beheren op uw iPhone of iPad
U kunt afzonderlijke meldingen beheren op uw mobiele apparaat of [alle meldingen beheren in de Power BI-service](../../create-reports/service-set-data-alerts.md).

1. Tik in een dashboard op een getal- of metertegel met een melding.  
   
   ![Schermopname van het dashboard van een iPhone of iPad met de nummertegel die een waarschuwing bevat.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual_has_alert.png)

2. Tik op het belpictogram :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-has-alert-icon.png" border="false":::.  
3. Tik op de naam van de melding om deze te bewerken, tik op de schuifregelaar om e-mailmeldingen uit te schakelen of tik op de prullenbak om de melding te verwijderen.
   
    ![Schermopname van een waarschuwing, wijzend naar de naam van de waarschuwing, prullenbak voor verwijdering van de waarschuwing en schuifregelaar om de waarschuwing uit te schakelen.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-edit-delete-alert.png)

## <a name="data-alerts-on-an-android-device"></a>Gegevensmeldingen op een Android-apparaat
### <a name="set-an-alert-on-an-android-device"></a>Een melding instellen op een Android-apparaat
1. Tik in een Power BI-dashboard op een getal- of metertegel om deze te openen.  
2. Tik op het belpictogram :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-alert-icon.png" border="false"::: om een melding toe te voegen.  
   
   ![Schermopname van het dashboard van een Android-apparaat met de nummertegel die een waarschuwing bevat.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tap-alert.png)
3. Tik op het plusteken (+).
   
   ![Schermopname van Waarschuwingen beheren met een aanwijzer naar het pluspictogram.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-plus-alert.png)
4. Kies ervoor om meldingen boven of onder een bepaalde waarde te ontvangen en voer vervolgens de waarde in.
   
   ![Schermopname van de waarschuwingsinstelling met aanwijzers naar Opslaan en Gereed.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tablet-set-alert-condition.png)
5. Tik op **Gereed**.
6. Bepaal of per uur of per dag meldingen wilt ontvangen, en of u ook een e-mailbericht wilt ontvangen wanneer u de melding krijgt.
   
   > [!NOTE]
   > U ontvangt niet elk uur of elke dag meldingen, tenzij de gegevens daadwerkelijk zijn vernieuwd in die tijd.
   > 
   > 
7. U kunt de titel van de melding ook wijzigen.
8. Tik op **Opslaan**.

### <a name="manage-alerts-on-an-android-device"></a>Meldingen beheren op een Android-apparaat
U kunt afzonderlijke meldingen beheren in de mobiele Power BI-app of [alle meldingen beheren in de Power BI-service](../../create-reports/service-set-data-alerts.md).

1. Tik in een dashboard op een kaart- of metertegel met een melding.  
2. Tik op het effen belpictogram :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-filled-alert-bell.png" border="false":::.  
3. Tik op de melding om een waarde te wijzigen of om de melding uit te schakelen.
   
    ![Schermopname van de tegel Waarschuwing beheren met het pluspictogram om een waarschuwing toe te voegen.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-manage-alerts.png)
4. Tik op het plusteken (+) om een nieuwe melding toe te voegen aan de dezelfde tegel.
5. Als u de waarschuwing helemaal wilt verwijderen, tikt u op het prullenbakpictogram ![Prullenbakpictogram](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-delete-alert-icon.png).

## <a name="data-alerts-on-a-windows-device"></a>Gegevensmeldingen op een Windows-apparaat

>[!NOTE]
>Power BI-ondersteuning voor mobiele apps voor **telefoons met Windows 10 Mobile** wordt stopgezet op 16 maart 2021. [Meer informatie](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

### <a name="set-data-alerts-on-a-windows-device"></a>Gegevensmeldingen instellen op een Windows-apparaat
1. Tik op een getal- of metertegel in een dashboard om deze te openen.  
2. Tik op het belpictogram :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-off.png" border="false"::: om een melding toe te voegen.  
   
   ![Schermopname van het dashboard van een Windows-apparaat met de nummertegel die een waarschuwing bevat.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-tap-alert.png)
3. Tik op het plusteken (+).
   
   ![Schermopname van Waarschuwingen beheren zonder ingestelde waarschuwingen.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-no-alerts-yet.png)
4. Kies ervoor om meldingen boven of onder een bepaalde waarde te ontvangen en voer vervolgens de waarde in.
   
   ![Schermopname van de waarschuwingsinstellingen met de vermeldingen om de waarschuwing te bewerken.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-set-alert.png)
5. Bepaal of per uur of per dag meldingen wilt ontvangen, en of u ook een e-mailbericht wilt ontvangen wanneer u de melding krijgt.
   
   > [!NOTE]
   > U ontvangt niet elk uur of elke dag meldingen, tenzij de gegevens daadwerkelijk zijn vernieuwd in die tijd.
   > 
   > 
6. U kunt de titel van de melding ook wijzigen.
7. Tik op het vinkje.
8. Eén tegel kan meldingen hebben voor waarden zowel boven als beneden bepaalde drempelwaarden. Tik in **Meldingen beheren** op het plusteken (+).
   
   ![Schermopname van Waarschuwing beheren met het pluspictogram om een waarschuwing toe te voegen.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)

### <a name="manage-alerts-on-a-windows-device"></a>Meldingen beheren op een Windows-apparaat
U kunt afzonderlijke meldingen beheren in de mobiele Power BI-app of [alle meldingen beheren in de Power BI-service](../../create-reports/service-set-data-alerts.md).

1. Tik in een dashboard op een kaart- of metertegel met een melding.  
2. Tik op het belpictogram :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-on.png" border="false":::.  
   
   ![Schermopname van het dashboard met de nummertegel die een waarschuwing bevat.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-has-alerts.png)
3. Tik op de melding om een waarde te wijzigen of om de melding uit te schakelen.
   
    ![Schermopname van Waarschuwing beheren met het pluspictogram om een waarschuwing toe te voegen.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)
4. Als u de melding helemaal wilt verwijderen, klikt u met de rechtermuisknop of tikt u op de melding en houdt deze vast. Klik of tik vervolgens op **Verwijderen**.

## <a name="receiving-alerts"></a>Meldingen ontvangen
U ontvangt meldingen in het [Meldingencentrum](mobile-apps-notification-center.md) van Power BI op uw mobiele apparaat of in de Power BI-service. Hier ontvangt u ook meldingen over nieuwe dashboards die iemand met u heeft gedeeld.

Gegevensbronnen worden vaak zo ingesteld dat ze dagelijks worden vernieuwd. Soms worden ze vaker vernieuwd. Als de gegevens in het dashboard worden vernieuwd en deze bijgehouden gegevens een van de ingestelde drempelwaarden bereiken, vinden er een aantal dingen plaats.

1. Power BI controleert of het langer dan 24 uur geleden is (afhankelijk van de door u geselecteerde optie) sinds de laatste melding is verzonden.
   
   U ontvangt elk uur of elke 24 uur een melding zolang de gegevens de drempelwaarde overschrijden.
2. Als de melding zo is ingesteld dat u een e-mail ontvangt, vindt u iets soortgelijks als hieronder in uw Postvak IN.
   
   ![Schermopname van een e-mailmelding met de waarschuwing.](media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alerts-email.png)
3. Power BI voegt een bericht toe aan uw [Meldingencentrum](mobile-apps-notification-center.md) en voegt een gele punt toe aan het klokpictogram :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alert-tile-notification-icon.png" border="false"::: op de titelbalk (iOS en Android) of aan de algemene navigatieknop ![algemene navigatieknop](./media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-global-nav-button.png) (Windows 10-apparaten).


4. Tik op het klokpictogram :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alert-tile-notification-icon.png" border="false"::: of de algemene navigatieknop ![algemene navigatieknop](./media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-global-nav-button.png) voor het [openen van uw **Meldingencentrum**](mobile-apps-notification-center.md) en details van de melding te zien.
   
     

> [!NOTE]
> Meldingen werken alleen voor gegevens die zijn vernieuwd. Als gegevens worden vernieuwd, controleert Power BI of er een melding voor die gegevens is ingesteld. Als de gegevens een drempelwaarde voor de melding hebben bereikt, wordt er een melding geactiveerd.
> 
> 

## <a name="tips-and-troubleshooting"></a>Tips en problemen oplossen
* Meldingen worden momenteel niet ondersteund voor Bing-tegels of kaarttegels met datum-/tijdmetingen.
* Meldingen werken alleen met numerieke gegevens.
* Meldingen werken alleen voor gegevens die zijn vernieuwd. Ze werken niet met statische gegevens.
* Meldingen werken niet met tegels die streaminggegevens bevatten.

## <a name="next-steps"></a>Volgende stappen
* [Meldingen beheren in de Power BI-service](../../create-reports/service-set-data-alerts.md)
* [Meldingencentrum van Power BI voor mobiel](mobile-apps-notification-center.md)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)