---
title: Problemen met Power BI Gateway - Personal oplossen
description: Problemen met Power BI Gateway - Personal oplossen
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 5/06/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: bc6eaccc2976266102dcca0d20df73df810fa5f3
ms.sourcegitcommit: bf535771c9ef495f9bb658569403fa5e3dd82e6a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65853628"
---
# <a name="troubleshooting-power-bi-gateway---personal"></a>Problemen met Power BI Gateway - Personal oplossen
De volgende secties zijn doorlopen van enkele veelvoorkomende problemen die u tegenkomt mogelijk wanneer u de Power BI Gateway-Personal.

> [!NOTE]
> De huidige versie van de gateway voor persoonlijk gebruik is de **On-premises gegevensgateway (persoonlijk)**. Werk uw installatie bij om deze versie te gebruiken.
> 
> 

## <a name="update-to-the-latest-version"></a>Bijwerken naar de nieuwste versie
Heel wat problemen kunnen surface als de gatewayversie verouderd is.  Het is een goede en gangbare praktijk om ervoor te zorgen dat u zich in de meest recente versie. Als u kunt de gateway nog niet hebt bijgewerkt, voor een maand of langer, Overweeg de installatie van de meest recente versie van de gateway. Bekijk vervolgens als het probleem zich voordoet.

## <a name="installation"></a>Installatie
**Persoonlijke gateway is 64-bits** -als uw computer 32-bits is, kunt u de persoonlijke gateway niet installeren. Het besturingssysteem is 64-bits versie. Een 64-bits versie van Windows installeren of de persoonlijke gateway installeren op een 64-bits computer.

