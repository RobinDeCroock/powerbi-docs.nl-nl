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
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100256"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Aanvullende diagnostische gegevens vastleggen voor Power BI

Dit artikel bevat instructies voor het handmatig verzamelen van aanvullende diagnostische gegevens van de Power BI-webclient.

1. Ga naar [Power BI](https://app.powerbi.com) met Microsoft Edge of Internet Explorer.

1. Druk op **F12** om de ontwikkelhulpprogramma's van Microsoft Edge te openen.

   ![Schermafbeelding van het tabblad met ontwikkelhulpprogramma's van Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Selecteer het tabblad **Netwerk**. Hier wordt een lijst weergegeven met het verkeer dat al is vastgelegd.

   ![Schermafbeelding van het tabblad Netwerk van de ontwikkelhulpprogramma's van Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    U kunt:

    * Bladeren in het venster en problemen reproduceren die u tegenkomt.

    * Het venster met ontwikkelhulpprogramma's op elk gewenst moment tijdens de sessie verbergen en weergeven door op F12 te drukken.

1. Als u wilt stoppen met het profileren van de sessie, selecteert u het rode blokje op het tabblad **Netwerk** van de ontwikkelhulpprogramma's.

   ![Schermafbeelding van het tabblad Netwerk van de ontwikkelhulpprogramma's van Microsoft Edge met de optie voor het stoppen van de profileringssessie.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Selecteer het diskettepictogram om de gegevens te exporteren als een HTTP-archiefbestand (HAR).

   ![Schermafbeelding van het tabblad Netwerk van de ontwikkelhulpprogramma's van Microsoft Edge met de optie voor het exporteren van gegevens.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Geef een bestandsnaam op en sla het HAR-bestand op.

    Het HAR-bestand bevat alle informatie over netwerkaanvragen tussen het browservenster en Power BI, waaronder:

    * De activiteit-id's voor elke aanvraag.

    * De exacte tijdstempel voor elke aanvraag.

    * Eventuele foutgegevens die naar de client zijn geretourneerd.

    Deze tracering bevat ook de gegevens die worden gebruikt voor het vullen van de visuele elementen die op het scherm worden weergegeven.

1. U kunt het HAR-bestand naar ondersteuning verzenden voor controle.

Nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
