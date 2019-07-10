---
title: Een Power BI on-premises gateway beheren
description: Informatie over het beheren van een gateway, zodat u verbinding kunt maken met on-premises gegevens in Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 04/18/2018
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Gateways
ms.openlocfilehash: 8acc0e403c983de79657cd01a7aa7f458bfb01ad
ms.sourcegitcommit: 9278540467765043d5cb953bcdd093934c536d6d
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67559048"
---
# <a name="manage-a-power-bi-on-premises-gateway"></a>Een Power BI on-premises gateway beheren

Nadat u [een Power BI-gegevensgateway hebt geïnstalleerd](service-gateway-install.md), beheert u deze op basis van uw vereisten. In dit onderwerp leert u hoe u: gegevensbronnen en gebruikers toevoegt en verwijdert; een gateway opnieuw opstart; en een gateway migreert, herstelt, overneemt en verwijdert.

U kunt een gateway beheren via het gedeelte **Gateways beheren** van de Power BI-service in de gateway-app op uw lokale computer en ook met PowerShell-scripts. Dit artikel richt zich op de Power BI-service.

Als u zojuist een gateway hebt geïnstalleerd, wordt u aangeraden vervolgens [een gegevensbron toe te voegen](#add-a-data-source) en vervolgens [gebruikers toe te voegen](#add-users-to-a-data-source), zodat ze de gegevensbron kunnen openen.


## <a name="manage-data-sources"></a>Gegevensbronnen beheren

Power BI biedt ondersteuning voor veel on-premises gegevensbronnen en elke bron heeft zijn eigen vereisten. Een gateway kan worden gebruikt voor een enkele gegevensbron of meerdere gegevensbronnen. In dit voorbeeld leert u hoe u SQL Server toevoegt als gegevensbron, maar de stappen komen overeen met die voor andere gegevensbronnen.

> [!NOTE]
> Gateway-beheerders kunnen nu meerdere gegevensbronnen met elk een andere referentie maken die verbinding maken met dezelfde bron en gebruikers aan deze gegevensbronnen toevoegen op basis van hun toegangsniveau.

### <a name="add-a-data-source"></a>Een gegevensbron toevoegen

1. Selecteer rechtsboven in de Power BI-service het tandwielpictogram ![tandwielpictogram Instellingen](media/service-gateway-manage/icon-gear.png) > **Gateways beheren**.

    ![Gateways beheren](media/service-gateway-manage/manage-gateways.png)

1. Selecteer een gateway > **Gegevensbron toevoegen** of ga naar Gateways > **Gegevensbron toevoegen**.

    ![Gegevensbron toevoegen](media/service-gateway-manage/add-data-source.png)

1. Selecteer het **type gegevensbron**.

    ![SQL Server selecteren](media/service-gateway-manage/select-sql-server.png)


1. Voer gegevens voor de gegevensbron in. In dit voorbeeld zijn deze **Server**, **Database** en overige gegevens.  

    ![Instellingen voor gegevensbron](media/service-gateway-manage/data-source-settings.png)

1. Voor SQL Server kiest u een **Verificatiemethode** van **Windows** of **Basic** (SQL-verificatie).  Als u **Basic** kiest, voert u de referenties voor de gegevensbron in.

1. Selecteer **Testverbinding overslaan** als deze gegevensbron momenteel niet beschikbaar is of traag werkt. Het maken van de gegevensbron kan anders mogelijk mislukken.

    > [!NOTE]
    > Het overslaan van de testverbinding wordt niet ondersteund voor Analysis Services.

1. Onder **Geavanceerde instellingen** kunt u optioneel het [privacyniveau](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540) voor de gegevensbron configureren (geldt niet voor [DirectQuery](desktop-directquery-about.md)).

    ![Geavanceerde instellingen](media/service-gateway-manage/advanced-settings.png)

1. Selecteer **Toevoegen**. U ziet *Verbinding gemaakt* als de procedure is voltooid.

    ![Verbinding gemaakt](media/service-gateway-manage/connection-successful.png)

U kunt deze gegevensbron nu gebruiken om gegevens uit SQL Server op te nemen in uw Power BI-dashboards en -rapporten.

### <a name="remove-a-data-source"></a>Een gegevensbron verwijderen

U kunt een gegevensbron verwijderen als u deze niet meer nodig hebt. Houd er rekening mee dat als u een gegevensbron verwijdert, de dashboards en rapporten die afhankelijk zijn van de gegevensbron niet meer werken.

Ga naar de gegevensbron en selecteer **Verwijderen** als u een gegevensbron wilt verwijderen.

![Een gegevensbron verwijderen](media/service-gateway-manage/remove-data-source.png)


## <a name="manage-users-and-administrators"></a>Gebruikers en beheerders beheren

Als u een gegevensbron aan een gateway hebt toegevoegd, geeft u gebruikers en beveiligingsgroepen met e-mailfunctie toegang tot die bepaalde gegevensbron (niet tot de hele gateway). Met de gebruikerslijst voor de gegevensbron wordt alleen gecontroleerd wie er rapporten mag publiceren die gegevens uit de gegevensbron bevatten. Rapporteigenaren kunnen dashboards, inhoudspakketten en apps maken en deze delen met andere gebruikers.

U kunt gebruikers en beveiligingsgroepen ook administratieve toegang tot de gateway geven.


### <a name="add-users-to-a-data-source"></a>Gebruikers toevoegen aan een gegevensbron

1. Selecteer rechtsboven in de Power BI-service het tandwielpictogram ![tandwielpictogram Instellingen](media/service-gateway-manage/icon-gear.png) > **Gateways beheren**.

2. Selecteer de gegevensbron waar u gebruikers aan wilt toevoegen.

3. Selecteer **Gebruikers** en voer een gebruiker uit uw organisatie in die u toegang wilt verlenen tot de geselecteerde gegevensbron. In het volgende scherm kunt u zien dat ik Menna en Rolf heb toegevoegd.

    ![Tabblad Gebruikers](media/service-gateway-manage/users-tab.png)

4. Selecteer **Toevoegen** en het toegevoegde lid wordt in het vak weergegeven.

    ![Gebruiker toevoegen](media/service-gateway-manage/add-user.png)

Zo eenvoudig werkt dat. Houd er rekening mee dat u gebruikers moet toevoegen aan elke gegevensbron waartoe u toegang wilt verlenen. Elke gegevensbron heeft een afzonderlijke lijst met gebruikers. De gebruikers moeten afzonderlijk worden toegevoegd aan de elke gegevensbron.


### <a name="remove-users-from-a-data-source"></a>Gebruikers uit een gegevensbron verwijderen

Op het tabblad **Gebruikers** voor de gegevensbron kunt u gebruikers en beveiligingsgroepen met e-mail verwijderen die deze gegevensbron gebruiken.

![Gebruiker verwijderen](media/service-gateway-manage/remove-user.png)


### <a name="add-and-remove-administrators"></a>Administrators toevoegen en verwijderen

Op het tabblad **Administrators** voor de gateway kunt u gebruikers (of beveiligingsgroepen met e-mail) toevoegen en verwijderen die de gateway kunnen beheren.

![Tabblad Administrators](media/service-gateway-manage/administrators-tab.png)


## <a name="manage-a-gateway-cluster"></a>Gatewaycluster beheren

Zodra u een cluster van twee of meer gateways maakt, worden alle beheerbewerkingen voor de gateway, zoals het toevoegen van een gegevensbron of het verlenen van beheerdersrechten aan een gateway, toegepast op alle gateways die deel uitmaken van het cluster. 

Wanneer beheerders het menu-item **Gateways beheren** (onder het tandwielpictogram in de **Power BI-service**) gebruiken, zien zij een lijst met geregistreerde clusters van afzonderlijke gateways, maar niet de afzonderlijke gatewayexemplaren die lid van het cluster zijn.

Alle nieuwe aanvragen voor **Geplande vernieuwing** en DirectQuery-bewerkingen worden automatisch doorgestuurd naar het primaire exemplaar van een bepaald gatewaycluster. Als het primaire gatewayexemplaar niet online is, wordt de aanvraag doorgestuurd naar een ander gatewayexemplaar in het cluster.


## <a name="share-a-gateway"></a>Een gateway delen

U kunt gateways niet direct *delen*, maar u kunt wel beheerders toevoegen aan de gateway en u kunt gebruikers toevoegen aan de gegevensbronnen van de gateway. 

Nadat u een gateway hebt geïnstalleerd, bent u de beheerder van die gateway. Dit is een standaardinstelling. Zoals u al eerder zag, kunt u andere personen als beheerders toevoegen. Deze beheerders kunnen gegevensbronnen toevoegen en de gateway configureren en verwijderen.

U kunt ook gebruikers toewijzen aan de gegevensbronnen die u maakt onder elk van uw gateways. Gebruikers kunnen vervolgens die gegevensbronnen gebruiken om Power BI-rapporten te vernieuwen. Ze kunnen echter geen gegevensbronnen of gatewayinstellingen wijzigen.

## <a name="migrate-restore-or-take-over-a-gateway"></a>Gateway migreren, herstellen of overnemen

Voer het installatieprogramma voor de gateway uit op de computer waarop u de gateway wilt migreren, herstellen of overnemen.

1. Download de gateway installeer deze.

2. Als u zich hebt aangemeld bij uw Power BI-account, registreert u de gateway. Selecteer **Een bestaande gateway migreren, herstellen of overnemen** > **Volgende**.

    ![Gateway registreren](media/service-gateway-manage/register-gateway.png)

3. Selecteer een cluster en gateway uit de beschikbare clusters en gateways en voer de herstelsleutel voor de geselecteerde gateway in. Selecteer **Configureren**.

    ![Migreren, herstellen of overnemen](media/service-gateway-manage/migrate-restore-takeover.png)


## <a name="restart-a-gateway"></a>Gateway opnieuw starten

De gateway wordt uitgevoerd als een Windows-service. U kunt deze service net als alle andere Windows-services op meerdere manieren starten en stoppen. Hier volgt hoe u kunt dit kunt doen vanaf de opdrachtprompt.

1. Start een opdrachtprompt met administratorbevoegdheden op de machine waarop de gateway wordt uitgevoerd

2. Voer `net stop PBIEgwService` in om de service te stoppen.

3. Voer `net start PBIEgwService` in om de service opnieuw te starten.


## <a name="remove-a-gateway"></a>Een gateway verwijderen

U kunt een gateway verwijderen als u deze niet meer nodig hebt. Houd er echter rekening mee dat als u een gateway verwijdert, alle bijbehorende gegevensbronnen ook worden verwijderd. De dashboards en rapporten die afhankelijk zijn van deze gegevensbronnen, werken hierdoor ook niet meer.

1. Selecteer rechtsboven in de Power BI-service het tandwielpictogram ![tandwielpictogram Instellingen](media/service-gateway-manage/icon-gear.png) > **Gateways beheren**.

2. Selecteer de gateway > **Verwijderen**
   
   ![Gateway verwijderen](media/service-gateway-manage/remove-gateway.png)


## <a name="next-steps"></a>Volgende stappen

[Richtlijnen voor het implementeren van een gegevensgateway](service-gateway-deployment-guidance.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
