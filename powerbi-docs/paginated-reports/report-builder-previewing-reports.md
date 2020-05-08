---
title: Voorbeelden van rapporten weergeven in Power BI Report Builder
description: Tijdens het maken van een gepagineerd Report Builder-rapport is het handig om een voorbeeld van het rapport te bekijken om te controleren of het rapport naar wens wordt weergegeven.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: afbc31e3ece8bc72ad52bb2fe7c3d871b2f68e1b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "78922937"
---
# <a name="previewing-reports-in-power-bi-report-builder"></a>Voorbeelden van rapporten weergeven in Power BI Report Builder
  Tijdens het maken van een gepagineerd Report Builder-rapport is het handig om een voorbeeld van het rapport te bekijken om te controleren of het rapport naar wens wordt weergegeven. Klik op **Uitvoeren** als u een voorbeeld van het rapport wilt bekijken. Het rapport wordt weergegeven in de voorbeeldmodus.  
  
 De voorbeeldervaring in Report Builder is te verbeteren door bewerkingssessies te gebruiken, als er een verbinding is met een rapportserver. Met de bewerkingssessie wordt een gegevenscache gemaakt en worden de gegevenssets in de cache beschikbaar gesteld voor herhaalde voorbeeldweergaven van rapporten. Een bewerkingssessie is geen functie waarmee u rechtstreeks kunt communiceren. U kunt de prestaties van een rapportvoorbeeld echter verbeteren als u begrijpt wanneer de gegevensset in cache wordt vernieuwd en waarom het rapport sneller of langzamer wordt weergegeven.  

  
> [!NOTE]  
> Er zijn enkele verschillen tussen een voorbeeldweergave in Report Builder en de weergave in een browser. Zo is bijvoorbeeld een agendabesturingselement, dat wordt toegevoegd aan een rapport wanneer u een parameter van het type datum/tijd opgeeft, anders in Report Builder dan in een browser. 
  
## <a name="improving-preview-performance"></a>De prestaties van voorbeeldweergaven verbeteren  
 De manier waarop u rapporten maakt en bijwerkt heeft invloed op hoe snel het rapport verschijnt in de voorbeeldweergave. De eerste keer is dat u een voorbeeld van een rapport met een serververwijzing bekijkt, wordt er een bewerkingssessie voor u gemaakt en worden de gegevens die worden gebruikt bij de uitvoering van het rapport toegevoegd aan een gegevenscache die wordt opgeslagen. Wanneer u wijzigingen in het rapport aanbrengt die geen invloed hebben op de gegevens, wordt de kopie in cache van de rapportgegevens gebruikt. Dit betekent dat u gegevens niet altijd ziet veranderen wanneer u een voorbeeld van het rapport bekijkt. Klik op de knop **Vernieuwen** op het lint als u nieuwe gegevens wilt.  
  
 De volgende acties leiden ertoe dat de cache wordt vernieuwd en dat de volgende voorbeeldweergave van het rapport wordt vertraagd:  
  
-   Het toevoegen, wijzigen of verwijderen van een gegevensset. De gegevensset in cache bevat alle gegevenssets waarvan een rapport gebruikmaakt. Bij wijziging van een gegevensset wordt de gegevensset in cache ongeldig. Dit omvat het wijzigen van de naam, van de query of van de velden in de gegevensset.  
  
    > [!NOTE]  
    >  Als de gegevensset een groot aantal velden bevat die u verwacht niet te gebruiken, is het raadzaam de gegevensset bij te werken om deze velden weg te laten. Hoewel hiermee een nieuwe bewerkingssessie wordt gemaakt en het eerste voorbeeld van het rapport langzamer wordt weergegeven, is de kleinere gegevensset in cache in het algemeen goed voor de prestaties van de rapportserver.  
  
-   Een gegevensbron toevoegen, wijzigen of verwijderen. Dit omvat het wijzigen van de naam of eigenschappen van de gegevensbron, de gegevensextensie van de gegevensbron of de eigenschappen van de verbinding met de gegevensbron.  
  
