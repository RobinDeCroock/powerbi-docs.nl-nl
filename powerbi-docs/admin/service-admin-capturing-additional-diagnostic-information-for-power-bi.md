---
title: Diagnostische gegevens vastleggen voor ondersteuning
description: Instructies voor het hand matig verzamelen van diagnostische gegevens van de Power BI-service. Stuur deze informatie naar ondersteuning om hen te helpen bij het oplossen van problemen.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/21/2021
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 59e434d571c5b8d10c944bc385fb4e18ed89963c
ms.sourcegitcommit: 84f0e7f31e62cae3bea2dcf2d62c2f023cc2d404
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/26/2021
ms.locfileid: "98781204"
---
# <a name="capture-diagnostic-information-from-the-power-bi-service"></a>Diagnostische gegevens vastleggen vanuit de Power BI-service

Voordat u contact opneemt met Microsoft Ondersteuning voor hulp bij een probleem dat u met de Power BI-service hebt, kunt u bestanden verzamelen waarmee het probleem kan worden opgelost. U wordt aangeraden om een browser tracering uit te voeren vanuit uw browser sessie. Een browser tracering is een diagnostisch bestand dat belang rijke informatie kan geven over wat er gebeurt in de Power BI-service wanneer het probleem optreedt.

Power BI beheerders kunnen de Help- **en ondersteunings** ervaring in het [Power platform-beheer centrum](https://admin.powerplatform.microsoft.com/) gebruiken om zelf hulp oplossingen te verkrijgen en contact op te nemen met de ondersteuning. De diagnostische bestanden die u kunt verzamelen met behulp van de onderstaande stappen, kunnen worden gekoppeld aan uw ondersteunings aanvraag om te helpen bij het oplossen van problemen. Zie [Power bi ondersteunings opties](service-support-options.md)voor meer ondersteunings opties.

Als u een browser tracering en andere sessie gegevens wilt verzamelen, volgt u de onderstaande stappen voor de browser die u gebruikt.

## <a name="collect-a-browser-trace"></a>Een browser tracering verzamelen

> [!IMPORTANT]
>Meld u aan bij de [Power bi-service](https://app.powerbi.com) *voordat* u begint met het verzamelen van informatie over de browser tracering, ongeacht de browser die u gebruikt. Deze stap is belang rijk om ervoor te zorgen dat de tracerings gegevens geen gevoelige informatie bevatten met betrekking tot uw aanmelding.

#### <a name="google-chrome-or-microsoft-edge"></a>[Google Chrome of micro soft Edge](#tab/google-chrome-or-microsoft-edge)

Google Chrome en micro soft Edge (chroom) zijn beide gebaseerd op het [open-source-project](https://www.chromium.org/Home)van Chrome. De volgende stappen laten zien hoe u de hulpprogram ma's voor ontwikkel aars gebruikt, die vergelijkbaar zijn in de twee browsers. Zie [Chrome devtools](https://developers.google.com/web/tools/chrome-devtools) en [micro soft Edge (chroom) Ontwikkelhulpprogramma's](/microsoft-edge/devtools-guide-chromium)voor meer informatie.

1. Nadat u zich hebt aangemeld, drukt u op F12 op het toetsen bord. Of Selecteer in micro soft Edge **instellingen en meer (...)**  >  **Meer hulpprogram ma's**  >  **Ontwikkel hulpprogramma's**. Selecteer in Google Chrome het menu voor **het aanpassen en beheren van Google Chrome** :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/chromium-icon-settings.png" alt-text="Google Chrome-instellingen." border="false"::: > **Meer hulpprogram ma's**  >  **Ontwikkel hulpprogramma's**.
1. Bereid u voor op het verzamelen van de browser tracering door tracerings opties in te stellen. U kunt ook alle informatie die is verzameld, uitschakelen voordat u het probleem opnieuw produceert. De browser houdt standaard alleen tracerings informatie bij voor de pagina die momenteel wordt geladen. Volg deze stappen om de browser zo in te stellen dat alle tracerings gegevens worden bewaard, zelfs als uw reproduceren naar meer dan één pagina gaat:
    1. Selecteer in het venster **ontwikkel hulpprogramma's** het tabblad **netwerk** . Selecteer vervolgens **logboek bewaren**.
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-preserve-log.png" alt-text="Hulp middelen voor ontwikkel aars met het tabblad netwerk en het selectief logboek bestand behouden." :::

     2. Selecteer het tabblad **console** en selecteer vervolgens **instellingen**  >  **logboek behouden**. 
   
           :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-console-settings.png" alt-text="Hulp middelen voor ontwikkel aars met het tabblad console en geselecteerd logboek bewaren." :::

        Selecteer **instellingen** opnieuw om de **console-instellingen** te sluiten.

3. Vervolgens stopt en wist u alle opnamen die worden uitgevoerd. Selecteer het tabblad **netwerk** , selecteer **netwerk logboek opname stoppen** en vervolgens **wissen**.
   
   :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-stop-recording.png" alt-text="Hulp middelen voor ontwikkel aars met het tabblad netwerk en de optie opname opties stoppen en wissen." :::
     
2. Nu kunt u het probleem dat u in de Power BI-servicete, reproduceren. Als u wilt beginnen, selecteert u in **ontwikkel hulpprogramma's** het tabblad **netwerk** . Selecteer **netwerk logboek opnemen**.

    > [!IMPORTANT]
    >Vernieuw de browser pagina in de Power BI-service voordat u begint met het reproduceren van het probleem, zodat traceringen correct worden vastgelegd.

   Reproduceer de stappen die hebben geleid tot het probleem waarvoor u hulp nodig hebt.

     :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-record-network-log.png" alt-text="Hulp middelen voor ontwikkel aars met tabblad netwerk en record netwerk logboek geselecteerd." :::

    Wanneer u het probleem reproduceert, ziet u uitvoer die vergelijkbaar is met de volgende afbeelding in het venster **hulpprogram ma's voor ontwikkel aars** .

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-output.png" alt-text="Ontwikkel hulpprogramma's met het tabblad netwerk met de sessie-uitvoer." :::
    
3. Nadat het probleem gedrag is opgetreden, moet u de logboek bestanden opslaan en koppelen aan uw ondersteunings aanvraag.
    1. Als u het netwerk logboek wilt exporteren, selecteert u in **hulp middelen voor ontwikkel aars** het tabblad **netwerk** . Selecteer **Stop opnemen netwerk logboek**. Selecteer vervolgens **exporteren har...** en sla het bestand op.

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-export-har.png" alt-text="Hulp middelen voor ontwikkel aars met het tabblad netwerk, stoppen met opnemen en exporteren van HAR-opties geselecteerd." :::

    2. Als u de uitvoer van de console wilt exporteren, selecteert u in **ontwikkel hulpprogramma's** het tabblad **console** . Klik met de rechter muisknop op een weer gegeven bericht, selecteer **Opslaan als...** en sla de uitvoer van de console op in een tekst bestand.
    
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-save-as.png" alt-text="Hulp middelen voor ontwikkel aars met geselecteerd tabblad en opslaan als optie weer gegeven." :::

   Pak het opgeslagen HAR-bestand, de console-uitvoer en de scherm opname in een gecomprimeerde indeling, zoals. zip, en koppel het bestand aan uw ondersteunings aanvraag.

#### <a name="apple-safari"></a>[Apple Safari](#tab/apple-safari)

De volgende stappen laten zien hoe u de hulpprogram ma's voor ontwikkel aars in Apple Safari kunt gebruiken. Zie [overzicht van Safari Ontwikkelhulpprogramma's](https://support.apple.com/guide/safari-developer/safari-developer-tools-overview-dev073038698/11.0/mac)voor meer informatie.

1. Nadat u zich hebt aangemeld, schakelt u de ontwikkel hulpprogramma's in Apple Safari in:
    1. Selecteer in de paginakop tekst **Safari**  >  **voor keuren**.
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-preferences.png" alt-text="Apple Safari-menu met voor keuren geselecteerd." :::

    2. Selecteer **Geavanceerd** en selecteer vervolgens het **menu ontwikkelen weer geven in de menu balk** om de ontwikkel hulpprogramma's in te scha kelen.
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-show-develop-menu.png" alt-text="Menu Geavanceerd van Safari met het menu ontwikkelen in de menu balk geselecteerd." :::

2. Vervolgens stelt u opties in de web- **Inspector** in om ervoor te zorgen dat uw browser alle tracerings gegevens kan bijhouden. De browser houdt standaard alleen tracerings informatie bij voor de pagina die momenteel wordt geladen. Deze instellingen zorgen ervoor dat tracerings gegevens worden verzameld, zelfs als uw reproduceren naar meer dan een pagina moet gaan.

    1. Selecteer **ontwikkel**  >  **weer geven Web-Inspector**.
    
        :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-web-inspector.png" alt-text="Het menu ontwikkelen met de optie webcontrole weer geven geselecteerd." :::

    2. Logboek voor **netwerk**  >  **behoud** selecteren
       
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-network-preserve-log.png" alt-text="Het menu webinspector met het onderdeel Netwerk en Bewaar logboek is geselecteerd." :::

    1. Selecteer logboek van **console**  >  **behouden**
   
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-console-preserve-log.png" alt-text="Het menu voor Webitems met de console en het logboek bewaren geselecteerd." :::

3. Nadat de opties zijn ingesteld, selecteert u **netwerk**  >  **wissen netwerk items** om ervoor te zorgen dat uw Logboeken alleen details over het probleem reproduceren bevatten.

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-clear-network-items.png" alt-text="Het menu voor Webitems met netwerk en netwerk items wissen geselecteerd." :::


4. Nu bent u klaar om het probleem te reproduceren. 
    > [!IMPORTANT]
    >Vernieuw de browser pagina in de Power BI-service voordat u begint met het reproduceren van het probleem, zodat traceringen correct worden vastgelegd.

    Door loop de stappen om het probleem te reproduceren dat u hebt. Wanneer u het probleem reproduceert, ziet u uitvoer die vergelijkbaar is met de volgende afbeelding in het **netwerk** venster.

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-session-output.png" alt-text="Netwerk venster waarin de voorbeeld uitvoer wordt weer gegeven." :::

5. Nadat het probleem gedrag is opgetreden, moet u de logboek bestanden opslaan en koppelen aan uw ondersteunings aanvraag.

    1. Als u het netwerk logboek wilt exporteren, selecteert u op het tabblad **netwerk** de optie **exporteren** en slaat u het bestand op in har-indeling.

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-export.png" alt-text="Tabblad netwerk waarvoor de optie exporteren is geselecteerd." :::

    2. Als u de uitvoer van de console wilt exporteren, selecteert u in het deel venster hulpprogram ma's **ontwikkelen** het tabblad **console** en vouwt u het venster uit. Plaats de cursor aan het begin van de console-uitvoer en sleep en selecteer de volledige inhoud van de uitvoer. Gebruik opdracht-C om de uitvoer te kopiëren en op te slaan in een tekst bestand.

   Pak het opgeslagen HAR-bestand, de console-uitvoer en de scherm opname in een gecomprimeerde indeling, zoals. zip, en koppel het bestand aan uw ondersteunings aanvraag.

#### <a name="firefox"></a>[Firefox](#tab/firefox)

De volgende stappen laten zien hoe u de hulpprogram ma's voor ontwikkel aars in Firefox kunt gebruiken. Zie voor meer informatie [Firefox-ontwikkel hulpprogramma's](https://developer.mozilla.org/docs/Tools).

1. Nadat u zich hebt aangemeld, drukt u op F12 op het toetsen bord. Of Selecteer in Firefox menu **Openen menu** :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-menu.png" alt-text="pictogram Firefox." border="false"::: > **Webontwikkelaar**  >  **Scha kelen tussen Hulpprogram ma's**. De hulpprogram ma's worden onder aan het scherm weer gegeven.

1. Vervolgens stelt u opties in de **Inspector** in om ervoor te zorgen dat uw browser alle tracerings gegevens kan bijhouden. De browser houdt standaard alleen tracerings informatie bij voor de pagina die momenteel wordt geladen. Deze instellingen zorgen ervoor dat tracerings gegevens worden verzameld, zelfs als uw reproduceren naar meer dan een pagina moet gaan.

    1. Selecteer het tabblad **netwerk** in het **Inspector** -venster. Selecteer vervolgens **Logboeken persistent** maken.
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-network-persist-logs.png" alt-text="Inspector-hulpprogram ma's met het tabblad netwerk en persistente logboeken geselecteerd." :::

     2. Selecteer het tabblad **console** en selecteer vervolgens **console-instellingen**  >  **persistente logboeken**. 
   
           :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-console-persist-logs.png" alt-text="Inspector-hulpprogram ma's met console tabblad en persistente logboeken geselecteerd." :::

3. Nadat de opties zijn ingesteld, wist u de opname wordt uitgevoerd. Selecteer het tabblad **netwerk** en **Schakel het selectie vakje uit**.
   
   :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-stop-recording.png" alt-text="Hulp middelen voor ontwikkel aars met het tabblad netwerk en de optie opname opties stoppen en wissen." :::
     
2. Nu bent u klaar om het probleem te reproduceren. 
    > [!IMPORTANT]
    >Vernieuw de browser pagina in de Power BI-service voordat u begint met het reproduceren van het probleem, zodat traceringen correct worden vastgelegd.
 
    Door loop de stappen om het probleem te reproduceren dat u hebt.
    
3. Nadat het probleem gedrag is opgetreden, moet u de logboek bestanden opslaan en koppelen aan uw ondersteunings aanvraag.
    1. Als u het netwerk logboek wilt exporteren, selecteert u **netwerk**  >  **har exporteren/importeren** en slaat u vervolgens **alles op als har**.

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-save-har.png" alt-text="Tabblad netwerk met HAR-menu exporteren/importeren en alle geselecteerde opties opslaan." :::

    2. Als u de console-uitvoer wilt exporteren, selecteert u het tabblad **console** . Klik met de rechter muisknop op een weer gegeven bericht, selecteer **zicht bare berichten exporteren naar** en sla de console-uitvoer op in een tekst bestand.
    
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-export-visible-messages.png" alt-text="Tabblad console geselecteerd en weer gegeven optie voor het exporteren van zicht bare berichten." :::

   Pak het opgeslagen HAR-bestand, de console-uitvoer en de scherm opname in een gecomprimeerde indeling, zoals. zip, en koppel het bestand aan uw ondersteunings aanvraag.

---

Nadat u de diagnostische bestanden hebt verzameld, koppelt u deze aan uw ondersteunings aanvraag om de ondersteunings technicus te helpen bij het oplossen van uw probleem. Het HAR-bestand bevat alle informatie over netwerk aanvragen tussen het browser venster en het Power BI-service, met inbegrip van:

* De activiteit-id's voor elke aanvraag.

* De exacte tijdstempel voor elke aanvraag.

* Eventuele foutgegevens die naar de client zijn geretourneerd.

Deze tracering bevat ook de gegevens die worden gebruikt voor het vullen van de visuele elementen die op het scherm worden weergegeven.

## <a name="next-steps"></a>Volgende stappen

* [Status van de Power BI-service in Microsoft 365 bijhouden](service-admin-health.md)
* [Meldingen over onderbrekingen van de service inschakelen](service-interruption-notifications.md)
* [Word lid van de Power BI-community](https://community.powerbi.com/)
