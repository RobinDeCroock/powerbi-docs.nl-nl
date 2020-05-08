---
title: Vertrouwde connectoren van derden in Power BI
description: Een ondertekende connector van derden vertrouwen in Power BI
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 05db20b2f83f10409339fad949874fc1076a6b98
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "75759831"
---
# <a name="trusted-third-party-connectors"></a>Vertrouwde externe connectoren

## <a name="why-do-you-need-trusted-third-party-connectors"></a>Waarom hebt u vertrouwde connectoren van derden nodig?

In Power BI wordt u aangeraden het niveau van uw 'beveiliging van gegevensextensies' op een hoger niveau te houden, waardoor het niet mogelijk is om code te laden die niet door Microsoft is gecertificeerd. Er zijn echter veel gevallen waarin u specifieke connectoren wilt laden die u hebt geschreven of die u hebt ontvangen van een consultant of leverancier buiten het Microsoft-certificeringspad.

De ontwikkelaar van een bepaalde connector kan deze ondertekenen met een certificaat en u de informatie verstrekken die u nodig hebt om deze veilig te laden zonder uw beveiligingsinstellingen te verlagen.

[Hier](https://docs.microsoft.com/power-bi/desktop-connector-extensibility) vindt u meer informatie over de beveiligingsinstellingen.

## <a name="using-the-registry-to-trust-third-party-connectors"></a>Het register gebruiken om connectoren van derden te vertrouwen

Het vertrouwen van connectoren van derden in Power BI wordt uitgevoerd door de vingerafdruk van het certificaat dat u wilt vertrouwen in een opgegeven registerwaarde te vermelden. Als deze vingerafdruk overeenkomt met de vingerafdruk van het certificaat op de connector die u wilt laden, kunt u deze laden in het beveiligingsniveau 'Aanbevolen' van Power BI. 

Het registerpad is HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop. Zorg ervoor dat het pad bestaat of maak het pad. We hebben deze locatie gekozen omdat deze primair wordt beheerd door IT-beleid, en toegang tot lokaal machinebeheer vereist voor bewerking. 

![Power BI Desktop-register zonder vertrouwde sleutels van derden](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Voeg een nieuwe waarde toe onder het hierboven opgegeven pad. Het type moet 'Waarde met meerdere tekenreeksen' (REG_MULTI_SZ) zijn en moet de naam 'TrustedCertificateThumbprints' hebben 

![Power BI Desktop-register met een vermelding voor vertrouwde connectoren van derden, maar geen sleutels](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Voeg de vingerafdrukken van de certificaten die u wilt vertrouwen toe. U kunt meerdere certificaten toevoegen met behulp van '\0' als scheidingsteken of in de register-editor. Klik met de rechtermuisknop Wijzigen en plaats elke vingerafdruk op een nieuwe regel. Er wordt een voorbeeld van een vingerafdruk gemaakt van een zelfondertekend certificaat. 

 ![Power BI Desktop-register met een vertrouwde sleutel van derden](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Als u de instructies op de juiste manier hebt gevolgd en de juiste vingerafdruk hebt gekregen van uw ontwikkelaar, moet u nu veilig connectoren kunnen vertrouwen die zijn ondertekend met het bijbehorende certificaat.

## <a name="how-to-sign-connectors"></a>Connectoren ondertekenen

Als u een connector hebt die u of een ontwikkelaar moet ondertekenen, kunt u hierover meer lezen in de Power Query-documenten [hier](https://docs.microsoft.com/power-query/handlingconnectorsigning).