**Persoonlijke gateway niet kan worden geïnstalleerd als een service, zelfs als u een lokale beheerder voor de computer zijn** -installatie kan mislukken als de gebruiker zich in de lokale beheerdersgroep van de computer, maar Groepsbeleid niet toestaan dat deze gebruikersnaam aanmelden als een de service. Op dit moment, zorg ervoor dat het groepsbeleid waarmee een gebruiker zich aanmeldt als een service. Er wordt gewerkt aan een oplossing voor dit probleem. [Meer informatie](https://technet.microsoft.com/library/cc739424.aspx)

**Time-out voor bewerking** -dit bericht is gebruikelijk als de computer (fysieke machine of virtuele machine) waarop u de persoonlijke gateway installeert een processor met één kern heeft. Sluit alle toepassingen af en beëindig alle niet-essentiële processen en probeer de installatie vervolgens opnieuw.

**Data Management Gateway of Analysis Services-Connector kan niet worden geïnstalleerd op dezelfde computer als de persoonlijke gateway** : als u hebt al een Analysis Services Connector of Data Management Gateway is geïnstalleerd, moet u eerst de Connector verwijderen of de gateway. Probeer vervolgens de persoonlijke gateway installeert.

> [!NOTE]
> Als u een probleem tijdens de installatie ondervindt, krijgt u de installatielogboeken informatie waarmee u kunt het probleem oplossen. Zie voor meer informatie, [installatielogboeken](#SetupLogs).
> 
> 

 **Proxyconfiguratie** ziet u mogelijk problemen met de configuratie van de persoonlijke gateway als uw omgeving, het gebruik van een proxy moet. Meer informatie over het configureren van proxygegevens kunt u lezen in [Configuring proxy settings for the on-premises data gateway](service-gateway-proxy.md) (Proxy-instellingen configureren voor Power BI-gateways).

## <a name="schedule-refresh"></a>Planning vernieuwen
**Fout: De referenties die zijn opgeslagen in de cloud ontbreken.**

U kunt deze fout krijgen in de instellingen voor \<gegevensset\> als u een geplande vernieuwing hebt verwijderd en opnieuw installeren van de persoonlijke gateway. Wanneer u een persoonlijke gateway verwijdert, worden de referenties van de gegevensbron voor een gegevensset die wordt geconfigureerd voor vernieuwen verwijderd uit de Power BI-service.

**Oplossing:** Ga in Power BI naar de instellingen voor het vernieuwen van een gegevensset. Schakel in gegevensbronnen beheren voor elke gegevensbron met een fout **referenties bewerken** en opnieuw aanmelden bij de gegevensbron.

**Fout: De opgegeven referenties voor de gegevensset zijn ongeldig. Werk de referenties bij via een vernieuwingsbewerking of in het dialoogvenster Instellingen voor gegevensbron om door te gaan.**

**Oplossing**: Als u een bericht over referenties krijgt, kan dit het volgende betekenen:

* Zorg ervoor dat de gebruikersnamen en wachtwoorden voor de aanmelding bij gegevensbronnen up-to-date zijn. Ga in Power BI naar de instellingen voor het vernieuwen van de gegevensset. Selecteer in gegevensbronnen beheren **referenties bewerken** om bij te werken van de referenties voor de gegevensbron.
* Mashups tussen een cloudbron en een on-premises bron, in één query, niet vernieuwd in de persoonlijke gateway als een van de bronnen OAuth gebruikt voor verificatie. Een voorbeeld van dit probleem is een mashup tussen CRM Online en een lokale SQL Server. De mashup is mislukt omdat voor CRM Online OAuth vereist is.
  
  Deze fout is een bekend probleem en wordt worden bekeken. Als tijdelijke oplossing voor het probleem, hebt u een afzonderlijke query voor de cloudbron en de on-premises bron. Vervolgens gebruikt u een samenvoegen of toevoegquery deze vervolgens te combineren.

**Fout: Niet-ondersteunde gegevensbron.**

**Oplossing:** Als u een bericht over een niet-ondersteunde gegevensbron krijgt in het venster met instellingen voor gepland vernieuwen, kan dit het volgende betekenen: 

* De gegevensbron wordt momenteel niet ondersteund voor vernieuwen in Power BI. 
* De Excel-werkmap bevat een gegevensmodel, alleen werkbladgegevens. Power BI ondersteunt momenteel alleen vernieuwen als de geüploade Excel-werkmap een gegevensmodel bevat. Wanneer u gegevens in Excel importeert met behulp van Power Query, vergeet dan niet om de optie te kiezen voor het laden van gegevens in het gegevensmodel. Deze optie zorgt ervoor dat gegevens worden geïmporteerd in een gegevensmodel. 

**Fout: [Kan gegevens niet combineren] &lt;queryonderdeel&gt;/&lt;... &gt; / &lt;... &gt; wil toegang tot gegevensbronnen met privacyniveaus die niet samen kunnen worden gebruikt. Bouw deze gegevenscombinatie opnieuw.**

**Oplossing**: Deze fout is vanwege de privacyniveaubeperkingen en de soorten gegevensbronnen die u gebruikt.

**Fout: Fout in de gegevensbron: De waarde '\[tabel\]' kan niet worden geconverteerd naar type tabel.**

**Oplossing**: Deze fout is vanwege de privacyniveaubeperkingen en de soorten gegevensbronnen die u gebruikt.

**Fout: Er is onvoldoende ruimte voor deze rij.**

Deze fout treedt op als u een enkele rij groter is dan 4 MB in grootte hebt. De rij in de gegevensbron zoeken en deze wegfilteren of de grootte voor die rij verkleinen.

## <a name="data-sources"></a>Gegevensbronnen
**Ontbrekende gegevensprovider** : de persoonlijke gateway is alleen 64-bits versie. De gateway vereist dat een 64-bits versie van de gegevensproviders is geïnstalleerd op dezelfde computer als waarop de persoonlijke gateway is geïnstalleerd. Als de gegevensbron in de gegevensset bijvoorbeeld Microsoft Access is, moet u de 64-bits ACE-provider installeren op de computer waarop u de persoonlijke gateway hebt geïnstalleerd.  

>[!NOTE]
>Als u een 32-bits versie van Excel hebt, kunt u een 64-bits versie ACE-provider niet installeren op dezelfde computer.

**Windows-verificatie wordt niet ondersteund voor Access-database**. Power BI ondersteunt momenteel alleen anonieme verificatie voor tot Access-databases. We werken aan het inschakelen van Windows-verificatie voor Access-database.

**Aanmeldingsfout bij invoeren van referenties voor een gegevensbron** -als u een foutmelding als deze krijgt wanneer u Windows-referenties voor een gegevensbron invoert, kunt u nog steeds mogelijk een oudere versie van de persoonlijke gateway. [Installeer de nieuwste versie van Power BI Gateway - Personal](https://powerbi.microsoft.com/gateway/).

  ![](media/service-admin-troubleshooting-power-bi-personal-gateway/pbi_pg_credentialserror.jpg.png)

**Fout: Aanmeldingsfout bij selecteren van Windows-verificatie voor een gegevensbron met behulp van ACE OLEDB**. Als u de onderstaande fout krijgt bij het invoeren van referenties voor een gegevensbron die een ACE OLEDB-provider gebruikt:

![](media/service-admin-troubleshooting-power-bi-personal-gateway/aceoledberror.png)

Power BI ondersteunt momenteel geen Windows-verificatie voor een gegevensbron met ACE OLEDB-provider.

**Oplossing:** U kunt deze fout omzeilen, kunt u **anonieme verificatie**. Voor oudere ACE OLE DB-providers zijn anonieme referenties gelijk zijn aan Windows-referenties.

## <a name="tile-refresh"></a>Tegels vernieuwen
Als u een fout opgetreden bij het vernieuwen van dashboardtegels ontvangt, raadpleegt u het volgende artikel.

[Problemen met tegelfouten oplossen](refresh-troubleshooting-tile-errors.md)

## <a name="tools-for-troubleshooting"></a>Hulpmiddelen voor probleemoplossing
### <a name="refresh-history"></a>Geschiedenis vernieuwen
**Geschiedenis vernieuwen** kunt u zien welke fouten zijn opgetreden en vindt u nuttige gegevens als u wilt een ondersteuningsaanvraag maken. U kunt zowel geplande als vernieuwingen op aanvraag bekijken. Hier volgt hoe u krijgen tot de **Geschiedenis vernieuwen**.

1. Ga in het navigatiedeelvenster van Power BI naar **Gegevenssets**, selecteer een gegevensset &gt; Menu openen &gt; **Vernieuwen plannen**.
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh.png)
1. In **-instellingen voor...** , selecteer **Geschiedenis vernieuwen**.  
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh-2.png)
   
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/refresh-history.png)

