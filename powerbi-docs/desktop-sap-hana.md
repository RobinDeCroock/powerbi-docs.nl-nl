---
title: SAP HANA in Power BI Desktop gebruiken
description: SAP HANA in Power BI Desktop gebruiken
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9b205a0ae9b58acf054a9afe43196e77ee404c84
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "76753099"
---
# <a name="connect-to-sap-hana-databases-in-power-bi-desktop"></a>Verbinding maken met SAP HANA-databases in Power BI Desktop

Met Power BI Desktop hebt u nu toegang tot *SAP HANA*-databases. Om SAP HANA te gebruiken moet u het SAP HANA ODBC-stuurprogramma hebben geïnstalleerd op de lokale clientcomputer. Anders werkt de gegevensverbinding tussen Power BI Desktop en SAP HANA niet goed. U kunt de SAP HANA-clienthulpprogramma's downloaden via [SAP-hulpprogramma's voor ontwikkelaars](https://tools.hana.ondemand.com/#hanatools), waar het benodigde ODBC-stuurprogramma te vinden is. U kunt dit ook ophalen via het [SAP Software Download Center](https://support.sap.com/en/my-support/software-downloads.html). Zoek in de Software-portal naar de *SAP HANA CLIENT* voor Windows-computers. Omdat de indeling van het SAP Software Download Center vaak verandert, is er geen specifiekere richtlijnen beschikbaar voor de navigatie op die site.

Als u verbinding wilt maken met een SAP HANA-database, selecteert u **Gegevens ophalen**, kiest u **Database** > **SAP HANA-database** en selecteert u vervolgens **Verbinding maken**:

![SAP HANA-database, dialoogvenster Gegevens ophalen, Power BI Desktop](media/desktop-sap-hana/sap-hana-1.png)

Wanneer u verbinding maakt met een SAP HANA-database, moet u de servernaam opgeven. Kies vervolgens de poort in de vervolgkeuzelijst en het invoervak.

In deze versie wordt SAP HANA in de [DirectQuery](desktop-directquery-sap-hana.md)-modus ondersteund in Power BI Desktop en de Power BI-service. U kunt rapporten die gebruikmaken van SAP HANA in de DirectQuery-modus publiceren en uploaden naar de Power BI-service. U kunt ook rapporten publiceren en uploaden naar de Power BI-service wanneer u SAP HANA niet in de DirectQuery-modus gebruikt.

## <a name="supported-features-for-sap-hana"></a>Ondersteunde functies voor SAP HANA

Deze release heeft veel mogelijkheden voor SAP HANA, zoals wordt weergegeven in de volgende lijst:

* De Power BI-connector voor SAP HANA maakt gebruik van het SAP ODBC-stuurprogramma om de beste gebruikerservaring te bieden.

* SAP HANA ondersteunt opties voor importeren en voor DirectQuery.

* Power BI ondersteunt HANA-informatiemodellen, zoals de weergaven Analyse en Berekening, en heeft geoptimaliseerde navigatie.

* Met SAP HANA kunt u ook de directe SQL-functie gebruiken om verbinding te maken met rij- en kolomtabellen.

* Power BI bevat geoptimaliseerde navigatie voor HANA-modellen.

* Power BI ondersteunt SAP HANA-variabelen en -invoerparameters.

* Power BI ondersteunt berekeningsweergaven op basis van een HDI-container.

  * Ondersteuning voor berekeningsweergaven op basis van een HDI-container is beschikbaar als openbare preview in de Power BI Desktop-versie van augustus 2019. Als u in Power BI toegang tot uw berekeningsweergaven op basis van HDI-containers wilt krijgen, moeten uw gebruikers van de HANA-database in Power BI toegang hebben tot de HDI-uitvoeringscontainer waarin de weergaven zijn opgeslagen die u wilt gebruiken. Als u deze toegang wilt verlenen, maakt u een rol waarmee toegang tot uw HDI-container wordt verleend. Wijs de rol vervolgens toe aan de HANA-databasegebruiker die u wilt gebruiken met Power BI. (Deze gebruiker moet ook zijn gemachtigd om de systeemtabellen in het \_SYS\_BI-schema te lezen, zoals gebruikelijk.) Raadpleeg de officiële SAP-documentatie voor uitgebreide instructies over het maken en toewijzen van databaserollen. [Deze SAP-blog](https://blogs.sap.com/2018/01/24/the-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user/) is mogelijk een goede plaats om te beginnen.

  * Er gelden momenteel enkele beperkingen voor HANA-variabelen die zijn gekoppeld aan berekeningsweergaven op basis van HDI. Deze beperkingen zijn ingesteld in verband met fouten bij HANA.
  
    Ten eerste is het niet mogelijk om een HANA-variabele toe te passen op een gedeelde kolom van een berekeningsweergave op basis van een HDI-container. Deze beperking kan worden verholpen door een upgrade uit te voeren naar HANA 2, versie 37.02 en hoger of naar HANA 2, versie 42 en hoger. Ten tweede worden de standaardwaarden met meerdere invoeren voor variabelen en parameters momenteel niet weergegeven in de gebruikersinterface van Power BI. Deze beperking wordt veroorzaakt door een fout in SAP HANA, maar er is nog geen oplossing aangekondigd door SAP.

## <a name="limitations-of-sap-hana"></a>Beperkingen van SAP HANA

Er zijn ook enkele beperkingen voor het gebruik van SAP HANA. Deze worden hieronder weergegeven:

* NVARCHAR-tekenreeksen worden afgekapt tot een maximale lengte van 4000 Unicode-tekens.
* SMALLDECIMAL wordt niet ondersteund.
* VARBINARY wordt niet ondersteund.
* Geldige datums liggen tussen 30-12-1899 en 31-12-9999.

## <a name="next-steps"></a>Volgende stappen

Raadpleeg de volgende resources voor meer informatie over DirectQuery en SAP HANA:

* [DirectQuery en SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery in Power BI gebruiken](desktop-directquery-about.md)
* [Power BI-gegevensbronnen](power-bi-data-sources.md)
* [Versleuteling inschakelen voor SAP HANA](desktop-sap-hana-encryption.md)
