---
title: Subrapporten in gepagineerde Power BI-rapporten
description: In dit artikel vindt u informatie over ondersteunde gegevensbronnen voor gepagineerde rapporten in de Power BI-service en hoe u verbinding maakt met Azure SQL Database-gegevensbronnen.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 04/29/2020
ms.openlocfilehash: fbe60bab0d1c8d95cec1a3fda1d4b23fe919ea31
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861378"
---
# <a name="subreports-in-power-bi-paginated-reports"></a>Subrapporten in gepagineerde Power BI-rapporten

Een *subrapport* is een gepagineerd rapportitem waarin een ander gepagineerd rapport wordt weergegeven in de hoofdtekst van een gepagineerd hoofdrapport. Conceptueel gezien is een subrapport in een rapport vergelijkbaar met een frame op een webpagina. U kunt hiermee een rapport insluiten in een rapport. U kunt elk rapport gebruiken als subrapport. U slaat het rapport op dat wordt weergegeven als subrapport in dezelfde Premium-werkruimte als het bovenliggende rapport. U kunt het bovenliggende rapport ontwerpen om parameters door te geven aan het subrapport. Een subrapport kan in gegevensgebieden worden herhaald, met behulp van een parameter voor het filteren van gegevens in elk exemplaar van het subrapport.  
  
 ![Subrapport in een gepagineerd rapport](media/subreports/paginated-report-subreport.png "Subrapport voor een gepagineerde rapport")  
  
 In deze afbeelding komen de contactgegevens die worden weergegeven in het hoofdrapport Verkooporders in werkelijkheid uit het subrapport Contactpersonen.  
  