### <a name="event-logs"></a>Gebeurtenislogboeken
Verschillende gebeurtenislogboeken kan gegevens bieden. De eerste twee **Data Management Gateway** en **PowerBIGateway**, zijn beschikbaar als u een beheerder op de machine bent.  Als u geen beheerder bent en u de persoonlijke Gateway gebruikt, ziet u de logboekvermeldingen in het **toepassing** log.

De logboeken **Data Management Gateway** en **PowerBIGateway** staan onder **Logboeken Toepassingen en Services**.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/event-logs.png)

### <a name="fiddler-trace"></a>Traceren met Fiddler
[Fiddler](http://www.telerik.com/fiddler) is een gratis hulpprogramma van Telerik waarmee u het HTTP-verkeer kunt controleren. Hier ziet u de communicatie met de Power BI-service op de clientcomputer. Deze communicatie mogelijk fouten en andere verwante informatie weergeven.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/fiddler.png)

<a name="SetupLogs"></a>

### <a name="setup-logs"></a>Installatielogboeken
Als de **persoonlijke Gateway**, niet kan worden geïnstalleerd, ziet u een koppeling naar het setup-logboek weergeven. Het setup-logboek kunt u details over de fout weergegeven. Deze logboeken zijn logboeken voor Windows installeren, ook wel bekend als MSI-Logboeken. Deze logboeken kunnen nogal ingewikkeld zijn en moeilijk te lezen. Normaal gesproken de resulterende fout onderaan wordt weergegeven, maar het bepalen van de oorzaak van de fout niet trivial voor. Deze kan namelijk ook het gevolg zijn van fouten in een ander logboek of van een fout die eerder in het logboek staat.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-log.png)

Of, gaat u naar uw **map Temp** (% temp %) en bestanden zoeken die met beginnen **Power\_BI\_**.

> [!NOTE]
> Als u naar %temp% gaat, komt u misschien terecht in een submap van Temp. De **Power\_BI\_**  bestanden zich in de hoofdmap van de map temp.  U moet mogelijk een of twee niveaus omhoog.
> 
> 

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-logs2.png)

## <a name="next-steps"></a>Volgende stappen
[Configuring proxy settings for the on-premises data gateway](service-gateway-proxy.md) (Proxy-instellingen voor de on-premises gegevensgateway configureren)  
[Data refresh in Power BI](refresh-data.md) (Gegevens vernieuwen in Power BI)  
[Power BI Gateway - Personal](service-gateway-personal-mode.md)  
[Problemen met tegelfouten oplossen](refresh-troubleshooting-tile-errors.md)  
[Problemen met de on-premises gegevensgateway oplossen](service-gateway-onprem-tshoot.md)  
Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

