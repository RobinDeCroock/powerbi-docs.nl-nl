---
title: Een gateway-gegevensbron toeveogen of verwijderen
description: Meer informatie over het toevoegen van gegevensbronnen aan een on-premises gateway in Power BI.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 11/03/2020
ms.custom: seodec18
LocalizationGroup: Gateways
ms.openlocfilehash: 55cdbfbe0572986de455ddb05c342af9e019de42
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96402841"
---
# <a name="add-or-remove-a-gateway-data-source"></a>Een gateway-gegevensbron toeveogen of verwijderen

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

Power BI biedt ondersteuning voor veel [on-premises gegevensbronnen](power-bi-data-sources.md) en elke bron heeft zijn eigen vereisten. Een gateway kan worden gebruikt voor een enkele gegevensbron of meerdere gegevensbronnen. In dit voorbeeld laten we u zien hoe u SQL Server als gegevensbron kunt toevoegen. De stappen zijn ongeveer hetzelfde bij andere gegevensbronnen.

De meeste beheerbewerkingen voor gegevensbronnen kunnen ook worden uitgevoerd met behulp van API's. Zie [REST API's (gateways)](/rest/api/power-bi/gateways) voor meer informatie.

Als u nog geen gateway hebt geïnstalleerd, raadpleegt u [Een on-premises gegevensgateway installeren](/data-integration/gateway/service-gateway-install) om aan de slag te gaan.

## <a name="add-a-data-source"></a>Een gegevensbron toevoegen

1. Selecteer in de paginaheader van de Power BI-service **Instellingen** ![het tandwielpictogram Instellingen](media/service-gateway-data-sources/icon-gear.png) > **Gateways beheren**.

    ![Gateways beheren](media/service-gateway-data-sources/manage-gateways.png)

2. Selecteer een gateway en selecteer vervolgens **Gegevensbron toevoegen**. U kunt de headertekst **GEGEVENSBRON TOEVOEGEN** selecteren of de cursor over het gedeelte naast de gatewayvermelding bewegen om het menu Meer opties weer te geven.

    ![Gegevensbron toevoegen](media/service-gateway-data-sources/add-data-source.png)

3. Wijs een naam toe aan uw gegevensbron en selecteer vervolgens het **gegevensbrontype**. In dit voorbeeld kiezen we SQL Server.

    ![SQL-server selecteren](media/service-gateway-data-sources/select-sql-server.png)

4. Voer gegevens over de gegevensbron in. Geef voor SQL Server de **server** en **database** op.

    ![Gegevensbroninstellingen](media/service-gateway-data-sources/data-source-settings.png)

5. Selecteer een **verificatiemethode** die u wilt gebruiken om verbinding te maken met de gegevensbron. Voor SQL Server kiest u **Windows** of **Basic** (SQL-verificatie). Voer de referenties voor de gegevensbron in.

   :::image type="content" source="media/service-gateway-data-sources/basic-auth.png" alt-text="Instellingen voor basisverificatie.":::

    > [!NOTE]
    > Als de geselecteerde verificatiemethode OAuth is, kan een query die langer wordt uitgevoerd dan het verloopbeleid voor het OAuth-token mislukken.

6. Onder **Geavanceerde instellingen** kunt u [Eenmalige aanmelding (SSO)](service-gateway-sso-overview.md) voor uw gegevensbron configureren. 

    ![geavanceerde instellingen](media/service-gateway-data-sources/advanced-settings-02.png)

    U kunt **Eenmalige aanmelding via Kerberos gebruiken voor DirectQuery-query's** of **Eenmalige aanmelding via Kerberos gebruiken voor DirectQuery- en Import-query's** configureren voor rapporten die op DirectQuery zijn gebaseerd, en **Eenmalige aanmelding gebruiken via Kerberos voor DirectQuery- en Import-query's** configureren voor rapporten op basis van vernieuwen.

    Als u de optie **Eenmalige aanmelding via Kerberos gebruiken voor DirectQuery-query's** gebruikt en deze gegevensbron gebruikt voor een op DirectQuery gebaseerd rapport, wordt gebruikgemaakt van de referenties van de gebruiker die zich aanmeldt bij de Power BI-service. Voor een rapport op basis van vernieuwen worden de referenties gebruikt die u invoert in de velden **Gebruikersnaam** en **Wachtwoord**.

    Als u **Eenmalige aanmelding via Kerberos gebruiken voor DirectQuery- en Import-query's** gebruikt, hoeft u geen referenties op te geven. Als deze gegevensbron wordt gebruikt voor een op DirectQuery gebaseerd rapport, wordt gebruikgemaakt van de gebruiker die is toegewezen aan de (Azure) Active Directory-gebruiker die zich aanmeldt bij de Power BI-service.  Voor een rapport op basis van vernieuwen wordt de beveiligingscontext van de eigenaar van de gegevensset gebruikt

    > [!NOTE]
    >SSO voor Import-query's is alleen beschikbaar voor de lijst met SSO-gegevensbronnen die gebruikmaken van [Beperkte Kerberos-delegering](service-gateway-sso-kerberos.md).

