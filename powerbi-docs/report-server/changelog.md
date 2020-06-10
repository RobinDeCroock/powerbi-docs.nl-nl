---
title: Wijzigingenlogboek voor Power BI Report Server
description: Dit is een wijzigingenlogboek voor Power BI Report Server met een overzicht van nieuwe items en oplossingen voor problemen voor elke uitgebrachte build.
ms.author: jaimeta
author: jtarquino
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/31/2020
ms.openlocfilehash: 0391f0f2e4340b01c1f1ad7a3bce860487daabc9
ms.sourcegitcommit: 49daa8964c6e30347e29e7bfc015762e2cf494b3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84272650"
---
# <a name="change-log-for-power-bi-report-server"></a>Wijzigingenlogboek voor Power BI Report Server

Dit is een wijzigingenlogboek voor Power BI Report Server met een overzicht van nieuwe items en oplossingen voor problemen voor elke uitgebrachte build.

Zie [Wat is er nieuw in Power BI Report Server](whats-new.md) voor gedetailleerde informatie over nieuwe functies. 


## <a name="may-2020"></a>Mei 2020
- **Power BI Report Server**
    - *Versie: 1.8.7450.37410 (Build 15.0.1103.227), uitgebracht: 27 mei 2020*
         - Functies
            -  Ondersteuning toegevoegd voor de grootte van de verbindingsgroep van de catalogus (zie[MaxCatalogConnectionPoolSizePerProcess-instelling](https://docs.microsoft.com/sql/reporting-services/report-server/rsreportserver-config-configuration-file?view=sql-server-ver15#bkmk_service) voor meer informatie).
            -  Verbeterd gedrag bij het bekijken van een rapport tijdens een vernieuwingsbewerking.
        - Beveiligingsupdates
        - Opgeloste fouten
            - Twee problemen opgelost met betrekking tot enkele aanhalingstekens in map- en rapportnamen.
            - Er is een probleem opgelost met betrekking tot de horizontale scroll met bepaalde browsers en de functie records weergeven.
            - Er is een probleem opgelost waarbij de geplande vernieuwing tijdens het openen van het rapport soms kan leiden tot schemafouten in het onderliggende model.
            - Er is een probleem opgelost waarbij alt-tekst voor PDF-export niet correct was gecodeerd voor multi-bytetekens.
            - Een probleem opgelost waarbij aangepaste toepassingen die LoadReport uitvoeren, ten onrechte een TrustedHeader-fout zouden ontvangen.
            - Er is een probleem opgelost waarbij zware belasting door geplande vernieuwing kan leiden tot mislukte vernieuwingen.
            - Er is een probleem opgelost waarbij rapporten op de verkeerde locatie werden opgeslagen als de rapportnaam overeenkwam met de mapnaam.
            - Problemen met tabbladen in de documentmap opgelost.
            - Er is een probleem met gegevensgestuurde abonnementen opgelost bij het gebruik van DAX-query's.
            - Er is een probleem opgelost in de URL-toegang waardoor FindString geen overeenkomsten kon vinden.
            - Er is een probleem opgelost waarbij ingesloten gegevensbronnen kapot gingen bij het verplaatsen van rapporten.
            - Er is een probleem opgelost waarbij de geplande vernieuwing voor bepaalde gegevensbronnen mislukt.
            - Validatie toegevoegd aan rapportplanning om de kans op ongeldige verzoeken te verminderen.


- **Power BI Report (geoptimaliseerd voor Power BI Report Server)**
    - *Versie: 2.81.5831.941 (mei 2020), uitgebracht: 27 mei 2020* (nieuwe build en nieuwe versie)
        - Bevat de vereiste wijzigingen om verbinding te maken met Power BI Report Server (mei 2020)        



## <a name="january-2020"></a>Januari 2020
- **Power BI Report Server**
    - *Versie: 1.6.7364.4075 (Build 15.0.1102.777), uitgebracht: 2 maart 2020*
         - Opgeloste fouten
           -  Oplossing voor Power BI-rapporten die niet kunnen worden geüpload voor bepaalde gegevensbronnen
           -  Oplossing voor de downloadlocatie voor de Power BI Report Server Desktop-koppeling in de portal
           -  Oplossing voor de weergave van DynamicImageDPI voor Excel
           -  Oplossing voor het gebruik van een onjuiste threadcultuur voor Oracle-verbindingen in bepaalde scenario’s met meerdere gebruikers (zie [UseInstalledUICulture-documentatie](https://docs.microsoft.com/power-bi/report-server/connect-data-sources) voor meer informatie)
           -  Oplossing voor fouten bij het insluiten van rapporten, die worden veroorzaakt door de CustomHeaders-standaardwaarde
           -  Oplossing voor het onjuist genereren van SQL-parameternamen in bepaalde gevallen
    - *Versie: 1.6.7327.3007 (Build 15.0.1102.759), uitgebracht: 23 januari 2020*
         - Functies
            -  Exporteren naar Excel vanuit Power BI-rapporten.
           -  Ondersteuning voor Power BI Premium-gegevenssets voor gepagineerde rapporten.
           -  Ondersteuning voor AltText (alternatieve tekst) voor elementen van een gepagineerd rapport.
           -  Ondersteuning voor aangepaste headers.
           -  Ondersteuning voor Azure SQL Managed Instances als de catalogus.
           -  Transparent Database Encryption voor de catalogus.
        - Beveiligingsupdates
        - Opgeloste fouten
            - Oplossingen voor toegankelijkheid voor schermlezers, het weergeven van rapporten en toetsenbordnavigatie.
            - Oplossing voor het opslaan van multi-byte rapporttitels.
            - Oplossing voor uitgebreide logboekregistratie die van invloed is op de betrouwbaarheid van de rapportserver.
          - Oplossing voor het garanderen van live-gegevens in Power BI-rapporten op mobiele apparaten.
          - Oplossing voor het toepassen van markeringen tussen visuals in een gefilterde export van Power BI-rapporten.
          - Oplossing voor het schrijven van voettekst bij het exporteren naar Word met expressie voor zichtbaarheid van gepagineerde rapporten. 
     
- **Power BI Report (geoptimaliseerd voor Power BI Report Server)**
    - *Versie: 2.76.5678.1521 (januari 2020), uitgebracht: 23 januari 2020* (nieuwe build en nieuwe versie)
        - Bevat wijzigingen vereist om verbinding te maken met Power BI Report Server (januari 2020)        


## <a name="september-2019"></a>September 2019
- **Power BI Report Server**
    - *Versie: 1.6.7236.4246 (build 15.0.1102.646), uitgebracht: 25 oktober 2019*
        - Beveiligingsupdates
        - Opgeloste fouten
            - De oplossing voor .NET Framework 4.7 is niet geïnstalleerd.
            - Oplossing voor gepagineerde rapporten voor Teradata met parameters met meerdere waarden met fout 110083.
            - Oplossing voor de URLRoot-waarde werkt niet als er meerdere URL-bindingen voor de webservice zijn en een van deze https://+80/reportserver is.
          - Oplossing voor parameterwaarden met meerdere waarden voor gepagineerde rapporten die buiten het rapportgebied worden vermeld.
          
    - *Versie: 1.6.7221.30698 (Build 15.0.1102.620), uitgebracht: 9 oktober 2019*
        - Opgeloste fouten
            - Oplossing voor aangepast visueel element voor tekstfilter.
            - Oplossing voor de prestaties van slicers voor vervolgkeuzelijsten.
            - Oplossing voor Strip PII op basis van telemetrie.
          - Oplossing voor URL's die niet hoofdlettergevoelig zijn.
          
    - *Versie 1.6.7206.38019 (build 15.0.1102.597), uitgebracht: 26 september 2019*
        - Beveiligingsupdates
        - Opgeloste fouten
           - Gepagineerde rapporten
             - Oplossing voor toegankelijkheidsproblemen die optreden bij het gebruik van Internet Explorer en Microsoft Edge.
             - Oplossing voor problemen met SAP HANA bij het testen van de verbinding.
             - Oplossing voor problemen die optreden bij het opgeven van een lijst met e-mailadressen.
             - Oplossing voor Power BI-rapporten die gebruikmaken van een DirectQuery-gegevensbron en geïntegreerde verificatie.
             - Oplossing voor gepagineerde rapporten die worden weergegeven met filterparameters wanneer de momentopname is ingeschakeld.
             - Oplossing voor dubbele uitvoering van opgeslagen procedures tijdens het uitvoeren van rapporten.
             - Oplossing voor de situatie waarin aan het standaardserviceaccount SQL Server- aanmeldingsmachtigingen worden toegekend wanneer volgens de configuratie de Power BI Report Server moet worden uitgevoerd met het aangepaste serviceaccount.
             - Oplossing voor de toegang tot modellen tijdens het vernieuwen in de Japanse tijdzone.
             - Oplossing voor verouderde modellen wanneer een nieuwe versie van het rapport wordt geüpload tijdens het vernieuwen.
             - Oplossing voor parameterwaarden die het teken '&' bevatten.
         - Programmeerbaarheid
             - Bijgewerkte web-API: /PowerBIReports({Id})/DataSources (PATCH) zodat verbindingsreeksupdates worden toegestaan.
         
- **Power BI Report (geoptimaliseerd voor Power BI Report Server)**
    - *Versie: 2.73.5586.1501 (september 2019), uitgebracht: 25 oktober 2019*
        - Opgeloste fouten
            - Oplossing voor telemetrie.
            
    - *Versie: 2.73.5586.1241 (september 2019), uitgebracht: 9 oktober 2019*
        - Opgeloste fouten
            - Oplossing voor aangepast visueel element voor tekstfilter.
            - Oplossing voor de prestaties van slicers voor vervolgkeuzelijsten.
            - Oplossing voor Strip PII op basis van telemetrie.
            
    - *Versie: 2.73.5586.821 (september 2019), uitgebracht: 26 september 2019* (nieuwe build en nieuwe versie)
        - Bevat de vereiste wijzigingen om verbinding te maken met Power BI Report Server (september 2019)

    
## <a name="may-2019"></a>Mei 2019

- **Power BI Report Server**          
    - *Versie 1.5.7074.36177 (build 15.0.1102.371), uitgebracht: 21 mei 2019*
        - Opgeloste fouten
            - Gepagineerde rapporten
                - Oplossing voor het altijd inschakelen van lettertype-insluiting voor PDF-bestanden.
                - Oplossing voor het instellen van cookies die als beveiligd via HTTPS worden verzonden
                - Oplossing voor problemen met pop-ups vanwege scriptfouten
                - Oplossing voor weergaveproblemen met mobiele app op Android-telefoons
                - Oplossing voor tijdnavigator in een mobiel rapport om de juiste weeknummers weer te geven, ongeacht het begin van het fiscale jaar
                - Configureerbare eigenschap RestrictedResourceMimeTypeForUpload toegevoegd voor beheerders om uitgesloten MIME-typen op te geven
         - Functies
            - Ondersteuning voor vertrouwde visuals toevoegen aan PBIRS

- **Power BI Report (geoptimaliseerd voor Power BI Report Server)**
    - *Versie: 2.69.5467.1801 (mei 2019), uitgebracht: 21 mei 2019*
        - Opgeloste fouten
            - Oplossing om het opnieuw invoeren van referenties tijdens het uploaden van PBIX naar PBIRS te voorkomen
            - Oplossing voor het openen van documenten met # in de bestandsnaam
            - Eenvoudiger koppeling toegevoegd om terug te gaan in het venster PBIRS-selectie
            - Oplossing voor modus Hoog contrast in PBIRS om knop Vorige weer te geven waarmee waarschuwingsberichten over visuals worden weergegeven.
            - Oplossingen voor gebruikersinterface in selectievenster, canvas schalen.

    - *Versie: 2.69.5467.5201 (mei 2019), uitgebracht: 30 juli 2019*
        - Opgeloste fouten
            - Oplossing voor onjuiste logboekregistratie van telemetriegegevens

## <a name="january-2019"></a>Januari 2019

- **Power BI Report Server**          
    - *Versie 1.4.7024.16477 (build 15.0.1102.299), uitgebracht: 28 maart 2019*
        - Opgeloste fouten
            - Power BI-rapporten
                - Oplossing voor een probleem met de basisreferenties bij het gebruik van DirectQuery voor SAP HANA en SAP BW
                - Oplossing voor problemen met het vernieuwen van gegevens van OData-feed met het bericht Kan bestand of assembly Microsoft.OData.Core.NetFX35.V7 niet laden

- **Power BI Report Server**            
    - *Versie 1.4.6969.7395 (build 15.0.1102.235), uitgebracht: 30 januari 2019*
        - Opgeloste fouten
            - Power BI-rapporten
                - Oplossing voor een probleem met de basisreferenties bij het gebruik van DirectQuery
                - Oplossing voor toegepaste filters bij bidirectionele relaties met beveiliging op rijniveau
                - Oplossing voor verlopen gegevens na het vernieuwen van een model in een uitgeschaalde omgeving
                - Oplossing voor dubbele scrollbalk voor tabel/matrix in Firefox 63+
                - Oplossing voor pictogramgrootte +/- in Internet Explorer
            - Gepagineerde rapporten
                - Oplossing voor probleem bij het gebruik van een gedeelde gegevensbron voor een rapport

    - *Versie 1.4.6960.38798 (build 15.0.1102.222), uitgebracht: 22 januari, 2019*
        - Functies
            - Power BI-rapporten 
                - Ondersteuning voor beveiliging op rijniveau
                - Uitvouwen of samenvouwen op rijkoppen van matrix
                - Kopiëren en plakken tussen .pbix-bestanden
                - Slimme uitlijningshulplijnen
                - Ondersteuning voor SAP BW 2.0-connector
            - Beheerders
                - Mogelijkheid om extensies van resources te beperken die kunnen worden geüpload naar de rapportserver
                - Mogelijkheid om ondersteunde hyperlinkschema's te beperken
            - Programmeerbaarheid
                - Nieuwe Web-API: /PowerBIReports({Id})/DataModelRoles (GET)
                - Nieuwe Web-API: /PowerBIReports({Id})/DataModelRoleAssignments (GET & PUT)
                - Zie [REST-API voor Power BI Report Server](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0) voor meer informatie
        - Opgeloste fouten
            - Beveiligingsprobleem met HTML-injectie
            - Exporteren naar PDF geeft geen euroteken weer
            - Door het opslaan van een wachtwoord met meerdere gegevensbronnen in Power BI-rapporten worden niet-gewijzigde wachtwoorden ongeldig
            - Visuele elementen geven problemen weer in Mobiele Power BI-app na inactiviteit

- **Power BI Report (geoptimaliseerd voor Power BI Report Server)**
    - *Versie: 2.65.5313.1562 (januari 2019), uitgebracht: 30 januari 2019*
        - Snelkoppeling en vastgemaakte pictogrammen blijven bestaan na het verwijderen van Power BI Report Server
        - Oplossing voor probleem waarbij het vastmaken van Power BI Report Server aan het startmenu leidt tot zwarte tekst op een zwart pictogram

    - *Versie: 2.65.5313.1421 (januari 2019), uitgebracht: 22 januari 2019* (nieuwe build en nieuwe versie)
        - Bevat de vereiste wijzigingen om verbinding te maken met Power BI Report Server (januari 2019) 
    - *Versie: 2.65.5313.5141 (januari 2019), uitgebracht: 31 juli 2019* (nieuwe build en nieuwe versie)
        - Opgeloste fouten
            - Oplossing voor onjuiste logboekregistratie van telemetriegegevens

## <a name="august-2018"></a>Augustus 2018

- **Power BI Report Server**
    - *Versie 1.3.6816.37243 (build 15.0.2.557), uitgebracht: 30 augustus 2018*
        - Opgeloste fouten
            - Er is een probleem opgelost waarbij na het upgraden van een eerdere versie van PBI-rapportserver waarbij een bindingsomleiding niet werd bijgewerkt, klanten het volgende zagen:      
            *`
            Failed to load expression host assembly. Details: Could not load file or assembly 'Microsoft.ReportingServices.ProcessingObjectModel, Version=2018.7.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040) (rsErrorLoadingExprHostAssembly)
             `*
             
            - Fout voor transparantie van gegevenslabel is nu opgelost.
            
    - *Versie 1.3.6801.38816 (build 15.0.2.540), uitgebracht: 15 augustus 2018*
        - Functies
            - SAP HANA SSO DirectQuery-ondersteuning met Kerberos is nu beschikbaar voor Power BI-rapporten
            - Aangepaste API voor visuals beschikbaar bij de release - versie 1.13.0
            - Er wordt een oudere versie van de functie voor Power BI-visuals geïntroduceerd die compatibel is met de huidige versie van de server-API (indien beschikbaar)

- **Power BI Report (geoptimaliseerd voor Power BI Report Server)**
    - *Versie: 2.61.5192.641 (augustus 2018), uitgebracht: 15 augustus 2018*
        - Bevat de vereiste wijzigingen om verbinding te maken met Power BI Report Server (augustus 2018)         
    - *Versie: 2.61.5192.7701 (augustus 2018), uitgebracht: 8 augustus 2019* (nieuwe build en nieuwe versie)
        - Opgeloste fouten
            - Oplossing voor onjuiste logboekregistratie van telemetriegegevens
            
## <a name="march-2018"></a>Maart 2018

- **Power BI Report Server**
    - *Versie 1.2.6690.34729 (build 15.0.2.402), uitgebracht: 27 april 2018*
        - Opgeloste fouten
            - Migratie van SQL Server Reporting Services 2017-catalogussen inschakelen
            - Voor Power BI-rapporten (PBIX)
                - Rapporten kunnen worden vernieuwd wanneer een server is geconfigureerd om aangepaste verificatie te gebruiken
                - De gegevensbronreferenties worden niet opnieuw ingesteld door de eigenschappen van een rapport te wijzigen
            - Voor Gepagineerde rapporten (RDL)
                - Het gebruik van `Lookup()` of afgeleide functies zoals `LookupSet()` en `MultiLookup()` in RDL-expressies heeft niet meer dit resultaat: `#Error`
                - Gekoppelde rapporten worden tijdens het afdrukken aangepast aan de paginagrootte van het doelrapport
                - Abonnementen kunnen worden gemaakt voor gekoppelde rapporten die gebruikmaken van trapsgewijze parameters
                - Standaardparameters voor meerdere waarden kunnen worden gewijzigd wanneer u IE11 gebruikt
                - Gegevensgestuurde bezorgingsopties voor abonnementen kunnen worden bewerkt
                - Abonnementen kunnen worden bekeken en bewerkt terwijl het abonnement wordt uitgevoerd
                - Verbindingsreeksen op basis van expressies worden niet verwijderd door de gegevensbronreferenties in te stellen
            - Voor KPI's
                - Trendregels worden vernieuwd wanneer de gegevens worden bijgewerkt
            - Algemene verbeteringen in de stabiliteit

    - *Versie 1.2.6660.39920 (build 15.0.2.389), uitgebracht: 28 maart 2018*
        - Opgeloste fouten
            - Voor Power BI-rapporten (PBIX) werkt de oplossing voor het exporteren van gegevens niet vanuit Power BI Visuals
            - Voor Power BI-rapporten (PBIX) werkt de oplossing voor het herstellen van URL-filters niet
            - Voor gepagineerde rapporten (RDL), wordt de oplossing voor het weergeven van installatiekopieën niet juist weergegeven in IE11 na de upgrade naar de maart-release van Power BI Report Server

    - *Versie 1.2.6648.38132 (build 15.0.2.378), uitgebracht: 19 maart 2018*
        - Beveiligingsupdates
        - Verbeterde toegankelijkheid
        - Opgeloste fouten
            - Er is voor gepagineerde rapporten (RDL) een fout opgelost, waarbij de zichtbaarheid van de parameters in een gekoppeld rapport werd teruggedraaid nadat de eigenschappen ervan waren bewerkt
            - Voor de webportal is een fout opgelost voor de verificatie van aangepaste formulieren, waarbij de cookie voor een verschuivende verloopdatum werd genegeerd
            - Er is een fout opgelost voor het exporteren naar Word, waarbij een ongelijke rijhoogte werd gemaakt als de inhoud van de rij leeg was
            - Er is voor gepagineerde rapporten (RDL) een fout opgelost, waarbij een verbindingsreeks die is gebaseerd op een expressie werd verwijderd wanneer de referenties voor de gegevensbron werden gewijzigd
            - Er is een fout opgelost zodat KPI kan worden gebruikt met tekstwaarden
            - Er is voor gepagineerde rapporten (RDL) een fout opgelost, zodat een nieuwe gegevensset kan worden toegewezen aan een bestaand gepagineerd rapport (RDL)
            - Andere foutoplossingen met betrekking tot de stabiliteit en het gebruik

- **Power BI Report (geoptimaliseerd voor Power BI Report Server)**
    - Versie: 2.56.5023.1043 (maart 2018), uitgebracht: 19 maart 2018
        - Bevat de vereiste wijzigingen om verbinding te maken met Power BI Report Server (maart 2018)

## <a name="october-2017"></a>Oktober 2017

- **Power BI Report Server**
    - *Versie 1.1.6582.41691 (build 14.0.600.442), uitgebracht: 10 januari 2018*
        - Beveiligingsupdates
        - Opgeloste fouten
            - Oplossing voor Model.GetParameters met 400 geretourneerd
            - Oplossing voor het instellen van gedeelde gegevensset voor bestaande gepagineerde rapporten (RDL)
            - Oplossing voor ExecutionNotFoundException wanneer het rapport met andere parameterwaarden naar PDF wordt geëxporteerd

    - *Versie 1.1.6551.5155 (build 14.0.600.438), uitgebracht: 11 december 2017*
        - Opgeloste fouten
            - Fout bij opslaan van gegevens na het vernieuwen van bepaalde Power BI Desktop-rapporten.

    - *Versie 1.1.6530.30789 (build 14.0.600.437), uitgebracht: 17 november 2017*
        - Opgeloste fouten
            - Oplossing voor basisverificatiescenario's. 
            - Oplossing voor het probleem met niet-selecteerbare weekdagen op de planningspagina voor abonnementen, in cachevernieuwingsplannen en voor momentopnamen van rapportgeschiedenis op de portal.
            - Oplossing voor het probleem met gepagineerde rapporten (RDL) waarbij expressies in het tekstvak waarvoor de CanGrow-eigenschap is ingesteld op false (onwaar), resulteren in waarden zonder kleur en lettertypen die niet goed worden weergegeven.
            - Oplossing voor het probleem met Power BI rapporten (PBIX) waarbij het toevoegen van legenda's aan een lijndiagram resulteert in een lege visual.

    - *Versie 1.1.6514.9163 (build 14.0.600.434), uitgebracht: 1 november 2017*
        - Opgeloste fouten
            - Oplossing voor problemen met de uploadbetrouwbaarheid van PBIX-rapporten van meer dan 500 MB.
            - Oplossing voor het probleem met het laden van PBIX-rapporten van meer dan 1 GB

    - *Versie 1.1.6513.3500 (build 14.0.600.433), uitgebracht: 31 oktober 2017*
        - Functies
            - Ondersteuning voor ingesloten gegevensmodellen
            - Weergeven van Excel-werkmappen (met Office Online Server-integratie ingeschakeld)
            - Geplande gegevensvernieuwing
            - Ondersteuning van DirectQuery
            - Ondersteuning voor grote bestanden (tot 2 GB)
            - Openbare REST API
            - Ondersteuning voor gedeelde gegevenssets in Power BI Desktop (oData)
            - Ondersteuning voor URL-parameters voor PBIX-bestanden
            - Verbeterde toegankelijkheid

- **Power BI Report (geoptimaliseerd voor Power BI Report Server)**
    - *Versie: 2.51.4885.3981 (oktober 2017), uitgebracht: 10 april 2018*
        - Beveiligingsupdates

    - *Versie: 2.51.4885.2501 (oktober 2017), uitgebracht: 10 januari 2018*
        - Beveiligingsupdates

    - *Versie: 2.51.4885.1423 (oktober 2017), uitgebracht: 17 november 2017*
        - Opgeloste fouten
            - Oplossing voor het probleem dat de 32-bits versie van Power BI Desktop niet kan worden uitgevoerd op x86-besturingssystemen.
            - Oplossing voor het probleem met de weergave van x-asrasterlijnen in Power BI Reports (PBIX).
            - Overige kleine correcties

    - *Versie: 2.51.4885.1041 (oktober 2017), uitgebracht: 31 oktober 2017*
        - Functies
            - Bevat de vereiste wijzigingen om verbinding te maken met Power BI Report Server (oktober 2017)

## <a name="june-2017"></a>Juni 2017

- **Power BI Report Server**
    - *Build 14.0.600.309, uitgebracht: 10 januari 2018*
        - Beveiligingsupdates

    - *Build 14.0.600.305, uitgebracht: 19 september 2017*  
        - Opgeloste fouten
            - Update naar de nieuwste [webbesturingselement voor Bing Kaarten](https://msdn.microsoft.com/library/mt712542.aspx)

    - *Build 14.0.600.301, uitgebracht: 11 juli 2017*
        - Opgeloste fouten
            - De tag `{{UserId}}` wordt omgezet in de opgeslagen referenties in plaats van dat de gebruiker het rapport uitvoert in Power BI-rapporten
            - Sommige afbeeldingen worden niet weergegeven in Power BI Report Server-rapporten.
            - De naam van een Power BI-rapport in Power BI Report Server kan niet worden gewijzigd.
            - Kan geen Power BI-visuals in de mobiele Power BI-app laden (de mobiele app moet opnieuw worden geïnstalleerd om de lokale cache te wissen)

    - *Build 14.0.600.271, uitgebracht: 12 juni 2017*
        - Eerste release van Power BI Report Server

- **Power BI Report (geoptimaliseerd voor Power BI Report Server)**
    - *Versie: 2.47.4766.4901 (juni 2017), uitgebracht: 10 januari 2018*
        - Beveiligingsupdates

## <a name="next-steps"></a>Volgende stappen

[Wat is Power BI Report Server?](get-started.md)
[Administratoroverzicht](admin-handbook-overview.md)  
[Power BI Report Server installeren](install-report-server.md)  
[Report Builder downloaden](https://www.microsoft.com/download/details.aspx?id=53613)  
[SQL Server Data Tools (SSDT) downloaden](https://go.microsoft.com/fwlink/?LinkID=616714)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
