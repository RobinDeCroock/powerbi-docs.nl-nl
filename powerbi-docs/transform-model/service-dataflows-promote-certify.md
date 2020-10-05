---
title: Niveauverhoging of certificering van gegevensstromen (preview)
description: Leer hoe u het niveau van gegevensstromen verhoogt of gegevensstromen certificeert.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 06/15/2020
ms.author: painbar
LocalizationGroup: Share your work
ms.openlocfilehash: 87b1f15b53ef5a76fe61e040766822dd2714add4
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91528270"
---
# <a name="promote-or-certify-dataflows-preview"></a>Niveauverhoging of certificering van gegevensstromen (preview)

Power BI biedt twee manieren om de zichtbaarheid van uw waardevolle gegevensstromen van hoge kwaliteit te vergroten: **niveauverhoging** en **certificering**.

* **Promotie**: Met niveauverhoging kunnen gebruikers gegevensstromen markeren die ze waardevol en de moeite waard achten voor gebruik door anderen. Op deze manier wordt het gezamenlijk verspreiden van gegevensstromen binnen een organisatie gestimuleerd. Een eigenaar van een gegevensstroom, of elk lid met schrijfmachtigingen voor de werkruimte waarin een gegevensstroom zich bevindt, kan het niveau van de gegevensstroom eenvoudig verhogen wanneer deze goed genoeg wordt geacht om te delen.

* **Certificering**: Certificering betekent dat een gegevensstroom is gecontroleerd door een geautoriseerde revisor en dat deze stroom een betrouwbare, gezaghebbende gegevensbron is die gereed is voor gebruik in de hele organisatie. Een geselecteerde groep revisoren die door de Power BI-beheerder is gedefinieerd, bepaalt welke gegevensstromen moeten worden gecertificeerd. Een gebruiker die meent dat een bepaalde gegevensstroom moet worden gecertificeerd, maar niet gemachtigd is om deze te certificeren, kan contact opnemen met de beheerder.

  Certificering van een gegevensstroom is alleen mogelijk als dit is [ingeschakeld door de Power BI-beheerder](../admin/service-admin-setup-certification.md).

Niveauverhoging of certificering van een gegevensstroom wordt *goedkeuring* genoemd. Makers van Power BI-rapporten hebben vaak veel verschillende gegevensstromen waaruit ze kunnen kiezen, en ondersteuning leidt ze naar de gegevensstromen die betrouwbaar en gezaghebbend zijn.

Ondersteunde gegevensstromen zijn duidelijk gelabeld op veel plaatsen in Power BI. Hierdoor zijn ze eenvoudig te vinden door rapportmakers die op zoek zijn naar betrouwbare gegevens, en kunnen beheerders en rapportmakers bijhouden hoe deze stromen in de hele organisatie worden gebruikt.

In de onderstaande afbeelding ziet u hoe gegevensstromen waarvan het niveau is verhoogd en die zijn gecertificeerd, eenvoudig kunnen worden geïdentificeerd in Power Query.

![Ondersteunde gegevensstromen gemarkeerd in Power Query](media/service-dataflows-promote-certify/powerbi-dataflow-endorsement-power-query.png)

In dit artikel wordt het volgende beschreven
* Het niveau van een gegevensstroom verhogen (door de eigenaar van een gegevensstroom of een gebruiker met lidmachtigingen voor de werkruimte waarin de gegevensstroom zich bevindt)
* Een gegevensstroom certificeren (door een geautoriseerde gegevensstroomcertificeerder, zoals bepaald door de Power BI-beheerder)

Zie [Certificering van gegevensset en gegevensstroom instellen](../admin/service-admin-setup-certification.md) voor informatie over het instellen van gegevensstroomcertificering (door de beheerder)


## <a name="promote-a-dataflow"></a>Het niveau van een gegevensset verhogen

Als u het niveau van een gegevensstroom wilt verhogen, moet u schrijfmachtigingen hebben voor de werkruimte waarin de gegevensstroom zich bevindt waarvan u het niveau wilt verhogen.

1. Ga naar de lijst met gegevensstromen in de werkruimte.
 
1. Selecteer **Meer opties** (...) voor de gegevensstroom waarvan u het niveau wilt verhogen en selecteer vervolgens **Instellingen**.

    ![Het beletselteken voor de gegevensstroom selecteren](media/service-dataflows-promote-certify/power-bi-dataflow-settings.png)

1. Vouw de sectie Goedkeuring uit en selecteer **Verhoogd niveau**.

    ![Selecteer Gepromoveerd en Toepassen](media/service-dataflows-promote-certify/power-bi-dataflow-promoted-endorsement.png)

1. Selecteer **Toepassen**.

## <a name="certify-a-dataflow"></a>Een gegevensstroom certificeren

Deze sectie is bedoeld voor gebruikers die door hun Power BI-beheerder zijn gemachtigd om gegevensstromen te certificeren. Het certificeren van gegevensstromen is een grote verantwoordelijkheid. In deze sectie wordt het te volgen certificeringsproces uitgelegd.

1. Verkrijg schrijfmachtigingen voor de werkruimte waarin de te certificeren gegevensstroom zich bevindt. Deze zijn te verkrijgen bij de gegevensstroomeigenaar of iemand met beheerdersmachtigingen voor de werkruimte. 

1. Controleer de gegevensstroom zorgvuldig en bepaal of deze certificering verdient.

1. Als u besluit de gegevensstroom te certificeren, gaat u naar de werkruimte waarin deze zich bevindt.
 
1. Zoek de gewenste gegevensstroom, klik op **Meer opties** (...) en selecteer vervolgens **Instellingen**.

    ![Het beletselteken voor de gegevensset of gegevensstroom selecteren](media/service-dataflows-promote-certify/power-bi-dataflow-settings.png)

1. Vouw de sectie Goedkeuring uit en selecteer **Gecertificeerd**. 

    ![Klikken op de koppeling Meer informatie](media/service-dataflows-promote-certify/service-certify-datasets-dataflows.png)

2. Klik op **Toepassen**.

## <a name="next-steps"></a>Volgende stappen

* [Certificering van gegevenssets en gegevensstromen instellen](../admin/service-admin-setup-certification.md)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)