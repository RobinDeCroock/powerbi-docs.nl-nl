---
title: 'Zelfstudie: Verbinding maken met on-premises gegevens in SQL Server'
description: Leer hoe u SQL Server gebruikt als gegevensbron van de gateway, inclusief het vernieuwen van gegevens.
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: tutorial
ms.date: 05/03/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 1c77c272bf5c03ce7df0a5173d194a4c0583ccf2
ms.sourcegitcommit: 3e72c6d564d930304886d51cdf12b8fc166aa33c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/05/2019
ms.locfileid: "67596641"
---
# <a name="refresh-data-from-an-on-premises-sql-server-database"></a>Gegevens vernieuwen in een on-premises SQL Server-database

In deze zelfstudie verkent u manieren voor het vernieuwen van een Power BI-gegevensset uit een relationele database die on-premises bestaat in uw lokale netwerk. Deze zelfstudie maakt specifiek gebruik van een SQL Server-voorbeelddatabase, die Power BI moet benaderen via een on-premises gegevensgateway.

In deze zelfstudie voert u de volgende stappen uit:

> [!div class="checklist"]
> * Een Power BI Desktop-bestand (.pbix) maken en publiceren dat gegevens uit een on-premises SQL Server-database importeert.
> * Gegevensbron- en gegevenssetinstellingen in Power BI configureren voor SQL Server-connectiviteit via een gegevensgateway.
> * Een vernieuwingsschema configureren om te zorgen dat uw Power BI-gegevensset over recente gegevens beschikt.
> * Een vernieuwing van uw gegevensset op aanvraag uitvoeren.
> * De vernieuwingsgeschiedenis controleren om de uitkomsten van eerdere vernieuwingscycli te analyseren.
> * Resources opschonen door artefacten te verwijderen die in deze zelfstudie werden gemaakt.

## <a name="prerequisites"></a>Vereisten

