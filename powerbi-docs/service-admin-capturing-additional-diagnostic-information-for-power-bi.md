---
title: Aanvullende diagnostische gegevens vastleggen
description: Deze instructies bieden twee mogelijke opties voor het handmatig verzamelen van aanvullende diagnostische gegevens van de Power BI-webclient.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 710fb4cdcf9efb051434966d47c2eaced17ac9ba
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100256"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Aanvullende diagnostische gegevens voor Power BI vastleggen

In dit artikel vindt u instructies voor het handmatig verzamelen van aanvullende diagnostische gegevens van de Power BI-webclient.

1. Blader naar [Power BI](https://app.powerbi.com) met Microsoft Edge of Internet Explorer.

1. Druk op **F12** de ontwikkelhulpprogramma's van Microsoft Edge openen.

   ![Schermafbeelding van Microsoft Edge Developer tools elementen tabblad.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Selecteer het tabblad **Netwerk**. Hier wordt een lijst weergegeven met het verkeer dat al is vastgelegd.

   ![Schermafbeelding van Microsoft Edge Developer tools tabblad netwerk.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    U kunt:

    * In het venster Bladeren en elk probleem dat u mogelijk gehoord reproduceren.

    * Verbergen en de ontwikkelaar van de hulpprogramma's voor venster weergeven op elk gewenst moment tijdens de sessie door op F12 te drukken.

1. Als u wilt stoppen met het profileren van de sessie, kunt u het rode vierkant selecteren op de **netwerk** gebied-tabblad van de ontwikkelaar van de hulpprogramma's.

   ![Schermafbeelding van Microsoft Edge Developer tools tabblad netwerk met een aanroep van buiten de stopknop.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Selecteer het pictogram diskette voor het exporteren van de gegevens als een HTTP-archief (HAR)-bestand.

   ![Schermafbeelding van Microsoft Edge Developer-hulpprogramma's tabblad netwerk met een bijschrift van de diskette-pictogram.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Geef een bestandsnaam op en sla het HAR-bestand op.

    Het HAR-bestand bevat alle informatie over netwerkaanvragen tussen het browservenster en Power BI met inbegrip van:

    * De activiteits-id's voor elke aanvraag.

    * De exacte tijdstempel voor elke aanvraag.

    * De gegevens van een fout geretourneerd naar de client.

    Deze tracering bevat ook de gegevens die worden gebruikt voor het vullen van de visuele elementen die op het scherm worden weergegeven.

1. U kunt het HAR-bestand naar ondersteuning verzenden voor controle.

Nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
