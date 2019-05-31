---
title: Vertrouwde Connectors van derden in Power BI
description: Het vertrouwen van een ondertekende van derden-connector in Power BI
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 30b7457c6149320c43f24b967a842382821b01b1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65607796"
---
# <a name="trusting-third-party-connectors"></a>Vertrouwen van connectors van derden

## <a name="why-do-you-need-trusted-third-party-connectors"></a>Waarom moet u de vertrouwde connectors van derden?

In Power BI raden we in het algemeen uitbreiding van uw gegevensbeveiliging niveau op het hogere niveau, waarmee wordt voorkomen het laden van code die niet door Microsoft laten certificeren dat. Echter, kunnen er veel gevallen waarin u wilt laden van specifieke connectors--die u hebt geschreven, of waarden die u van een consultant of de leverancier van buiten het certificeringspad van Microsoft.

De ontwikkelaar van een bepaalde connector kan deze ondertekenen met een certificaat en u voorzien van informatie die u nodig het veilig laden zonder uw beveiligingsinstellingen te verlagen.

Als u meer weten over de beveiligingsinstellingen wilt, kunt u lezen over deze [hier](https://docs.microsoft.com/power-bi/desktop-connector-extensibility).

## <a name="using-the-registry-to-trust-third-party-connectors"></a>Met behulp van het register te vertrouwen connectors van derden

Vertrouwen van connectors van derden in Power BI wordt gedaan door de vingerafdruk van het certificaat dat u wilt vertrouwen in een opgegeven registerwaarde weer te geven. Als deze vingerafdruk overeenkomt met de vingerafdruk van het certificaat op de connector die u wilt laden, kunt u zich te laden in het beveiligingsniveau 'Aanbevolen' van Power BI. 

Het registerpad is HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop. Zorg ervoor dat het pad bestaat of maken. We hebben gekozen voor deze locatie vanwege het hoofdzakelijk wordt beheerd door IT-beleid, evenals vereisen lokale machine beheertoegang om te bewerken. 

![Power BI Desktop register geen vertrouwde externe sleutels instellen](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Voeg een nieuwe waarde onder het opgegeven pad. Het type moet 'waarde met meerdere tekenreeksen"(REG_MULTI_SZ), en deze moet worden aangeroepen"TrustedCertificateThumbprints" 

![Power BI Desktop register met een vermelding voor vertrouwde connectors van derden, maar er zijn geen sleutels](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Voeg de vingerafdrukken van de certificaten die u wilt vertrouwen. U kunt meerdere certificaten met behulp van '\0' als scheidingsteken, of in de Register-editor, rechts -> Klik op wijzigen en de vingerafdruk van elke plaats op een nieuwe regel toevoegen. Voorbeeld van een vingerafdruk is afkomstig uit een zelfondertekend certificaat. 

 ![Power BI Desktop register met een vertrouwde derde sleutel instellen](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Als u de instructies correct hebt gevolgd, en de vingerafdruk van het juiste hebben gekregen van de ontwikkelaar, zou het nu mogelijk voor veilig vertrouwensrelatie connectors die zijn ondertekend met het bijbehorende certificaat.

## <a name="how-to-sign-connectors"></a>Het ondertekenen van Connectors

Als u een connector u of een ontwikkelaar moet zich aanmelden, kunt u meer informatie over het in de Power Query-documenten [hier](https://docs.microsoft.com/power-query/handlingconnectorsigning).
