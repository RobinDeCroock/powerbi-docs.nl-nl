---
title: Een sjabloon voor een Power BI-app bijwerken, verwijderen en ophalen
description: Instructies voor het bijwerken, verwijderen en ophalen van een sjabloon-app.
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/23/2019
ms.author: tebercov
ms.openlocfilehash: 8ed27d830e0bc779fc7ecb8e3aa8fde11b8d9c61
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73432278"
---
# <a name="update-delete-and-extract-template-app"></a>Een sjabloon-app bijwerken, verwijderen en ophalen

Nu uw app in productie is, kunt u opnieuw beginnen in de testfase, zonder de app in productie te onderbreken.
## <a name="update-your-app"></a>Uw app bijwerken

Als u wijzigingen in Power BI Desktop hebt aangebracht, begint u bij stap (1). Als u geen wijzigingen in Power BI Desktop hebt aangebracht, begint u bij stap (4).

1. Upload de bijgewerkte gegevensset en overschrijf de bestaande gegevensset. **Zorg ervoor dat u exact dezelfde naam gebruikt voor de gegevensset**. Als u een andere naam gebruikt, wordt er een nieuwe gegevensset gemaakt voor gebruikers die de app bijwerken.
![gegevensset overschrijven](media/service-template-apps-update-extract-delete/power-bi-template-app-upload-dataset.png)
1. Importeer het PBIX-bestand van uw computer.
![gegevensset overschrijven](media/service-template-apps-update-extract-delete/power-bi-template-app-upload-dataset2.png)
1. Bevestig de overschrijving.
![gegevensset overschrijven](media/service-template-apps-update-extract-delete/power-bi-template-app-upload-dataset3.png)

1. Selecteer **App maken** in het deelvenster **Publicatiebeheer**.
1. Ga terug via het proces voor het maken van een app.
1. Nadat u **Huisstijl**, **Inhoud**, **Besturingselement** en **Toegang** hebt ingesteld, selecteert u nogmaals **App maken**.
1. Selecteer **Sluiten** en ga terug naar **Publicatiebeheer**.

   U hebt nu twee versies: De versie in productie en een nieuwe versie in de testfase.

    ![Twee versies van een sjabloon-app](media/service-template-apps-update-extract-delete/power-bi-template-app-update.png)

5. Als u klaar bent om de app te promoveren naar de preproductiefase waarin de app buiten de tenant wordt getest, gaat u terug naar het deelvenster Publicatiebeheer en selecteert u **App promoveren** naast **Testen**.
6. De koppeling is nu live. Dien de app nogmaals in bij de Cloud Partner-portal door de stappen te volgen bij de [Update voor Power BI-app-aanbieding](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-update-existing-offer).
7. U moet de aanbieding opnieuw **publiceren** in de Cloud Partner-portal en deze nogmaals laten valideren.

   >[!NOTE]
   >Promoveer uw app pas naar de productiefase wanneer de app in de Cloud Partner-portal is goedgekeurd en u de app hebt gepubliceerd.

### <a name="update-behavior"></a>Gedrag bijwerken

1. Als u de app bijwerkt, kan het installatieprogramma van de sjabloon-app [een sjabloon-app bijwerken](service-template-apps-install-distribute.md#update-a-template-app) in de reeds geïnstalleerde werkruimte zonder dat de configuratie van de verbinding verloren gaat.
1. Zie het [overschrijvingsgedrag](service-template-apps-install-distribute.md#overwrite-behavior) van het installatieprogramma voor meer informatie over hoe veranderingen in de gegevensset van invloed zijn op de geïnstalleerde sjabloon-app.
1. Wanneer u een sjabloon-app bijwerkt (overschrijft), wordt er om te beginnen teruggegaan naar voorbeeldgegevens en daarna wordt er automatisch opnieuw verbinding gemaakt met de configuratie van de gebruiker (parameters en verificatie). Totdat het vernieuwen is voltooid, worden de rapporten, dashboards en organisatie-app weergegeven met de banner met voorbeeldgegevens.
1. Als u een nieuwe queryparameter hebt toegevoegd aan de bijgewerkte gegevensset waarvoor invoer van gebruikers is vereist, moet u het selectievakje bij *Vereist* inschakelen. Hierdoor wordt de verbindingsreeks opgevraagd bij het installatieprogramma nadat de app is bijgewerkt.
 ![vereiste parameters](media/service-template-apps-update-extract-delete/power-bi-template-app-upload-dataset4.png)

## <a name="extract-workspace"></a>Werkruimte extraheren
Terugschakelen naar de vorige versie van een sjabloon-app is nu gemakkelijker dan ooit met de mogelijkheid voor extraheren. Met de volgende stappen wordt een specifieke app-versie in verschillende releasestadia geëxtraheerd naar een nieuwe werkruimte:

1. Druk in het deelvenster Publicatiebeheer op **(...)** en vervolgens op **Extraheren**.

    ![versie van sjabloon-app extraheren](media/service-template-apps-update-extract-delete/power-bi-template-app-extract.png) ![versie van sjabloon-app extraheren](media/service-template-apps-update-extract-delete/power-bi-template-app-extract-dialog.png)
2. Voer in het dialoogvenster de naam voor de geëxtraheerde werkruimte in. er wordt een nieuwe werkruimte toegevoegd.

Versiebeheer voor uw nieuwe werkruimte wordt opnieuw ingesteld en u kunt doorgaan met het ontwikkelen en distribueren van de sjabloon-app vanuit de onlangs geëxtraheerde werkruimte.

## <a name="delete-template-app-version"></a>Versie van sjabloon-app verwijderen
Een werkruimte voor de sjabloon is de bron van een actief gedistribueerde sjabloon-app. Ter bescherming van de gebruikers van de sjabloon-app is het niet mogelijk om een werkruimte te verwijderen zonder eerst alle gemaakt app-versies in de werkruimte te verwijderen.
Als u een app-versie verwijdert, wordt de app-URL ook verwijderd en werkt deze niet meer.

1. Selecteer in het deelvenster Publicatiebeheer het beletselteken **(...)** en vervolgens **Verwijderen**.
 ![Versie van sjabloon-app verwijderen](media/service-template-apps-update-extract-delete/power-bi-template-app-delete.png)
  ![Versie van sjabloon-app verwijderen](media/service-template-apps-update-extract-delete/power-bi-template-app-delete-dialog.png)

>[!NOTE]
>Zorg ervoor dat u niet de app-versie verwijdert die wordt gebruikt door klanten of **AppSource**, anders werkt deze niet meer.

## <a name="next-steps"></a>Volgende stappen

Zie hoe uw klanten werken met uw sjabloon-app in [Install, customize, and distribute template apps in your organization](service-template-apps-install-distribute.md) (Sjabloon-apps in uw organisatie installeren, aanpassen en distribueren).

Zie de [aanbieding voor Power BI-toepassing](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) voor meer informatie over het distribueren van uw app.