-   Het wijzigen van de door het rapport gebruikte gegevensbron in een andere gegevensbron.  
  
-   Het wijzigen van de taal van het rapport.  
  
-   Het wijzigen van de door het rapport gebruikte assembly's of aangepaste code.  
  
-   Queryparameters in de rapport- of parameterwaarden toevoegen, wijzigen of verwijderen.  
  
 Het wijzigen van de rapportindeling en gegevensopmaak heeft geen invloed op de gegevensset in cache. U kunt de volgende acties uitvoeren zonder de gegevensset in cache te vernieuwen:  
  
-   Gegevensgebieden, zoals tabellen, matrices of grafieken, toevoegen of verwijderen.  
  
-   Het toevoegen of verwijderen van rapportkolommen. Alle velden in de gegevensset zijn beschikbaar voor gebruik in het rapport. Het toevoegen of verwijderen van rapportvelden heeft geen effect op de gegevensset.  
  
-   De volgorde van velden in tabellen en matrices wijzigen.  
  
-   Rij- en kolomgroepen toevoegen, wijzigen of verwijderen.  
  
-   De opmaak van gegevenswaarden in velden toevoegen, wijzigen of verwijderen.  
  
-   Afbeeldingen, regels of tekstvakken toevoegen, wijzigen of verwijderen.  
  
-   Pagina-einden wijzigen.  
  
De bewerkingssessie wordt gemaakt bij de eerste weergave van een rapportvoorbeeld. Standaard duurt een bewerksessie 7200 seconden (2 uur). Steeds wanneer u het rapport uitvoert, wordt de sessie opnieuw ingesteld op twee uur. Wanneer de bewerkingssessie is verlopen, wordt de gegevenscache verwijderd. Als de bewerkingssessie is verlopen, wordt de volgende keer dat u een rapportvoorbeeld bekijkt, automatisch een nieuwe bewerkingssessie gemaakt.
  
Standaard kan de gegevenscache maximaal vijf gegevenssets bevatten. Als u veel verschillende combinaties parameterwaarden gebruikt, zijn er misschien meer gegevens nodig voor het rapport. Hiervoor moet de cache worden vernieuwd, waardoor het eerstvolgende rapportvoorbeeld langzamer wordt weergegeven. 
  
## <a name="concurrency-of-report-updates"></a>Gelijktijdigheid van rapportupdates  
Vaak zult u een rapportvoorbeeld weergeven als u een rapport bijwerkt en vervolgens opslaat in de Power BI-service. Wanneer u een rapport bijwerkt, is het mogelijk dat iemand anders het rapport op hetzelfde moment bijwerkt en vervolgens opslaat. Het rapport dat het laatst wordt opgeslagen is de rapportversie die beschikbaar is voor toekomstige voorbeeldweergaven en bewerkingen. Dit betekent dat de versie van het rapport waarvan u een voorbeeld hebt bekeken, mogelijk niet de versie is die u opnieuw opent. Daarom hebt u de mogelijkheid om het rapport op te slaan met een nieuwe naam met behulp van de optie **Opslaan als** in het Report Builder-menu.  
  
## <a name="external-report-items"></a>Externe rapportitems  
 Uw rapport kan items als externe afbeeldingen bevatten, die gescheiden van het rapport worden opgeslagen. Omdat de items apart worden opgeslagen, kunnen deze worden verplaatst naar een andere locatie of worden verwijderd. Als dit gebeurt, kan een voorbeeldweergave van het rapport mislukken. Als oplossing kunt u het rapport bijwerken zodat de bijgewerkte locatie van het item wordt aangegeven. Of als het item is verwijderd, kunt u het vervangen door een bestaand item of de verwijzing naar het item uit het rapport verwijderen.  
  
## <a name="next-steps"></a>Volgende stappen

- [Wat zijn gepagineerde rapporten in Power BI Premium?](paginated-reports-report-builder-power-bi.md)
  