7. Onder **Geavanceerde instellingen** kunt u optioneel het [privacyniveau](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540) voor uw gegevensbron configureren (geldt niet voor [DirectQuery](desktop-directquery-about.md)).

    :::image type="content" source="media/service-gateway-data-sources/privacy-level.png" alt-text="Selecties van het privacyniveau.":::

8. Selecteer **Toevoegen**. U ziet *Verbinding gemaakt* als de procedure is voltooid.

    ![Verbinding gemaakt](media/service-gateway-data-sources/connection-successful.png)

U kunt deze gegevensbron nu gebruiken om gegevens uit SQL Server op te nemen in uw Power BI-dashboards en -rapporten.

## <a name="remove-a-data-source"></a>Een gegevensbron verwijderen

U kunt een gegevensbron verwijderen als u deze niet meer nodig hebt. Als u een gegevensbron verwijdert, werken de dashboards en rapporten die afhankelijk zijn van de gegevensbron niet meer.

Ga naar de gegevensbron en selecteer vervolgens in het menu Meer opties **Verwijderen** als u een gegevensbron wilt verwijderen. Het menu Meer opties wordt weergegeven wanneer u de cursor over het gedeelte naast de naam van de gegevensbron beweegt.

![Een gegevensbron verwijderen](media/service-gateway-data-sources/remove-data-source.png)

## <a name="use-the-data-source-for-scheduled-refresh-or-directquery"></a>De gegevensbron gebruiken voor geplande vernieuwing of DirectQuery

Nadat u de gegevensbron hebt gemaakt, is deze beschikbaar voor gebruik met zowel DirectQuery-verbindingen als via geplande vernieuwing. Meer informatie over het instellen van geplande vernieuwing vindt u in [Geplande vernieuwing configureren](refresh-scheduled-refresh.md).

> [!NOTE]
>De servernaam en databasenaam die worden gebruikt voor Power BI Desktop en de aan de on-premises gegevensgateway toegevoegde gegevensbron moeten overeenkomen.

De koppeling tussen uw gegevensset en de gegevensbron in de gateway is gebaseerd op uw server- en databasenaam. Deze namen moeten overeenkomen. Als u bijvoorbeeld een IP-adres als servernaam gebruikt, moet u dit IP-adres in Power BI Desktop gebruiken voor de gegevensbron in de gatewayconfiguratie. Als u in Power BI Desktop *SERVER\EXEMPLAAR* gebruikt, moet u daar ook gebruik van maken in de gegevensbron die u voor de gateway configureert.

Als u wordt vermeld op het tabblad **Gebruikers** voor de gegevensbron die is geconfigureerd in de gateway, en als de server- en databasenaam overeenkomen, wordt de gateway als optie vermeld om te gebruiken bij geplande vernieuwing.

![Gatewayverbinding](media/service-gateway-data-sources/gateway-connection.png)

> [!WARNING]
> Als uw gegevensset meerdere gegevensbronnen bevat, moet elke gegevensbron aan de gateway worden toegevoegd. Als een of meer gegevensbronnen niet aan de gateway zijn toegevoegd, wordt de gateway niet weergegeven omdat deze niet beschikbaar is voor geplande vernieuwing.

### <a name="limitations"></a>Beperkingen

OAuth is uitsluitend een ondersteund verificatieschema voor aangepaste connectoren voor de on-premises gegevensgateway. U kunt geen andere gegevensbronnen toevoegen waarvoor OAuth vereist is. Als uw gegevensset een gegevensbron bevat waarvoor OAuth vereist is en als deze gegevensbron geen aangepaste connector is, kunt u de gateway niet gebruiken voor geplande vernieuwing.

## <a name="manage-users"></a>Gebruikers beheren

