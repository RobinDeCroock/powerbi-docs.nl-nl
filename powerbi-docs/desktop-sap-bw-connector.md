---
title: De SAP BW Connector in Power BI Desktop gebruiken
description: De SAP BW Connector in Power BI Desktop gebruiken
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: af227d2bcbbba2a27804ec74f14003f54aa89dde
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514681"
---
# <a name="use-the-sap-bw-connector-in-power-bi-desktop"></a>De SAP BW Connector in Power BI Desktop gebruiken
Met Power BI Desktop hebt u toegang tot gegevens van **SAP Business Warehouse (BW)** .

Raadpleegt het [technische document over Power BI en SAP BW](https://aka.ms/powerbiandsapbw) voor informatie over hoe SAP-klanten kunnen profiteren van de koppeling tussen Power BI en hun bestaande SAP Business Warehouse-systemen. Zie het artikel [DirectQuery en SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md) voor meer informatie over het gebruik van DirectQuery met SAP BW.

Vanaf de release van juni 2018 van **Power BI Desktop** (en algemeen beschikbaar vanaf de release van oktober 2018) kunt u de SAP BW-connector gebruiken. Er zijn belangrijke verbeteringen aangebracht in de prestaties en mogelijkheden. Deze bijgewerkte versie van de SAP BW-connector is ontwikkeld door Microsoft en heet **Implementation 2.0**. U kunt versie 1 (v1) van de **SAP BW-connector** of de **Implementation 2.0 SAP-connector** selecteren. In de volgende gedeelten wordt voor elke versie beschreven hoe de installatie in zijn werk gaat. U kunt een van beide connectors kiezen wanneer u vanuit Power BI Desktop verbinding maakt met SAP BW.

Het wordt aangeraden om waar mogelijk gebruik te maken van de **Implementation 2.0 SAP-connector**.

## <a name="installation-of-version-1-of-the-sap-bw-connector"></a>Installatie van versie 1 van de SAP BW-connector
Het wordt aangeraden om waar mogelijk gebruik te maken van de Implementation 2.0 SAP-connector (zie de instructies in het volgende gedeelte). In dit gedeelte wordt beschreven hoe u versie 1 van de **SAP BW-connector** installeert. Volg voor de installatie de volgende stappen:

1. Installeer de **SAP NetWeaver**-bibliotheek op uw lokale computer. U kunt de **SAP Netweaver**-bibliotheek bij uw SAP-beheerder verkrijgen of rechtstreeks uit het [SAP Software Download Center](https://support.sap.com/swdc) downloaden. Omdat de indeling van het **SAP Software Download Center** vaak verandert, kunnen we geen specifiekere richtlijnen geven voor de navigatie op die site. De **SAP NetWeaver** bibliotheek is meestal ook opgenomen in de hulpprogramma's voor installatie van de SAP-client.
   
   U kunt mogelijk zoeken naar *SAP Note #1025361* voor informatie over de downloadlocatie van de meest recente versie. Zorg ervoor dat de architectuur voor de **SAP NetWeaver**-bibliotheek (32-bits of 64-bits) overeenkomt met uw **Power BI Desktop**-installatie en installeer vervolgens alle bestanden die zijn opgenomen in de **SAP NetWeaver RFC-SDK**  in overeenstemming met de SAP Note.
2. Het dialoogvenster **Gegevens ophalen** bevat een vermelding voor **SAP Business Warehouse-toepassingsserver** en **SAP Business Warehouse-berichtenserver** in de categorie **Database**.
   
   ![Gegevensopties voor SAP ophalen](media/desktop-sap-bw-connector/sap_bw_2a.png)

## <a name="installation-of-implementation-20-sap-connector"></a>Installatie van de Implementation 2.0 SAP-connector

voor **Implementation 2.0** van de SAP-connector is de SAP .NET Connector 3.0 vereist. U kunt de [SAP .NET Connector 3.0 downloaden](https://support.sap.com/en/product/connectors/msnet.html) van de SAP-website. Gebruik daarvoor de volgende koppeling:

* [SAP .NET Connector 3.0](https://support.sap.com/en/product/connectors/msnet.html)

Er is een geldige S-gebruiker nodig om de download te kunnen uitvoeren. Klanten wordt aangeraden om contact op te nemen met het SAP Basis-team om de SAP .NET Connector 3.0 te verkrijgen. 

De connector is beschikbaar in 32-bits en 64-bits versies. Gebruikers *moeten* de versie kiezen die overeenkomt met hun Power BI Desktop-installatie. Op het moment dat dit wordt geschreven, staan op de website twee versies vermeld (voor .NET 4.0 Framework):

* De SAP-connector voor Microsoft .NET 3.0.20.0 voor Windows 32-bits (x86) als ZIP-bestand (6896 KB), 16 januari 2018
* De SAP-connector voor Microsoft .NET 3.0.20.0 voor Windows 64-bits (x64) als ZIP-bestand (7180 KB), 16 januari 2018

Tijdens de installatie selecteert u in het venster **Optionele installatiestappen** de optie *Assembly's installeren in GAC*, zoals wordt weergegeven in de volgende afbeelding.

![Optionele SAP-installatiestappen](media/desktop-sap-bw-connector/sap_bw_2b.png)

> [!NOTE]
> Voor de eerste versie van de SAP BW-implementatie waren Netweaver-DLL's vereist. Als u Implementation 2.0 van de SAP-connector gebruikt (en niet de eerste versie gebruikt), zijn de Netweaver-DLL's niet vereist.


## <a name="version-1-sap-bw-connector-features"></a>Functies van versie 1 van de SAP BW-connector
Met versie 1 van de **SAP BW-connector** in Power BI Desktop kunt u gegevens importeren uit uw **SAP Business Warehouse Server**-kubussen, of u kunt DirectQuery gebruiken. 

Lees voor meer informatie over de **SAP BW-connector** en hoe u deze kunt gebruiken met DirectQuery eens het artikel [DirectQuery en SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md).

U moet een *server*, *systeemnummer* en *client-id* opgeven om verbinding te maken.

![Verbindingsinstellingen voor de SAP-server](media/desktop-sap-bw-connector/sap_bw_3a.png)

U kunt ook twee extra **geavanceerde opties** opgeven: de taalcode en een aangepaste MDX-instructie om uit te voeren op de opgegeven server.

![aanvullende verbindingsgegevens](media/desktop-sap-bw-connector/sap_bw_4a.png)

Als er geen MDX-instructie is opgegeven, wordt het **Navigator**-venster weergegeven, waarin de lijst met kubussen die beschikbaar zijn op de server wordt weergegeven en dat de optie biedt om in te zoomen en items te selecteren in de beschikbare kubussen, inclusief dimensies en metingen. Power BI geeft de query's en kubussen weer die worden weergegeven door de [BW Open Analysis Interface OLAP-BAPI’s](https://help.sap.com/saphelp_nw70/helpdata/en/d9/ed8c3c59021315e10000000a114084/content.htm).

Wanneer u een of meer items van de server selecteert, wordt een voorbeeld van de uitvoertabel gemaakt op basis van deze selectie.

![SAP-tabelvoorbeeld](media/desktop-sap-bw-connector/sap_bw_5.png)

Het **Navigator**-venster biedt ook enkele **weergaveopties** waarmee u het volgende kunt doen:

* ***Alleen geselecteerde items* weergeven versus *Alle items* (standaardweergave):** deze optie is handig voor het controleren van de definitieve set geselecteerde items. Een alternatieve methode om deze weer te geven, is door de *kolomnamen* in het gebied *Preview* te selecteren.
* **Voorbeelden van gegevens inschakelen (standaardinstelling):** u kunt ook bepalen of voorbeelden van gegevens in dit dialoogvenster moeten worden weergegeven. Als u voorbeelden van gegevens uitschakelt, zijn er minder serveraanroepen, omdat er geen gegevens meer voor de voorbeelden worden aangevraagd.
* **Technische namen:** SAP BW ondersteunt het principe van *technische namen* voor objecten in een kubus. Met technische namen kan de eigenaar van een kubus *gebruikersvriendelijke* namen weergeven voor kubusobjecten, in plaats van alleen de *fysieke namen* voor die objecten in de kubus weer te geven.

![het Navigator-venster](media/desktop-sap-bw-connector/sap_bw_6.png)

Na het selecteren van alle benodigde objecten in de **Navigator**, kunt u bepalen wat u nu wilt gaan doen door een van de volgende knoppen aan de onderkant van het **Navigator**-venster te selecteren:

* Als u **Laden** selecteert, wordt de volledige set rijen voor de uitvoertabel in het gegevensmodel van Power BI Desktop geladen. Vervolgens gaat u naar de **rapportviewer**, waar u kunt beginnen met het visualiseren van de gegevens of verdere wijzigingen kunt aanbrengen met behulp van de **gegevens**- of **relatie**weergave.
* Als u **Bewerken** selecteert, wordt de **Query-editor** geopend, waar u extra stappen voor gegevenstransformatie en filteren van gegevens kunt uitvoeren voordat de volledige set van rijen in het gegevensmodel van Power BI Desktop wordt gebracht.

Naast het importeren van gegevens uit **SAP BW**-kubussen kunt u ook gegevens importeren uit een breed scala aan andere gegevensbronnen in Power BI Desktop. Vervolgens kunt u deze combineren tot één rapport. Dit geeft naast **SAP BW**-gegevens allerlei interessante scenario's voor rapportage en analyse.

## <a name="using-implementation-20-sap-bw-connector"></a>De Implementation 2.0 SAP BW-connector gebruiken

U moet een nieuwe verbinding maken voor het gebruik van Implementation 2.0 van de SAP BW-connector. Voer de volgende stappen uit om een nieuwe verbinding te maken.

1. In het venster **Gegevens ophalen** selecteert u **SAP Business Warehouse-toepassingsserver** of **SAP Business Warehouse-berichtenserver**.

2. Het dialoogvenster voor de nieuwe verbinding wordt weergegeven. Hier kunt u de implementatie selecteren. Als u **Implementation 2.0** selecteert, zoals weergegeven in de volgende afbeelding, worden de opties Uitvoeringsmodus, Batchgrootte en Kenmerkstructuren inschakelen beschikbaar.

    ![Dialoogvenster voor SAP-verbinding](media/desktop-sap-bw-connector/sap_bw_7.png)

3. Selecteer **OK**. De **Navigator**-ervaring is dan hetzelfde als in het vorige gedeelte is beschreven voor versie 1 van de SAP BW-connector. 

### <a name="new-options-for-implementation-20"></a>Nieuwe opties voor Implementation 2.0 

Implementation 2.0 biedt ondersteuning voor de volgende opties:

1. **ExecutionMode**: hiermee wordt aangegeven welke MDX-interface wordt gebruikt voor het uitvoeren van query's op de server. Dit zijn geldige opties:

        a. SapBusinessWarehouseExecutionMode.BasXml
        b. SapBusinessWarehouseExecutionMode.BasXmlGzip
        c. SapBusinessWarehouseExecutionMode.DataStream

    De standaardwaarde voor deze optie is SapBusinessWarehouseExecutionMode.BasXmlGzip.

    Met *SapBusinessWarehouseExecutionMode.BasXmlGzip* worden de prestaties mogelijk verbeterd als er sprake is van een hoge latentie bij grote gegevenssets.

2. **BatchSize**: hiermee wordt aangegeven hoeveel rijen er maximaal in één keer worden opgehaald bij het uitvoeren van een MDX-instructie. Een klein aantal rijen wordt omgezet in meerdere aanroepen naar de server bij het ophalen van een grote gegevensset. Met een groot aantal rijen zijn de prestaties mogelijk beter, maar dit kan op de SAP BW-server leiden tot geheugenproblemen. De standaardwaarde is 50.000 rijen.

3. **EnableStructures**: een logische waarde waarmee wordt aangegeven of kenmerkstructuren worden herkend. De standaardwaarde voor deze optie is false. Dit is van invloed op de lijst met objecten die kunnen worden geselecteerd. Niet ondersteund in de systeemeigen querymodus.

De optie **ScaleMeasures** is afgeschaft in deze implementatie. Het gedrag is nu hetzelfde als bij de instelling *ScaleMeasures = false*. Hierbij worden altijd ongeschaalde waarden weergegeven.

### <a name="additional-improvements-for-implementation-20"></a>Aanvullende verbeteringen voor Implementation 2.0 

In de volgende lijst met opsommingstekens worden enkele van de aanvullende verbeteringen beschreven die deel uitmaken van de nieuwe implementatie:

* Verbeterde prestaties
* De mogelijkheid om verschillende miljoenen rijen gegevens op te halen en af te stemmen via de batchgrootteparameter.
* De mogelijkheid om tussen uitvoeringsmodi te wisselen.
* Ondersteuning voor de gecomprimeerde modus. Dit is vooral nuttig voor verbindingen met een hoge latentie en grote gegevenssets.
* Verbeterde detectie van datumvariabelen
* [Experimental] Datum- (ABAP-type DATS) en tijddimensies (ABAP-type TIMS) weergeven als respectievelijk datums en tijden in plaats van tekstwaarden.
* Betere afhandeling van uitzonderingen. Fouten die optreden in BAPI-aanroepen worden nu zichtbaar.
* Kolommen inklappen in de modi BasXml en BasXmlGzip. Als met de gegenereerde MDX-query bijvoorbeeld 40 kolommen worden opgehaald, maar er voor de huidige selectie maar 10 nodig zijn, wordt de aanvraag doorgegeven aan de server om een kleinere gegevensset op te halen.


### <a name="changing-existing-reports-to-use-implementation-20"></a>Bestaande rapporten wijzigen voor het gebruik van Implementation 2.0 

Bestaande rapporten kunnen alleen worden gewijzigd voor het gebruik van **Implementation 2.0** als de importeermodus is ingeschakeld. De volgende stappen moeten handmatig worden uitgevoerd.

1. Open een bestaand rapport, selecteer **Query's bewerken** in het lint en selecteer vervolgens de SAP Business Warehouse-query die u wilt bijwerken.

2. Klik met de rechtermuisknop op de query en selecteer **Geavanceerde editor**.

3. In de **geavanceerde editor** wijzigt u de aanroep SapBusinessWarehouse.Cubes als volgt: 

    a. Bepaal of de query al een optierecord bevat, zoals wordt weergegeven in het volgende voorbeeld:

    ![querycodefragment](media/desktop-sap-bw-connector/sap_bw_9.png)

    b. Als dat het geval is, voegt u de optie Implementation 2.0 toe en verwijdert u de optie ScaleMeasures (indien aanwezig). U doet dit als volgt:

    ![querycodefragment](media/desktop-sap-bw-connector/sap_bw_10.png)

    c. Als de query nog geen optierecord bevat, voegt u er een toe. Als bijvoorbeeld het volgende aanwezig is:

    ![querycodefragment](media/desktop-sap-bw-connector/sap_bw_11.png)

    d. Verandert u dit in:

    ![querycodefragment](media/desktop-sap-bw-connector/sap_bw_12.png)

4. Er is alles aan gedaan om Implementation 2.0 van de SAP BW-connector compatibel te maken met versie 1 van de SAP BW-connector. Er kunnen echter verschillen zijn als er verschillende SAP BW MDX-uitvoeringsmodi worden gebruikt. U kunt eventuele verschillen verhelpen door een andere uitvoeringsmodus te selecteren.

## <a name="troubleshooting"></a>Problemen oplossen
Dit gedeelte bevat situaties waarin zich problemen voordoen (en oplossingen hiervoor) bij het werken met de **SAP BW**-connector.

1. Numerieke gegevens uit **SAP BW** retourneren decimale punten in plaats van komma's. Bijvoorbeeld: 1,000,000 wordt geretourneerd als 1.000.000.
   
   **SAP BW** retourneert decimale gegevens met een *,* (komma) of een *.* (punt) als decimaal scheidingsteken. Om op te geven welke van beide **SAP BW** moet gebruiken voor het decimale scheidingsteken, roept het stuurprogramma dat wordt gebruikt door **Power BI Desktop** *BAPI_USER_GET_DETAIL* aan. Deze aanroep retourneert een structuur genaamd **DEFAULTS**, die een veld heeft met de naam *DCPFM* waarin de *decimale notatie* is opgeslagen. Eén van de volgende drie waarden wordt gebruikt:
   
       ‘ ‘ (space) = Decimal point is comma: N.NNN,NN
       'X' = Decimal point is period: N,NNN.NN
       'Y' = Decimal point is N NNN NNN,NN
   
   Klanten die dit probleem hebben gerapporteerd, hebben ondervonden dat de aanroep naar *BAPI_USER_GET_DETAIL* mislukt voor een bepaalde gebruiker (de gebruiker die de onjuiste gegevens weergeeft), en er een foutbericht wordt weergegeven dat vergelijkbaar is met het volgende:
   
       You are not authorized to display users in group TI:
           <item>
               <TYPE>E</TYPE>
               <ID>01</ID>
               <NUMBER>512</NUMBER>
               <MESSAGE>You are not authorized to display users in group TI</MESSAGE>
               <LOG_NO/>
               <LOG_MSG_NO>000000</LOG_MSG_NO>
               <MESSAGE_V1>TI</MESSAGE_V1>
               <MESSAGE_V2/>
               <MESSAGE_V3/>
               <MESSAGE_V4/>
               <PARAMETER/>
               <ROW>0</ROW>
               <FIELD>BNAME</FIELD>
               <SYSTEM>CLNTPW1400</SYSTEM>
           </item>
   
   Om deze fout op te lossen, moeten gebruikers hun SAP-beheerder vragen om de SAPBW-gebruiker die wordt gebruikt in Power BI het recht te verlenen om *BAPI_USER_GET_DETAIL* uit te voeren. Het verdient ook aanbeveling om te controleren of de gebruiker de vereiste *DCPFM*-waarde heeft, zoals eerder in deze oplossing is beschreven.
   
2. **Connectiviteit voor SAP BEx-query's**
   
   U kunt **BEx**-query's uitvoeren in Power BI Desktop door een bepaalde eigenschap in te schakelen, zoals wordt weergegeven op de volgende afbeelding:
   
   ![](media/desktop-sap-bw-connector/sap_bw_8.png)
   
3. Het venster **Navigator** toont geen voorbeeld van gegevens, maar geeft een foutmelding dat de *objectverwijzing niet is ingesteld op een exemplaar van een object*.
   
   SAP-gebruikers moeten toegang hebben tot specifieke BAPI-functiemodules om metagegevens en gegevens op te halen van InfoProviders van SAP BW. Deze omvatten:
   * BAPI_MDPROVIDER_GET_CATALOGS
   * BAPI_MDPROVIDER_GET_CUBES
   * BAPI_MDPROVIDER_GET_DIMENSIONS
   * BAPI_MDPROVIDER_GET_HIERARCHYS
   * BAPI_MDPROVIDER_GET_LEVELS
   * BAPI_MDPROVIDER_GET_MEASURES
   * BAPI_MDPROVIDER_GET_MEMBERS
   * BAPI_MDPROVIDER_GET_VARIABLES
   * BAPI_IOBJ_GETDETAIL

   Om dit probleem op te lossen, moet u eerst verifiëren dat de gebruiker toegang heeft tot de verschillende *MDPROVIDER*-modules en tot *BAPI_IOBJ_GETDETAIL*. Voor verdere probleemoplossing voor dit probleem of vergelijkbare problemen, selecteert u *Tracering inschakelen* in het venster *Diagnostische gegevens* in de *Opties* van Power BI Desktop. Probeer gegevens van SAP BW op te halen terwijl de tracering actief is en bekijk het traceringsbestand voor meer informatie.

## <a name="sap-bw-connection-support"></a>Ondersteuning voor SAP BW-verbindingen

In de volgende tabel wordt de huidige ondersteuning voor SAP BW beschreven.



|Product  |Modus  |Verificatie  |Connector  |SNC-bibliotheek  |Ondersteund  |
|---------|---------|---------|---------|---------|---------|
|Power BI Desktop     |Elke         | Gebruiker / wachtwoord  | Toepassingsserver | N.v.t.  | Ja  |
|Power BI Desktop     |Elke         | Windows          | Toepassingsserver | sapcrypto + gsskrb5/gx64krb5  | Ja  |
|Power BI Desktop     |Elke         | Windows via imitatie | Toepassingsserver | sapcrypto + gsskrb5/gx64krb5  | Ja  |
|Power BI Desktop     |Elke         | Gebruiker / wachtwoord        | Berichtenserver | N.v.t.  | Ja  |
|Power BI Desktop     |Elke         | Windows        | Berichtenserver | sapcrypto + gsskrb5/gx64krb5  | Ja  |
|Power BI Desktop     |Elke         | Windows via imitatie | Berichtenserver | sapcrypto + gsskrb5/gx64krb5  | Ja  |
|Power BI Gateway     |Importeren      | Hetzelfde als Power BI Desktop |         |   |   |
|Power BI Gateway     |DirectQuery | Gebruiker / wachtwoord        | Toepassingsserver | N.v.t.  | Ja  |
|Power BI Gateway     |DirectQuery | Windows via imitatie (vaste gebruiker, geen eenmalige aanmelding) | Toepassingsserver | sapcrypto + gsskrb5/gx64krb5  | Ja  |
|Power BI Gateway     |DirectQuery | Eenmalige aanmelding via Kerberos gebruiken voor de optie DirectQuery-query’s | Toepassingsserver | *uitsluitend met* gsskrb5/gx64krb5   | Ja  |
|Power BI Gateway     |DirectQuery | Gebruiker / wachtwoord        | Berichtenserver | N.v.t.  | Ja  |
|Power BI Gateway     |DirectQuery | Windows via imitatie (vaste gebruiker, geen eenmalige aanmelding) | Berichtenserver | sapcrypto + gsskrb5/gx64krb5  | Ja  |
|Power BI Gateway     |DirectQuery | Eenmalige aanmelding via Kerberos gebruiken voor de optie DirectQuery-query’s | Berichtenserver | sapcrypto + gsskrb5/gx64krb5  | Nee  |



## <a name="next-steps"></a>Volgende stappen
Raadpleeg de volgende resources voor meer informatie over SAP en DirectQuery:

* [DirectQuery en SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery en SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Gegevensbronnen die worden ondersteund door DirectQuery](desktop-directquery-data-sources.md)
* [Technisch document over Power BI en SAP BW](https://aka.ms/powerbiandsapbw)
