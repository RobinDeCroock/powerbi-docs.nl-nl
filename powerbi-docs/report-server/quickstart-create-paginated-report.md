---
title: Een gepagineerd rapport maken voor Power BI Report Server
description: Leer hoe u in een paar eenvoudige stappen een gepagineerd rapport voor Power BI Report Server maakt.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/07/2020
ms.author: maggies
ms.openlocfilehash: 33c4f7b208916c2d920591acfc444f52c7655e47
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/07/2020
ms.locfileid: "78919530"
---
# <a name="create-a-paginated-report-for-power-bi-report-server"></a>Een gepagineerd rapport maken voor Power BI Report Server
In dit artikel ziet u hoe u met een paar eenvoudige stappen een gepagineerd rapport voor Power BI Report Server maakt.

Bent u op zoek naar hulp bij het maken van gepagineerde rapporten in Report Builder voor de Power BI-service? Zie in plaats hiervan [Power BI Report Builder](../paginated-reports/report-builder-power-bi.md).

Zoals de naam al aangeeft, kunnen gepagineerde rapporten uit meerdere pagina's bestaan. Ze worden opgemaakt met een vaste indeling en kunnen uiterst precies worden aangepast. Gepagineerde rapporten zijn RDL bestanden.

U kunt gepagineerde rapporten beheren en opslaan in de webportal van Power BI Report Server, net als u in de webportal van de SQL Server Reporting Services (SSRS). U maakt en bewerkt de rapporten in Report Builder of Report Designer in SQL Server Data Tools (SSDT). Vervolgens kunt u ze naar een van de twee webportals publiceren. De rapportlezers binnen uw organisatie kunnen ze weergeven in een browser of in een mobiele Power BI-app op hun mobiele apparaat.

![Gepagineerd Power BI Report Server-rapport](media/quickstart-create-paginated-report/reportserver-paginated-report.png)

Als u al gepagineerde rapporten in Report Builder of Report Designer hebt gemaakt, bent u er klaar voor om gepagineerde rapporten voor Power BI Report Server te maken. Als dat niet het geval is, volgen hier enkele snelle stappen om u op weg te helpen.

## <a name="step-1-start-report-builder"></a>Stap 1: Report Builder starten
Mogelijk hebt u Report Builder al geïnstalleerd om rapporten voor een SSRS-server te maken. U kunt dezelfde versie of Report Builder gebruiken om rapporten voor Power BI Report Server te maken. Als u Report Builder nog niet hebt geïnstalleerd, kunt u dit vrij eenvoudig alsnog doen.

1. Selecteer in de Power BI Report Server-webportal **Nieuw** > **Gepagineerd rapport**.
   
    ![Menu Nieuw gepagineerd rapport](media/quickstart-create-paginated-report/reportserver-new-paginated-report-menu.png)
   
    Als u Report Builder nog niet hebt geïnstalleerd, wordt u nu door het installatieproces geleid.
2. Nadat Report Builder is geïnstalleerd, wordt het programma geopend en wordt het scherm **Nieuw rapport of nieuwe gegevensset** weergegeven.
   
    ![Het scherm Nieuw rapport of nieuwe gegevensset](media/quickstart-create-paginated-report/reportserver-paginated-new-report-screen.png)
3. Selecteer de wizard voor het type rapport dat u wilt maken:
   
   * Tabel of matrix
   * Diagram
   * Kaart
   * Leeg
4. Laten we beginnen met de wizard Grafieken.
   
    Met de wizard Grafieken doorloopt u het proces om eenvoudige diagrammen in een rapport te maken. Daar kunt u het rapport vrijwel zonder enige restrictie naar wens aanpassen.

## <a name="step-2-go-through-the-chart-wizard"></a>Stap 2: De wizard voor grafieken doorlopen
Met de wizard Grafieken doorloopt u de basisstappen om een visualisatie in een rapport te maken.

Gepagineerde rapporten kunnen verbinding maken met een groot aantal gegevensbronnen, van Microsoft SQL Server en Microsoft Azure SQL Database tot Oracle, Hyperion en nog veel meer. Meer informatie over [gegevensbronnen die worden ondersteund door gepagineerde rapporten](connect-data-sources.md).

Op de eerste pagina in de wizard Grafieken, **Een gegevensset kiezen**, kunt u een gegevensset maken of een gedeelde gegevensset op een server kiezen. *Gegevenssets* retourneren rapportgegevens naar aanleiding van een query voor een externe gegevensbron.

1. Selecteer **Bladeren** > selecteer een gedeelde gegevensset op een server > **Openen** > **Volgende**.
   
    ![Wizard Grafiek: Een gegevensset kiezen](media/quickstart-create-paginated-report/reportserver-paginated-choose-dataset.png)
   
     Moet u een gegevensset maken? Zie [Een gedeelde of ingesloten gegevensset maken](https://docs.microsoft.com/sql/reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs).
2. Kiest een type diagram. In dit geval kiest u een staafdiagram.
   
    ![Wizard Grafiek: Grafiektype](media/quickstart-create-paginated-report/reportserver-paginated-choose-chart-type.png)
3. Rangschik de velden door ze naar de vakken **Categorieën**, **Reeks** en **Waarden** te slepen.
   
    ![Wizard Grafiek: Velden rangschikken](media/quickstart-create-paginated-report/reportserver-paginated-arrange-fields.png)
4. Selecteer **Volgende** > **Voltooien**.

## <a name="step-3-design-your-report"></a>Stap 3: Het rapport ontwerpen
U bevindt zich nu in de weergave voor het ontwerpen van rapporten. Zoals u ziet, wordt er een tijdelijke gegevensaanduiding weergegeven, niet uw gegevens.

![Ontwerpweergave van een rapport](media/quickstart-create-paginated-report/reportserver-paginated-preview-report.png)

* Als u uw gegevens wilt weergeven, selecteert u **Uitvoeren**.
  
     ![Rapport uitvoeren](media/quickstart-create-paginated-report/reportserver-paginated-run-report.png)
* Selecteer **Ontwerpen** om terug te keren naar de ontwerpweergave.

U kunt het diagram dat u zojuist hebt gemaakt, wijzigen door de indeling, waarden, legenda... eigenlijk vrijwel alles aan te passen.

En u kunt diverse andere visualisaties toevoegen: meters, tabellen, matrices, kaarten en meer. U kunt kop- en voetteksten toevoegen voor meerdere pagina's. Zie de [zelfstudies voor Report Builder](https://docs.microsoft.com/sql/reporting-services/report-builder-tutorials) om het zelf te proberen.

![De ontwerpweergave van Report Builder](media/quickstart-create-paginated-report/reportserver-paginated-finished-design-report.png)

## <a name="step-4-save-your-report-to-the-report-server"></a>Stap 4: Het rapport opslaan op de rapportserver
Wanneer uw rapport klaar is, slaat u het op in Power BI Report Server.

1. Selecteer in het menu **Bestand** de optie **Opslaan als** en sla het bestand op naar de rapportserver. 
2. Nu kunt u het rapport weergeven in de browser.
   
    ![Gepagineerd rapport in de browser](media/quickstart-create-paginated-report/reportserver-paginated-report.png)

## <a name="next-steps"></a>Volgende stappen
Er zijn meer dan genoeg goede bronnen voor het ontwerpen van rapporten in Report Builder en in Report Designer in SQL Server Data Tools. De zelfstudies over Report Builder vormen een goed startpunt.

* [Zelfstudies over Report Builder](https://docs.microsoft.com/sql/reporting-services/report-builder-tutorials)
* [Wat is Power BI Report Server?](get-started.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