U kunt definitiebestanden van gepagineerde rapporten (. RDL) maken en wijzigen in Power BI Report Builder. U kunt subrapporten die zijn opgeslagen in SQL Server Reporting Services uploaden naar een Premium-werkruimte in de Power BI-service. De hoofdrapporten en subrapporten moeten naar dezelfde werkruimte worden gepubliceerd. Installeer [Power BI Report Builder](https://aka.ms/pbireportbuilder).
  
## <a name="work-with-report-builder-and-the-power-bi-service"></a>Werken met Report Builder en de Power BI-service

In Power BI Report Builder kunt u werken met gepagineerde rapporten op uw computer (ook wel lokale rapporten genoemd) of met rapporten in de Power BI-service.  Wanneer u Report Builder voor de eerste keer opent, wordt u gevraagd u aan te melden bij uw Power BI-account. Als dat niet het geval is, selecteert u in de rechterbovenhoek **Aanmelden**.

:::image type="content" source="media/subreports/report-builder-sign-in.png" alt-text="Aanmelden bij Power BI":::

Nadat u zich hebt aangemeld, ziet u de optie **Power BI-service** in Power BI Report Builder voor de opties **Openen** en **Opslaan als** in het menu **Bestand**. Wanneer u de optie **Power BI-service** selecteert om een rapport op te slaan, maakt u een live verbinding tussen Power BI Report Builder en de Power BI-service. 

:::image type="content" source="media/subreports/report-builder-subreport-open-service.png" alt-text="Openen via de Power BI-service":::

## <a name="save-a-local-report-to-the-power-bi-service"></a>Een gepagineerd rapport opslaan in de Power BI-service

Voordat u een subrapport aan een hoofdrapport kunt toevoegen, maakt u eerst de twee rapporten en slaat u deze op in dezelfde Power BI Premium-werkruimte. 

1. Als u een bestaand lokaal rapport wilt openen, selecteert u in het menu **Bestand** **Openen** > **Deze PC** en selecteert u een RDL-bestand.  

2. Selecteer in het menu **Bestand** de optie **Opslaan als** > **Power BI-service**.  Zie [Een gepagineerd rapport publiceren in de Power BI-service](paginated-reports-save-to-power-bi-service.md) voor uitgebreide informatie.

    > [!NOTE]
    > U kunt ook een rapport uploaden door te beginnen in de Power BI-service. Hetzelfde artikel [Een gepagineerd rapport publiceren in de Power BI-service](paginated-reports-save-to-power-bi-service.md) biedt uitgebreide informatie.

3. Selecteer in het dialoogvenster **Opslaan als** een Power BI Premium-werkruimte waar u uw gepagineerde rapporten kunt opslaan.  Premium-werkruimten hebben een diamantpictogram ![Premium-diamantpictogram](media/subreports/report-builder-premium-diamond.png) naast de naam van de werkruimte.

    :::image type="content" source="media/subreports/report-builder-subreport-save-as-service.png" alt-text="Opslaan als in de Power BI-service":::

4. Selecteer **Opslaan**.

## <a name="add-a-subreport-to-a-report"></a>Een subrapport aan een rapport toevoegen

Nu u beide rapporten hebt opgeslagen in dezelfde Premium-werkruimte, kunt u het ene aan het andere toevoegen als subrapport. Er zijn twee manieren om een subrapport toe te voegen. 

1. Selecteer in het lint **Invoegen** de knop **Subrapport** of klik met de rechtermuisknop op het canvas van het rapport en selecteer **Invoegen** > **Subrapport**.

    :::image type="content" source="media/subreports/report-builder-insert-subreport.png" alt-text="Een subrapport invoegen in een rapport":::

    Het dialoogvenster **Eigenschappen van subrapport** wordt geopend.  

2. Selecteer de knop **Bladeren** > Navigeer naar het rapport dat u wilt gebruiken als subrapport > Geef de naam van het subrapport op in het tekstvak **Naam**.

3. Configureer, indien nodig, andere eigenschappen, zoals [parameters](#use-parameters-in-subreports).

## <a name="use-parameters-in-subreports"></a>Parameters in subrapporten gebruiken  
 Als u parameters van het bovenliggende rapport wilt doorgeven aan het subrapport, definieert u een rapportparameter in het rapport dat u als subrapport gebruikt. Wanneer u het subrapport in het bovenliggende rapport plaatst, kunt u de rapportparameter selecteren en een waarde die u van het bovenliggende rapport aan de rapportparameter in het subrapport wilt doorgeven.  
  
> [!NOTE]  
> De parameter die u in het subrapport selecteert, is een *rapport*parameter, niet een *query*parameter.  
  
 U kunt een subrapport in de hoofdtekst van het rapport of in een gegevensgebied plaatsen. Als u een subrapport in een gegevensgebied plaatst, wordt het subrapport herhaald met elk exemplaar van de groep of rij in het gegevensgebied. U kunt een waarde van de groep of rij doorgeven aan het subrapport. Gebruik in de eigenschapswaarde van het subrapport een veldexpressie voor het veld met de waarde die u wilt doorgeven aan de subrapportparameter.  
  
 Zie [Een subrapport en parameters toevoegen](/sql/reporting-services/report-design/add-a-subreport-and-parameters-report-builder-and-ssrs) in de SQL Server Reporting Services-documentatie voor meer informatie over het werken met parameters en subrapporten.  

## <a name="preview-paginated-reports-in-report-builder"></a>Voorbeeldweergave van gepagineerde rapporten in Report Builder

U kunt een voorbeeld van uw rapporten weergeven in Report Builder.

- Selecteer in het lint **Start** **Uitvoeren**. 

Omdat Report Builder een ontwerpprogramma is, kan een voorbeeldweergave van het rapport er anders uitzien dan de weergave van het rapport in de Power BI-service.

### <a name="notes-about-previewing"></a>Opmerkingen over voorbeeldweergave

- Report Builder slaat geen referenties op voor gegevensbronnen die in rapporten worden gebruikt.  Report Builder vraagt u tijdens de voorbeeldweergave om elke set referenties.  
- Als de gegevensbronnen van het rapport on-premises zijn, moet u een gateway configureren nadat u het rapport hebt opgeslagen in de Power BI-werkruimte.
- Als Report Builder een fout tegenkomt tijdens de voorbeeldweergave, wordt een algemeen bericht geretourneerd.  Als de fout moeilijk kan worden opgespoord, kunt u het rapport weergeven in de Power BI-service.  

## <a name="considerations"></a>Overwegingen

### <a name="maintaining-the-connection"></a>De verbinding onderhouden

De verbinding tussen Report Builder en Power BI blijft niet behouden wanneer u het bestand sluit.  Het is mogelijk om met een lokaal hoofdrapport te werken terwijl er subrapporten zijn opgeslagen in de Power BI-werkruimte. Zorg ervoor dat u het hoofdrapport opslaat in de Power BI-werkruimte voordat u het rapport sluit.  Als u dat niet doet, ontvangt u mogelijk het bericht 'Niet gevonden' tijdens de voorbeeldweergave, omdat er geen live verbinding is met de Power BI-service.  In dat geval gaat u naar een subrapport en selecteert u de eigenschappen ervan.  Open het subrapport opnieuw vanuit de Power BI-service.  Hiermee wordt de verbinding opnieuw tot stand gebracht en ontstaan er geen problemen voor alle andere subrapporten.

### <a name="renaming-a-subreport"></a>De naam van een subrapport wijzigen

Als u de naam van een subrapport in de werkruimte wijzigt, moet u de verwijzing naar de naam in het hoofdrapport corrigeren. Anders wordt het subrapport niet weergegeven. Het hoofdrapport wordt nog steeds weergegeven met een foutbericht in het subrapportitem.

## <a name="migrate-large-reports"></a>Grote rapporten migreren

Als u grote rapporten naar Power BI migreert, is het misschien een goed idee om het hulpprogramma [RdlMigration](../guidance/migrate-ssrs-reports-to-power-bi.md) te gebruiken.  Dankzij een update kan het hulpprogramma RdlMigration dubbele subrapportnamen verwerken.  Dubbele subrapportnamen kunnen optreden wanneer twee of meer rapporten dezelfde naam hebben, maar zich in verschillende submappen bevinden.  Als de namen niet uniek zijn gemaakt, wordt alleen het eerste subrapport herkend.

Als u Report Builder wilt gebruiken voor het migreren van grote rapporten, raden we u aan om eerst met de subrapporten te werken. Sla deze allemaal op in de Power BI-werkruimte om dubbele rapportnamen te voorkomen.

## <a name="share-reports-with-subreports"></a>Rapporten met subrapporten delen

Zoals we hebben aangegeven, moeten het hoofdrapport en de subrapporten zich in dezelfde werkruimte bevinden. Anders wordt het subrapport niet weergegeven. Wanneer u het hoofdrapport deelt, moet u ook de subrapporten delen. Als u het hoofdrapport in een app deelt, moet u ervoor zorgen dat u ook de subrapporten in die app opneemt. Als u het hoofdrapport rechtstreeks met gebruikers of gebruikersgroepen deelt, moet u ook elk subrapport delen met dezelfde set gebruikers of gebruikersgroepen.
  
## <a name="next-steps"></a>Volgende stappen

[Problemen met subrapporten in gepagineerde Power BI-rapporten oplossen](subreports-troubleshoot.md)

[Een gepagineerd rapport weergeven in de Power BI-service](../consumer/paginated-reports-view-power-bi-service.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)