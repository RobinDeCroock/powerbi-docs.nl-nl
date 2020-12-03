---
title: 'Zelfstudie: Power BI Report Server in een VM verkennen'
description: In deze zelfstudie maakt u een virtuele machine met Power BI Report Server dat al is geïnstalleerd en verkent u de webportal.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: tutorial
ms.date: 05/06/2019
ms.openlocfilehash: 85fcd6249a833c35cb98fca6abf2881ab1a4bf7e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418412"
---
# <a name="tutorial-explore-the-power-bi-report-server-web-portal-in-a-vm"></a>Zelfstudie: de webportal van Power BI Report Server in een VM verkennen
In deze zelfstudie maakt u een virtuele Azure-machine met Power BI Report Server dat al is geïnstalleerd, zodat u voorbeeldexemplaren van Power BI- en gepagineerde rapporten en KPI's kunt bekijken, bewerken en beheren.

![Webportal van Report Server](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm-no-numbers.png)

Dit zijn de taken die u in deze zelfstudie gaat uitvoeren:

> [!div class="checklist"]
> * Een VM maken en er verbinding mee maken
> * De webportal van Power BI Report Server starten en verkennen
> * Een favoriet item labelen
> * Een Power BI-rapport bekijken en bewerken
> * Een gepagineerd rapport bekijken, beheren en bewerken
> * Een Excel-werkmap in Excel Online bekijken

Voor deze zelfstudie hebt u een abonnement op Azure nodig. Als u er nog niet een hebt, maakt u een [gratis account](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) voordat u begint.

## <a name="create-a-power-bi-report-server-vm"></a>Een VM met Power BI Report Server maken

Gelukkig heeft het Power BI-team een VM gemaakt die hoort bij het al geïnstalleerde Power BI Report Server.