Als u een gegevensbron aan een gateway hebt toegevoegd, geeft u gebruikers en beveiligingsgroepen met e-mailfunctie toegang tot die bepaalde gegevensbron (niet tot de hele gateway). Met de toegangslijst voor de gegevensbron wordt alleen gecontroleerd wie er rapporten mag publiceren die gegevens uit de gegevensbron bevatten. Rapporteigenaren kunnen dashboards, inhoudspakketten en apps maken en deze delen met andere gebruikers.

U kunt gebruikers en beveiligingsgroepen ook administratieve toegang tot de gateway geven.

> [!NOTE]
> Gebruikers met toegang tot de gegevensbron kunnen gegevenssets koppelen aan de gegevensbron en verbinding maken op basis van de beveiligingsopties (de opgeslagen referenties of eenmalige aanmelding) die zijn geselecteerd tijdens het maken van een gegevensbron.

### <a name="add-users-to-a-data-source"></a>Gebruikers toevoegen aan een gegevensbron

1. Selecteer in de paginaheader van de Power BI-service **Instellingen** ![het tandwielpictogram Instellingen](media/service-gateway-data-sources/icon-gear.png) > **Gateways beheren**.

2. Selecteer de gegevensbron waaraan u gebruikers wilt toevoegen.

3. Selecteer **Gebruikers** en voer de gebruikers en voor e-mailberichten ingeschakelde beveiligingsgroepen in voor uw organisatie die toegang krijgen tot de geselecteerde gegevensbron. Selecteer **Toevoegen**, waarna de naam van het toegevoegde lid aan de lijst met personen wordt toegevoegd die rapporten kunnen publiceren waarin deze gegevensbron wordt gebruikt.

    ![Gebruiker toevoegen](media/service-gateway-data-sources/add-user.png)

Houd er rekening mee dat u gebruikers moet toevoegen aan elke gegevensbron waartoe u toegang wilt verlenen. Elke gegevensbron heeft een afzonderlijke lijst met gebruikers. Voeg gebruikers afzonderlijk toe aan elke gegevensbron.

### <a name="remove-users-from-a-data-source"></a>Gebruikers uit een gegevensbron verwijderen

Op het tabblad **Gebruikers** voor de gegevensbron kunt u gebruikers en beveiligingsgroepen verwijderen die deze gegevensbron gebruiken.

![Gebruiker verwijderen](media/service-gateway-data-sources/remove-user.png)

## <a name="store-encrypted-credentials-in-the-cloud"></a>Versleutelde referenties opslaan in de cloud

Wanneer u een gegevensbron aan de gateway toevoegt, moet u referenties opgeven voor de gegevensbron. Alle query's over de gegevensbron worden uitgevoerd met deze referenties. De referenties zijn veilig versleuteld. Voordat de referenties worden opgeslagen in de cloud, worden ze versleuteld met behulp van symmetrische codering zodat ze in de cloud niet kunnen worden ontsleuteld. De referenties worden verzonden naar de on-premises machine waarop de gateway wordt uitgevoerd, waar ze worden ontsleuteld als de gegevensbronnen worden geopend.

## <a name="list-of-available-data-source-types"></a>Lijst met beschikbare typen gegevensbronnen

Zie [Power BI data sources](power-bi-data-sources.md) (Gegevensbronnen voor Power BI) voor meer informatie over welke gegevensbronnen worden ondersteund binnen de on-premises gegevensgateway.

## <a name="next-steps"></a>Volgende stappen

* [Manage your data source - Analysis Services](service-gateway-enterprise-manage-ssas.md) (Uw gegevensbron beheren - Analysis Services)
* [Manage your data source - SAP HANA](service-gateway-enterprise-manage-sap.md) (Uw gegevensbron beheren - SAP HANA)
* [Manage your data source - SQL Server](service-gateway-enterprise-manage-sql.md) (Uw gegevensbron beheren - SQL Server)
* [Manage your data source - Oracle](service-gateway-onprem-manage-oracle.md) (Gegevensbron beheren - Oracle)
* [Uw gegevensbron beheren - importeren/geplande vernieuwing](service-gateway-enterprise-manage-scheduled-refresh.md)
* [Richtlijnen voor het implementeren van een gegevensgateway](service-gateway-deployment-guidance.md)

Hebt u nog vragen? Misschien dat de [Power BI-community](https://community.powerbi.com/) het antwoord weet.
