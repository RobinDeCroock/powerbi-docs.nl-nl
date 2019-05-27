---
title: SAP HANA in Power BI Desktop gebruiken
description: SAP HANA in Power BI Desktop gebruiken
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7b3a59ae8926ce5e302cfcdecec617d1f3fd107b
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65513885"
---
# <a name="use-sap-hana-in-power-bi-desktop"></a>SAP HANA in Power BI Desktop gebruiken
Met Power BI Desktop hebt u nu toegang tot **SAP HANA**-databases. Om **SAP HANA** te gebruiken moet u het SAP HANA ODBC-stuurprogramma installeren op de lokale clientcomputer. Anders werkt de gegevensverbinding tussen Power BI Desktop en **SAP HANA** niet goed. U kunt het SAP HANA ODBC-stuurprogramma downloaden via het [SAP Software Download Center](https://support.sap.com/swdc). Zoek daar de SAP HANA CLIENT voor Windows-computers. Omdat de indeling van het **SAP Software Download Center** vaak verandert, kunnen we geen specifiekere richtlijnen geven voor de navigatie op die site.

Om verbinding te maken met een **SAP HANA**-database, selecteert u **Gegevens ophalen > Database > SAP HANA-database**, zoals weergegeven op de volgende afbeelding:

![](media/desktop-sap-hana/sap-hana-1.png)

Bij het verbinden met een SAP HANA-database moet u de naam van de server en de poort opgeven in de indeling *server: poort*. De volgende afbeelding toont een voorbeeld met een server met de naam *ServerXYZ* en poort *30015*.

![](media/desktop-sap-hana/sap-hana-2.png)

In deze release wordt **SAP HANA** in de [DirectQuery](desktop-directquery-sap-hana.md)-modus ondersteund in Power BI Desktop en de Power BI-service. U kunt rapporten die gebruikmaken van **SAP HANA** in de DirectQuery-modus publiceren en uploaden met de Power BI-service. U kunt ook rapporten publiceren en uploaden naar de Power BI-service wanneer u **SAP HANA** niet in de DirectQuery-modus gebruikt.

## <a name="supported-features-for-sap-hana"></a>Ondersteunde functies voor SAP HANA
Deze release heeft veel mogelijkheden voor **SAP HANA**, zoals wordt weergegeven in de volgende lijst:

* De Power BI-connector voor **SAP HANA** maakt gebruik van het SAP ODBC-stuurprogramma om de beste gebruikerservaring te bieden
* **SAP HANA** ondersteunt opties voor importeren en voor DirectQuery
* Power BI ondersteunt HANA-informatiemodellen (zoals de weergaven Analyse en Berekenen) en heeft geoptimaliseerde navigatie
* Met **SAP HANA** kunt u ook de directe SQL-functie gebruiken om verbinding te maken met rij- en kolomtabellen
* Bevat geoptimaliseerde navigatie voor HANA-modellen
* Power BI ondersteunt **SAP HANA**-variabelen en -invoerparameters

## <a name="limitations-of-sap-hana"></a>Beperkingen van SAP HANA
Er zijn ook enkele beperkingen voor het gebruik van **SAP HANA**. Deze worden hieronder weergegeven:

* NVARCHAR-tekenreeksen worden afgekapt tot de maximale lengte van 4000 Unicode-tekens
* SMALLDECIMAL wordt niet ondersteund
* VARBINARY wordt niet ondersteund
* Geldige datums liggen tussen 30-12-1899 en 31-12-9999


## <a name="next-steps"></a>Volgende stappen
Bekijk de volgende bronnen voor meer informatie over DirectQuery:

* [DirectQuery en SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Gegevensbronnen die worden ondersteund door DirectQuery](desktop-directquery-data-sources.md)