- Registreer voordat u begint een [gratis proefversie van Power BI](https://app.powerbi.com/signupredirect?pbi_source=web) als u dit nog niet hebt gedaan.
- [Installeer Power BI Desktop](https://powerbi.microsoft.com/desktop/) op een lokale computer.
- [Installeer SQL Server](/sql/database-engine/install-windows/install-sql-server) op een lokale computer en herstel de [voorbeelddatabase uit een reservekopie](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak). Raadpleeg [Installatie en configuratie van AdventureWorks](/sql/samples/adventureworks-install-configure) voor meer informatie over AdventureWorks.
- [Installeer een on-premises gegevensgateway](service-gateway-install.md) op dezelfde lokale computer als SQL Server (in productie is het meestal een andere computer).

> [!NOTE]
> Neem contact op met een gatewaybeheerder in uw organisatie als u geen gatewaybeheerder bent en niet zelf een gateway wilt installeren. Deze kan de vereiste gegevensbrondefinitie maken om uw gegevensset te verbinden met uw SQL Server-database.

## <a name="create-and-publish-a-power-bi-desktop-file"></a>Een Power BI Desktop-bestand maken en publiceren

Gebruik de volgende procedure om een eenvoudig Power BI-rapport te maken met behulp van de AdventureWorksDW-voorbeelddatabase. Publiceer het rapport in de Power BI-service, zodat u een gegevensset in Power BI krijgt, die u in volgende stappen kunt configureren en vernieuwen.

1. Selecteer in Power BI Desktop, op het tabblad **Start**, de optie **Gegevens ophalen** \> **SQL Server**.

2. Voer in het dialoogvenster **SQL Server-database** de namen van de **Server** en **Database (optioneel)** in, zorg dat de **Modus voor toegang tot gegevens** op **Importeren** staat en selecteer daarna **OK**.

    ![SQL Server-database](./media/service-gateway-sql-tutorial/sql-server-database.png)

3. Controleer uw **referenties** en selecteer vervolgens **Verbinding maken**.

    > [!NOTE]
    > Zorg dat u de juiste verificatiemethode selecteert en gebruik een account met databasetoegang als u zich niet kunt verifiëren. In testomgevingen kunt u databaseverificatie met een expliciete gebruikersnaam en dito wachtwoord gebruiken. In productieomgevingen gebruikt u meestal Windows-verificatie. Raadpleeg [Problemen met vernieuwingsscenario’s oplossen](refresh-troubleshooting-refresh-scenarios.md) en neem contact op met uw databasebeheerder voor extra ondersteuning.

1. Selecteer **OK** als het dialoogvenster **Ondersteuning voor versleuteling** wordt weergegeven.

2. Selecteer in het dialoogvenster **Navigator** de tabel **DimProduct** en selecteer vervolgens **Laden**.

    ![Gegevensbronnavigator](./media/service-gateway-sql-tutorial/data-source-navigator.png)

3. Selecteer in de Power BI Desktop-**rapportweergave**, in het deelvenster **Visualisaties**, de optie **Gestapeld kolomdiagram**.

    ![Gestapeld kolomdiagram](./media/service-gateway-sql-tutorial/stacked-column-chart.png)

4. Selecteer in het deelvenster **Velden** de velden **EnglishProductName** en **ListPrice** terwijl het kolomdiagram op het rapportcanvas is geopend.

    ![Deelvenster Velden](./media/service-gateway-sql-tutorial/fields-pane.png)

5. Sleep **EndDate** naar **Filters op rapportniveau** en schakel onder **Standaardfilters** alleen het selectievakje voor **(Leeg)** in.

    ![Filters op rapportniveau](./media/service-gateway-sql-tutorial/report-level-filters.png)

    De grafiek moet er nu ongeveer als volgt uitzien.

    ![Voltooid kolomdiagram](./media/service-gateway-sql-tutorial/finished-column-chart.png)

    U ziet dat de vijf **Road-250**-producten worden vermeld met de hoogste prijs. Dit verandert als u later in deze zelfstudie de gegevens bijwerkt en het rapport vernieuwt.

6. Sla het rapport op met de naam 'AdventureWorksProducts.pbix'.

7. Selecteer op het tabblad **Start** **Publiceren** \> **Mijn werkruimte** \> **Selecteren**. Meld u aan bij de Power BI-service wanneer u hierom wordt gevraagd.

8. Selecteer op het scherm **Geslaagd** de optie **‘AdventureWorksProducts.pbix’ openen in Power BI**.

    [Publiceren naar Power BI](./media/service-gateway-sql-tutorial/publish-to-power-bi.png)

## <a name="connect-a-dataset-to-a-sql-server-database"></a>Een gegevensset verbinden met een SQL Server-database

In Power BI Desktop maakt u rechtstreeks verbinding met uw on-premises SQL Server-database, maar de Power BI-service vereist een gegevensgateway om te fungeren als een brug tussen de cloud en uw on-premises netwerk. Volg deze stappen om uw on-premises SQL Server-database als gegevensbron aan een gateway toe te voegen en uw gegevensset vervolgens te verbinden met deze gegevensbron.

1. Meld u aan bij Power BI. Selecteer in de rechterbovenhoek het tandwielpictogram voor instellingen en selecteer vervolgens **Instellingen**.

    ![Power BI-instellingen](./media/service-gateway-sql-tutorial/power-bi-settings.png)

2. Selecteer op het tabblad **Gegevenssets** de gegevensset **AdventureWorksProducts**, zodat u verbinding met uw on-premises SQL Server-database kunt maken via een gegevensgateway.

3. Vouw **Gatewayverbinding** uit en verifieer of er minimaal één gateway wordt vermeld. Raadpleeg het hoofdstuk [Vereisten](#prerequisites) eerder in deze zelfstudie voor een koppeling naar de productdocumentatie voor het installeren en configureren van een gateway als u nog geen gateway hebt.

    ![Gatewayverbinding](./media/service-gateway-sql-tutorial/gateway-connection.png)

4. Vouw onder **Acties** de wisselknop uit om de gegevensbronnen weer te geven en selecteer de koppeling **Toevoegen aan gateway**.

    ![Gegevensbron toevoegen aan gateway](./media/service-gateway-sql-tutorial/add-data-source-gateway.png)

    > [!NOTE]
    > Neem contact op met een gatewaybeheerder in uw organisatie als u geen gatewaybeheerder bent en niet zelf een gateway wilt installeren. Deze kan de vereiste gegevensbrondefinitie maken om uw gegevensset te verbinden met uw SQL Server-database.

5. U moet op het tabblad **Gegevensbroninstellingen** op de beheerpagina **Gateways** de volgende informatie invoeren en verifiëren. Selecteer **Toevoegen**.

    | Optie | Waarde |
    | --- | --- |
    | Naam gegevensbron | AdventureWorksProducts |
    | Gegevensbrontype | SQL Server |
    | Server | De naam van het SQL Server-exemplaar, zoals SQLServer01 (moet identiek zijn aan de naam die u hebt opgegeven in Power BI Desktop). |
    | Database | De naam van uw SQL Server-database, zoals AdventureWorksDW (moet identiek zijn aan de naam die u hebt opgegeven in Power BI Desktop). |
    | Verificatiemethode | Windows of Basic (meestal Windows). |
    | Gebruikersnaam | Het gebruikersaccount dat u gebruikt om verbinding te maken met SQL Server. |
    | Wachtwoord | Het wachtwoord voor het account dat u gebruikt om verbinding te maken met SQL Server. |

    ![Instellingen voor gegevensbron](./media/service-gateway-sql-tutorial/data-source-settings.png)

6. Vouw op het tabblad **Gegevenssets** opnieuw het gedeelte **Gatewayverbinding** uit. Selecteer de gegevensgateway die u hebt geconfigureerd. Deze toont als **Status** dat deze wordt uitgevoerd op de computer waarop u deze hebt geïnstalleerd. Selecteer **Toepassen**.

    ![Gatewayverbinding bijwerken](./media/service-gateway-sql-tutorial/update-gateway-connection.png)

## <a name="configure-a-refresh-schedule"></a>Een vernieuwingsschema configureren

Nu u uw gegevensset in Power BI met uw on-premises SQL Server-database via een gegevensgateway hebt verbonden, moet u deze stappen volgen om een vernieuwingsschema configureren. Door uw gegevensset volgens een planning te vernieuwen, weet u zeker dat uw rapporten en dashboards over de meest recente gegevens beschikken.

1. Open in het linkernavigatievenster **Mijn Werkruimte** \> **Gegevenssets**. Selecteer het beletselteken ( **. . .** ) voor de **AdventureWorksProducts**-gegevensset en selecteer vervolgens **Vernieuwen plannen**.

    > [!NOTE]
    > Zorg dat u het beletselteken voor de gegevensset **AdventureWorksProducts** selecteert, niet het beletselteken voor het rapport met dezelfde naam. Het contextmenu van het **AdventureWorksProducts**-rapport bevat geen optie **Vernieuwen plannen**.

2. Stel Vernieuwen bij de optie **Geplande vernieuwing** onder **Uw gegevens actueel houden** in op **Aan**.

3. Selecteer een geschikte **Vernieuwingsfrequentie**, (in dit voorbeeld **Dagelijks**) en selecteer vervolgens onder **Tijd** de optie **Een ander tijdstip toevoegen** om de gewenste vernieuwingstijd op te geven (in dit voorbeeld 6:30 AM en PM).

    ![Geplande vernieuwing configureren](./media/service-gateway-sql-tutorial/configure-scheduled-refresh.png)

    > [!NOTE]
    > U kunt maximaal 8 dagelijkse tijdvakken configureren als uw gegevensset zich op gedeelde capaciteit bevindt of 48 tijdvakken op Power BI Premium.

4. Laat het selectievakje **Meldingsberichten van mislukte vernieuwingen aan mij verzenden** ingeschakeld en selecteer **Toepassen**.

## <a name="perform-an-on-demand-refresh"></a>Een vernieuwing op aanvraag uitvoeren

Nu u een vernieuwingsschema hebt geconfigureerd, vernieuwt Power BI uw gegevensset op het volgende geplande tijdstip, met een marge van 15 minuten. Als u de gegevens eerder wilt vernieuwen om bijvoorbeeld uw gateway en de configuratie van de gegevensbron te testen, voert u een on-demand vernieuwing uit met behulp van de optie **Nu vernieuwen** in het gegevenssetmenu in het navigatiedeelvenster links. On-demand vernieuwingen hebben geen invloed op de volgende keer dat een geplande vernieuwing plaatsvindt, maar tellen mee voor de dagelijkse vernieuwingslimiet, zoals in het vorige gedeelte werd uitgelegd.

Simuleer ter illustratie een wijziging in de voorbeeldgegevens door de tabel DimProduct in de AdventureWorksDW-database bij te werken met behulp van SQL Server Management Studio (SSMS).

```sql

UPDATE [AdventureWorksDW].[dbo].[DimProduct]
SET ListPrice = 5000
WHERE EnglishProductName ='Road-250 Red, 58'

```

Volg vervolgens deze stappen, zodat de bijgewerkte gegevens via de gatewayverbinding naar de gegevensset en in de rapporten in Power BI kunnen stromen.

1. Selecteer in het linkernavigatievenster in de Power BI-service de optie **Mijn werkruimte** en vouw deze uit.

2. Selecteer onder **Gegevenssets** het beletselteken ( **. . .** ) voor de **AdventureWorksProducts**-gegevensset en selecteer vervolgens **Nu vernieuwen**.

    ![Nu vernieuwen](./media/service-gateway-sql-tutorial/refresh-now.png)

    Merk op dat Power BI in de rechterbovenhoek wordt voorbereid om de aangevraagde vernieuwingsbewerking uit te voeren.

3. Selecteer **Mijn werkruimte \> Rapporten \> AdventureWorksProducts**. Zie hoe de bijgewerkte gegevens worden toegepast en dat het product met de hoogste catalogusprijs nu **Road-250 Red, 58** is.

    ![Bijgewerkt kolomdiagram](./media/service-gateway-sql-tutorial/updated-column-chart.png)

## <a name="review-the-refresh-history"></a>De vernieuwingsgeschiedenis controleren

Er is een goed idee om de resultaten van de laatste vernieuwingcycli periodiek te controleren in de vernieuwingsgeschiedenis. Mogelijk zijn de databasereferenties verlopen of was de geselecteerde gateway offline toen een geplande vernieuwing zou worden uitgevoerd. Volg deze stappen om de vernieuwingsgeschiedenis te beoordelen en te controleren of er sprake is van problemen.

1. Selecteer in de rechterbovenhoek van de Power BI-gebruikersinterface het tandwielpictogram voor instellingen en selecteer vervolgens **Instellingen**.

2. Schakel naar **Gegevenssets** en selecteer de gegevensset die u wilt onderzoeken, zoals **AdventureWorksProducts**.

3. Selecteer de koppeling **Vernieuwingsgeschiedenis** om het dialoogvenster **Vernieuwingsgeschiedenis** te openen.

    ![Koppeling naar Geschiedenis vernieuwen](./media/service-gateway-sql-tutorial/refresh-history-link.png)

4. Merk op hoe u op het tabblad **Gepland** de eerder geplande en aangevraagde vernieuwingen ziet met hun **Begin**- en **Eind**-tijden en de **Status** **Voltooid**, die aangeeft dat Power BI de vernieuwingen met succes heeft uitgevoerd. U kunt bij mislukte vernieuwingen de foutmelding zien en foutdetails onderzoeken.

    ![Geschiedenisgegevens vernieuwen](./media/service-gateway-sql-tutorial/refresh-history-details.png)

    > [!NOTE]
    > Het tabblad OneDrive is alleen relevant voor gegevenssets die zijn verbonden met Power BI Desktop-bestanden, Excel-werkmappen of CSV-bestanden in OneDrive of SharePoint Online. Meer uitleg daarover vindt u in [Gegevens vernieuwen in Power BI](refresh-data.md).

## <a name="clean-up-resources"></a>Resources opschonen

Verwijder de database in SQL Server Management Studio (SSMS) als u de voorbeeldgegevens niet meer wilt gebruiken. Verwijder de gegevensbron in uw gegevensgateway als u de SQL Server-gegevensbron niet wilt gebruiken. Overweeg ook om de gegevensgateway te verwijderen als u deze alleen installeerde om deze zelfstudie te kunnen uitvoeren. U moet ook de AdventureWorksProducts-gegevensset en het AdventureWorksProducts-rapport verwijderen dat Power BI maakte toen u het bestand AdventureWorksProducts.pbix uploadde.

## <a name="next-steps"></a>Volgende stappen

In deze zelfstudie hebt u verkend hoe u gegevens uit een on-premises SQL Server-database in een Power BI-gegevensset kunt importeren en hoe u deze gegevensset volgens een planning en op verzoek kunt vernieuwen om de rapporten en dashboards die van deze gegevensset gebruikmaken actueel te houden in Power BI. U kunt nu meer leren over het beheren van gegevensgateways en gegevensbronnen in Power BI. Het is mogelijk ook een goed idee het conceptuele artikel Gegevens vernieuwen in Power BI door te nemen.

- [Een Power BI on-premises gateway beheren](service-gateway-manage.md)
- [Uw gegevensbron beheren - importeren/geplande vernieuwing](service-gateway-enterprise-manage-scheduled-refresh.md)
- [Gegevens vernieuwen in Power BI](refresh-data.md)
