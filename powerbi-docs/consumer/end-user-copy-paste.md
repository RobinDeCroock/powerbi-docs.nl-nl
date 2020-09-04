---
title: Een visualisatie kopiëren en plakken in de Power BI-service
description: Een visualisatie kopiëren en plakken in de Power BI-service
author: mihart
ms.reviewer: maggie.tsang
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 08/25/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 6e1850e281c58bd89597af2bbd9ade0a769071ae
ms.sourcegitcommit: 1aaa742c239a3119cdaad698be5a7553b68801fa
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/27/2020
ms.locfileid: "89040242"
---
# <a name="copy-a-visual-as-an-image-to-your-clipboard"></a>Een visual als afbeelding naar uw klembord kopiëren

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]

Hebt u ooit een afbeelding uit een Power BI-rapport of dashboard willen delen? Nu kunt u de visual kopiëren en plakken in een willekeurige andere toepassing die plakken ondersteunt. 

Wanneer u een statische afbeelding van een visual kopieert, krijgt u een kopie van de visual, voorzien van de metagegevens. Dit omvat:
* terugkoppeling naar het Power BI-rapport of dashboard
* titel van het rapport of dashboard
* kennisgeving of de afbeelding vertrouwelijke informatie bevat
* tijdstempel van moment waarop het laatst is bijgewerkt
* filters die op de visual zijn toegepast

### <a name="copy-from-a-dashboard-tile"></a>Kopiëren vanaf een dashboardtegel

1. Navigeer naar het dashboard vanaf waar u inhoud wilt kopiëren.

2. In de rechterbovenhoek van de visual selecteert u **Meer acties(...)** en kiest u **Visual als afbeelding kopiëren**. 

    ![Visual kopiëren als afbeelding wordt weergegeven in vervolgkeuzelijst](media/end-user-copy-paste/power-bi-copy-dashboard.png)

3. Wanneer het dialoogvenster **De visual is gereed om te kopiëren** wordt weergegeven, selecteert u **Naar het klembord kopiëren**.

    ![dialoogvenster met de optie Naar het klembord kopiëren](media//end-user-copy-paste/power-bi-copied.png)

4. Nadat uw visual gekopieerd is, plakt u deze in een andere toepassing met **Ctrl + V** of door met de **rechtermuisknop** > **Plakken** te klikken. In de onderstaande schermopname is de visual in Microsoft Word geplakt. 

    ![Visual geplakt in Microsoft Word](media//end-user-copy-paste/power-bi-paste-word.png)

### <a name="copy-from-a-report-visual"></a>Kopiëren vanuit een rapportvisual 

1. Navigeer naar het rapport van waaruit u inhoud wilt kopiëren.

2. In de rechterbovenhoek van de visual selecteert u het pictogram voor **Visual als afbeelding kopiëren**. 

    ![Weergaven van het pictogram Visual als afbeelding kopiëren](media/end-user-copy-paste/power-bi-copy-icon.png)

3. Wanneer het dialoogvenster **De visual is gereed om te kopiëren** wordt weergegeven, selecteert u **Naar het klembord kopiëren**.

    ![dialoogvenster met de optie Naar het klembord kopiëren](media//end-user-copy-paste/power-bi-copied.png)


4. Nadat uw visual gekopieerd is, plakt u deze in een andere toepassing met **Ctrl + V** of door met de **rechtermuisknop** > **Plakken** te klikken. In de onderstaande schermopname is de visual in een e-mailbericht geplakt.

    ![visual die in Outlook is geplakt](media//end-user-copy-paste/power-bi-copy-email.png)

5. Als er een label over gevoeligheid van gegevens is toegepast op het rapport, wordt een waarschuwing weergegeven wanneer u het kopieerpictogram selecteert.  

    ![waarschuwing over gevoelige gegevens](media//end-user-copy-paste/power-bi-sensitive.png)

    Bovendien wordt een gevoeligheidslabel toegevoegd aan de metagegevens onder de geplakte visual. 

    ![visual met label over vertrouwelijke informatie](media//end-user-copy-paste/power-bi-confidential.png)



## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing

   ![kopiëren niet beschikbaar](media//end-user-copy-paste/power-bi-copy-grey.png)


V: Waarom is het kopieerpictogram uitgeschakeld bij een visual?    
A: Momenteel worden systeemeigen Power BI-visuals en gecertificeerde aangepaste visuals ondersteund. Er is beperkte ondersteuning voor bepaalde visuals, inclusief: 
- ESRI en andere kaartvisuals 
- Python-visuals 
- R-visuals 
- PowerApps-visual   

A: De mogelijkheid om een visual te kopiëren kan worden uitgeschakeld door uw IT-afdeling of Power BI-beheerder.


V: Waarom wordt mijn visual niet goed geplakt?    
A: Er gelden beperkingen voor aangepaste visuals en visuals met animatie. 



## <a name="next-steps"></a>Volgende stappen
Meer informatie over [visualisaties in Power BI-rapporten](end-user-visual-type.md)

Als u bewerkingsmachtigingen hebt voor een rapport, [kunt u visuals kopiëren en plakken binnen hetzelfde rapport](../visuals/power-bi-visualization-copy-paste.md). 

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