1. Selecteer Power BI Report Server op Azure Marketplace. Met deze koppeling wordt het programma direct geopend: [Power BI Report Server](https://azuremarketplace.microsoft.com/marketplace/apps/reportingservices.technical-preview?tab=Overview).  

2. Selecteer **Nu downloaden**.
3. Selecteer **Doorgaan** als u de gebruiksvoorwaarden en het privacybeleid van de provider wilt accepteren.

4. Selecteer **Maken**.

    ![VM met Power BI Report Server maken](media/tutorial-explore-report-server-web-portal/power-bi-report-server-create.png)

5. Geef in **Stap 1, Basisinformatie** **reportservervm** op voor **VM-naam**.

    De naam van de VM met Power BI Report Server mag geen streepjes bevatten.

5. Maak een gebruikersnaam en wachtwoord.

6. Selecteer **Nieuw** bij **Resourcegroep** en geef de groep de naam **reportserverresourcegroup** > **OK**.

    Als u de zelfstudie meer dan één keer volgt, moet u de resourcegroep na de eerste keer een andere naam geven. U kunt de naam van dezelfde resourcegroep niet twee keer in één abonnement gebruiken. 

    ![VM en resourcegroep een naam geven](media/tutorial-explore-report-server-web-portal/power-bi-report-server-create-resource-group.png)

7. Laat de overige standaardwaarden ongemoeid en klik op **OK**.

8. Laat in **Stap 2, Instellingen** de standaardwaarden staan > **OK**.
 
    De waarden voor **SQL Storage-account** en **Opslagaccount voor diagnose** moeten ook uniek zijn. Als u de zelfstudie meer dan één keer volgt, moet u steeds andere namen gebruiken.

9. Controleer in **Stap 3, Samenvatting** uw selecties > **OK**.

10. Lees in **Stap 4, Kopen** de gebruiksrechtovereenkomst en het privacybeleid > **Maken**.

    Het proces van het **verzenden van de implementatie voor Power BI Report Server** kan enkele minuten in beslag nemen.

## <a name="connect-to-your-virtual-machine"></a>Verbinding maken met de virtuele machine

1. Selecteer **Virtuele machines** in het navigatievenster van Azure. 

2. Typ 'rapport' in het vak **Filteren op naam**. 

3. Selecteer de VM met de naam **REPORTSERVERVM**.

    ![Virtuele machine bekijken](media/tutorial-explore-report-server-web-portal/power-bi-report-server-view-virtual-machine.png)

4. Selecteer **Verbinding maken** onder virtuele machine REPORTSERVERVM.

    ![Verbinding maken met de virtuele machine](media/tutorial-explore-report-server-web-portal/power-bi-report-server-connect-to-virtual-machine.png)

5. Laat de standaardwaarden staan in het deelvenster **Verbinding maken met uw virtuele machine** en selecteer **RDP-bestand downloaden**.

1. Selecteer **Verbinding maken** in het dialoogvenster **Verbinding met extern bureaublad**.

6. Voer de naam en het wachtwoord in die u hebt gemaakt voor de virtuele machine en klik op **OK**.

7. In het volgende dialoogvenster **staat dat de identiteit van de externe computer niet kan worden** vastgesteld. Selecteer **Ja**.

   De nieuwe VM wordt geopend.

## <a name="power-bi-report-server-on-the-vm"></a>Power BI Report Server op de VM

Als de VM wordt geopend, vindt u hier de items die u op het bureaublad ziet.

![Virtuele machine van Power BI Report Server wordt gestart](media/tutorial-explore-report-server-web-portal/power-bi-report-server-vm-5-numbers.png)

|Aantal  |Wat het betekent  |
|---------|---------|
|![Nummer 1](media/tutorial-explore-report-server-web-portal/number-1.png) | Power BI-voorbeeldrapporten (PBIX) |
|![Nummer 2](media/tutorial-explore-report-server-web-portal/number-2.png) | Koppelingen naar documentatie van Power BI Report Server |
|![Nummer 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Hiermee wordt een versie van Power BI Desktop gestart die is geoptimaliseerd voor Power BI Report Server (januari 2019) |
|![Nummer 4](media/tutorial-explore-report-server-web-portal/number-4.png) | Hiermee wordt de webportal van Power BI Report Server in de browser geopend |
|![Nummer 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Hiermee wordt SQL Server Data Tools gestart om gepagineerde (RDL) rapporten te maken |

Dubbelklik op het pictogram **Webportal van Report Server**. In de browser wordt `https://localhost/reports/browse` geopend. In de webportal ziet u verschillende, op type ingedeelde bestanden. 

![De webportal van Power BI Report Server](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm.png)

|Aantal  |Wat het betekent  |
|---------|---------|
|![Nummer 1](media/tutorial-explore-report-server-web-portal/number-1.png) | KPI's die in de webportal zijn gemaakt |
|![Nummer 2](media/tutorial-explore-report-server-web-portal/number-2.png) |  Power BI-rapporten (PBIX)  |
|![Nummer 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Mobiele rapporten die in SQL Server Mobile Report Publisher zijn gemaakt  |
|![Nummer 4](media/tutorial-explore-report-server-web-portal/number-4.png) |  Gepagineerde rapporten die in Report Builder of SQL Server Data Tools zijn gemaakt  |
|![Nummer 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Excel-werkmappen   | 
|![Nummer 6](media/tutorial-explore-report-server-web-portal/number-6.png) | Gegevensbronnen voor gepagineerde rapporten | 


## <a name="tag-your-favorites"></a>Favorieten labelen
U kunt uw rapporten en KPI's taggen die u wilt toevoegen aan uw favorieten. Ze zijn dan gemakkelijker te vinden omdat ze allemaal worden verzameld in één map met favorieten, zowel in de webportal als in de mobiele Power BI-apps. 

1. Selecteer het beletselteken ( **...** ) in de rechterbovenhoek van de KPI **Winstmarge** > **Toevoegen aan favorieten**.
   
    ![Toevoegen aan Favorieten](media/tutorial-explore-report-server-web-portal/power-bi-report-server-add-to-favorites.png)
2. Selecteer op het lint van het webportaal de optie **Favorieten** om de KPI of het rapport samen met uw andere favorieten weer te geven op de pagina Favorieten in de webportal.
   
    ![Favorieten weergeven](media/tutorial-explore-report-server-web-portal/power-bi-report-server-favorites.png)

3. Selecteer **Bladeren** om terug te gaan naar de webportal.
   
## <a name="view-items-in-list-view"></a>Items bekijken in de lijstweergave
Standaard wordt de inhoud in de webportal weergegeven in de tegelweergave.

Desgewenst kunt u overschakelen naar de lijstweergave. In deze weergave is het makkelijker om meerdere items tegelijkertijd te verplaatsen of te verwijderen. 

1. Selecteer **Tegels** > **Lijst**.
   
    ![Tussen weergaven schakelen](media/tutorial-explore-report-server-web-portal/report-server-web-portal-list-view.png)

2. Ga terug naar de tegelweergave: selecteer **Lijst** > **Tegels**.

## <a name="power-bi-reports"></a>Power BI-rapporten

In de webportal kunt u Power BI-rapporten bekijken en ermee werken en u kunt Power BI Desktop rechtstreeks in de webportal starten.

### <a name="view-power-bi-reports"></a>Power BI-rapporten bekijken

1. In de webportal onder **Power BI-rapporten** selecteert u **Sample Customer Overview Report**. Het rapport wordt geopend in de browser.

1. Selecteer het blok Verenigde Staten in de boomstructuur om te zien hoe gerelateerde waarden in de andere visuele weergaven zijn gemarkeerd.

    ![Gemarkeerd Power BI-rapport](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi.png)

### <a name="edit-in-power-bi-desktop"></a>Bewerken in Power BI Desktop

1. Selecteer **Bewerken in Power BI Desktop**.

1. Selecteer **Toestaan** zodat deze website een programma op uw computer kan openen. 

     Het rapport wordt geopend in Power BI Desktop. Let op de naam in de bovenste balk: 'Power BI Desktop (January March 2019)'. Dat is de versie die is geoptimaliseerd voor Power BI Report Server.

    Gebruik de versie van Power BI Desktop die is geïnstalleerd op de VM. U kunt niet wisselen tussen domeinen voor het uploaden van een rapport.

3. Vouw in het deelvenster Velden de tabel Klanten uit en sleep het veld Occupation naar Filters op rapportniveau.

    ![Een veld naar het deelvenster Filters slepen](media/tutorial-explore-report-server-web-portal/power-bi-report-server-desktop-filter.png)

1. Sla het rapport op.

1. Ga terug naar het rapport in de browser en selecteer het pictogram **Vernieuwen** om de browser te vernieuwen.

    ![Pictogram Vernieuwen in de browser](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-refresh.png)

8. Vouw het deelvenster **Filters** aan de rechterkant uit om het filter **Occupation** te zien dat u hebt toegevoegd. Selecteer **Professional**.

    ![Gefilterd Power BI-rapport](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi-filtered.png)

3. Selecteer **Bladeren** om terug te gaan naar de webportal.

## <a name="paginated-rdl-reports"></a>Gepagineerde (RDL) rapporten

In de webportal kunt u gepagineerde rapporten bekijken en beheren en Report Builder starten.

### <a name="manage-a-paginated-report"></a>Gepagineerd rapport beheren

1. Selecteer in de webportal onder **Gepagineerde rapporten** **Meer opties** (...) naast **Verkooporder** > **Beheren**.

1. Selecteer **Parameters**, wijzig de standaardwaarde voor **SalesOrderNumber** in **SO50689** > **Toepassen**.

   ![Rapportparameters instellen](media/tutorial-explore-report-server-web-portal/power-bi-report-server-set-parameters.png)

3. Selecteer **Bladeren** om terug te gaan naar de webportal.

### <a name="view-a-paginated-report"></a>Gepagineerd rapport bekijken

1. Selecteer **Sales Order** in de webportal.
 
3.  Het wordt geopend in de parameter **Order** die u hebt ingesteld: **SO50689**. 

    ![Parameter gepagineerd rapport](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated.png)

    U kunt deze parameter, samen met de overige parameters, hier wijzigen zonder dat de standaardwaarden worden gewijzigd.

1. Selecteer **Order** **SO48339** > **Rapport weergeven**.

4. U ziet dat dit pagina 1 van 2 is. Selecteer de pijl-rechts om de tweede pagina te zien. De tabel wordt op die pagina vervolgd.

    ![Pagina 2 van 2 van gepagineerde rapport](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-2-of-2.png)

5. Selecteer **Bladeren** om terug te gaan naar de webportal.

### <a name="edit-a-paginated-report"></a>Gepagineerd rapport bewerken

U kunt gepagineerde rapporten bewerken in Report Builder, dat u rechtstreeks vanuit de browser kunt starten.

1. Selecteer in de webportal **Meer opties** (...) naast **Verkooporder** > **Bewerken in Report Builder**.

1. Selecteer **Toestaan** zodat deze website een programma op uw computer kan openen.

1. Het rapport Sales Order wordt geopend in de ontwerpweergave van Report Builder.

    ![Ontwerpweergave, gepagineerd rapport](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-design-view.png)

1. Selecteer **Uitvoeren** om een voorbeeld van het rapport te bekijken.

    ![Voorbeeld van gepagineerd rapport bekijken](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-preview.png)

5. Sluit Report Builder en ga terug naar de browser.

## <a name="view-excel-workbooks"></a>Excel-werkmappen bekijken

U kunt Excel-werkmappen in Excel Online bekijken en ermee werken in Power BI Report Server. 

1. Selecteer de Excel-werkmap **Office Liquidation Sale.xlsx**. U kunt om referenties worden gevraagd. Selecteer **Annuleren**. 
    De map wordt in de webportal geopend.
1. Selecteer **Apparaat** in de slicer.

    ![Excel Online in webportal](media/tutorial-explore-report-server-web-portal/power-bi-report-server-excel-online.png)

1. Selecteer **Bladeren** om terug te gaan naar de webportal.

## <a name="clean-up-resources"></a>Resources opschonen

Als u deze zelfstudie hebt voltooid, verwijdert u de resourcegroep, de virtuele machine en alle gerelateerde resources. 

- Selecteer hiertoe de resourcegroep voor de VM en selecteer **Verwijderen**.

## <a name="next-steps"></a>Volgende stappen

In deze zelfstudie hebt u een VM gemaakt met Power BI Report Server. U hebt enkele functies van de webportal uitgeprobeerd en een Power BI- en een gepagineerd rapport geopend in de bijbehorende editors. Op deze VM zijn de SQL Server Analysis Services-gegevensbronnen geïnstalleerd, zodat u uw eigen Power BI en gepagineerde rapporten kunt maken met die gegevensbronnen. 

Als u meer informatie zoekt over het maken van rapporten voor Power BI Report Server, kunt u doorgaan.

> [!div class="nextstepaction"]
> [Een Power BI-rapport maken voor Power BI Report Server](./quickstart-create-powerbi-report.md)



