---
title: 'Project Online: verbinding met gegevens maken via Power BI Desktop'
description: 'Project Online: verbinding met gegevens maken via Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/01/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0f01a6da3bb0d829d396861814f71d33ba69f22f
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83291921"
---
# <a name="connect-to-project-online-data-through-power-bi-desktop"></a>Verbinding maken met Project Online-gegevens via Power BI Desktop
U kunt verbinding maken met gegevens maken in Project Online via Power BI Desktop.

## <a name="step-1-download-power-bi-desktop"></a>Stap 1: Power BI Desktop downloaden
1. [Download Power BI Desktop](https://go.microsoft.com/fwlink/?LinkID=521662) en voer vervolgens het installatieprogramma uit om **Power BI Desktop** op uw computer te installeren.

## <a name="step-2-connect-to-project-online-with-odata"></a>Stap 2: verbinding maken met Project Online met OData
1. Open **Power BI Desktop**.
2. Selecteer *Gegevens ophalen* in het **welkomstscherm**.
3. Kies **OData-feed** en selecteer **Verbinding maken**.
4. Voer het adres voor uw OData-feed in het URL-vak in en klik op OK.
   
   Als het adres voor uw Project Web App-site lijkt op *https://\<tenantnaam\>.sharepoint.com/sites/pwa*, is het adres dat u invoert voor uw OData-feed *https://\<tenantnaam\>.sharepoint.com/sites/pwa/\_api/Projectdata*.
   
   Voor ons voorbeeld gebruiken we:

    `https://contoso.sharepoint.com/sites/pwa/default.aspx`

5. Power BI Desktop vraagt u om te verifiëren met uw Office 365-account. Selecteer Organisatieaccount en voer uw referenties in.
   
   ![](media/desktop-project-online-connect-to-data/image.png)

Het account waarmee u verbinding maakt met de OData-feed moet ten minste Portfolioviewer-toegang tot de Project Web App-site hebben. 

Vanaf hier kunt u kiezen met welke tabellen u verbinding wilt maken en een query bouwen.  Wilt u een idee krijgen van hoe u aan de slag kunt gaan?  In de volgende blogbost wordt beschreven hoe u een burndowndiagram kunt maken van uw Project Online-gegevens.  Deze blogpost verwijst naar het gebruik van Power Query om verbinding te maken met Project Online, maar dit is ook van toepassing op Power BI Desktop.

[Burndowndiagrammen maken voor project met behulp van Power Pivot en Power Query](https://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)
