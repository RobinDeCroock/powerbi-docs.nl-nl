---
title: Problemen met importeren in Access en met XLS-bestanden oplossen in Power BI Desktop
description: Problemen met het importeren van Access-databases en XLS-spreadsheets oplossen in Power BI Desktop en Power Query
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/21/2019
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 085a21404fefe214656f31d077c6cba401b8219e
ms.sourcegitcommit: 17f45a81b0dcbf9e3f1fb2a551584170baecd320
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72922526"
---
# <a name="resolve-issues-importing-access-and-xls-files-in-power-bi-desktop"></a>Problemen met het importeren van Access- en XLS-bestanden oplossen in Power BI Desktop

In Power BI Desktop maken zowel Access-databases als vroege versies van Excel-werkmappen (XLS-bestanden van het type Excel 97-2003) gebruik van de *Access-database-engine*. Er zijn drie veelvoorkomende situaties die kunnen verhinderen dat de Access-database-engine goed werkt.

## <a name="situation-1-no-access-database-engine-is-installed"></a>Situatie 1: Er is geen Access-database-engine geïnstalleerd

Als het foutbericht in Power BI Desktop aangeeft dat de Access-database-engine niet is geïnstalleerd, moet u de versie van de Access-database-engine (32- of 64-bits) installeren die overeenkomt met uw versie van Power BI Desktop. U kunt de Access-database-engine installeren vanaf de [downloadpagina](http://www.microsoft.com/download/details.aspx?id=13255).

>[!NOTE]
>Als de geïnstalleerde bitsversie van de Access-database-engine niet overeenkomt met de geïnstalleerde bitsversie van Microsoft Office, kunnen Office-toepassingen geen gebruik maken van de Access-database-engine.

## <a name="situation-2-the-access-database-engine-bit-version-32-bit-or-64-bit-is-different-from-your-power-bi-desktop-bit-version"></a>Situatie 2: De bitsversie van de Access-database-engine (32-bits of 64-bits) komt niet overeen met de bitsversie van Power BI Desktop

Deze situatie treedt vaak op wanneer de geïnstalleerde versie van Microsoft Office 32-bits is en de versie van Power BI Desktop 64-bits. Het tegenovergestelde kan ook plaatsvinden en de bitsversie komt in beide gevallen niet overeen. Als u een Office 365-abonnement gebruikt, raadpleegt u [situatie 3](#situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription) voor een ander probleem en bijbehorende oplossing. Met een van de volgende oplossingen kunt u het probleem met de tegengestelde bitsversies oplossen:

### <a name="solution-1"></a>Oplossing 1

Wijzig de versie van Power BI Desktop zodat deze overeenkomt met de bitsversie van het geïnstalleerde Microsoft Office. 

1. Als u de bitsversie van Power BI Desktop wilt wijzigen, verwijdert u Power BI Desktop en installeert u de versie van Power BI Desktop die overeenkomt met uw Office-installatie. 

1. Als u een versie van Power BI Desktop wilt selecteren, selecteert u **Geavanceerde downloadopties** op de downloadpagina van Power BI Desktop.
   
   ![Geavanceerde downloadopties op de downloadpagina van Power BI Desktop](media/desktop-access-database-errors/desktop-access-errors-1.png)
   
1. Kies uw taal en selecteer de knop **Downloaden**. 
 
1. Schakel in het scherm dat verschijnt het selectievakje in naast PBIDesktop.msi voor de 32-bits versie, of naast PBIDesktop_x64.msi voor de 64-bits versie. 

   In de volgende schermopname is de 64-bits versie geselecteerd.
   
   ![Het type Power BI Desktop-download kiezen](media/desktop-access-database-errors/desktop-access-errors-2.png)
   
   >[!NOTE]
   >Als u de 32-bitsversie van Power BI Desktop gebruikt, kunt u geheugenproblemen ondervinden bij het maken van zeer grote gegevensmodellen.

### <a name="solution-2"></a>Oplossing 2

Wijzig de bitsversie van Microsoft Office zodat deze overeenkomt met de bitsversie van uw Power BI Desktop-toepassing:

1. Microsoft Office verwijderen

2. Installeer de versie van Office die overeenkomt met uw Power BI Desktop-toepassing.

### <a name="solution-3"></a>Oplossing 3

Als de fout optreedt bij het openen van een XLS-bestand (een werkmap in Excel 97-2003), kunt u het gebruik van de Access-database-engine vermijden door het XLS-bestand in Excel te openen en het op te slaan als een XLSX-bestand.

### <a name="solution-4"></a>Oplossing 4

Als u het probleem niet kunt oplossen met een van deze drie oplossingen, kunt u beide versies van de Access-database-engine installeren. Deze tijdelijke oplossing wordt echter niet aanbevolen. Als u beide versies installeert, wordt dit probleem met Power Query voor Excel en Power BI Desktop weliswaar opgelost, maar treden er fouten op voor de toepassingen die automatisch (standaard) gebruikmaken van de bitsversie van de Access-database-engine die oorspronkelijk is geïnstalleerd. 

Als u beide bitsversies van de Access-database-engine wilt installeren, voert u de volgende stappen uit:

1. Installeer beide bitsversies van de Access-database-engine vanaf de [downloadpagina](http://www.microsoft.com/download/details.aspx?id=13255). 

1. Voer elke versie van de Access-database-engine uit met behulp van de */passive*-schakelaar. Bijvoorbeeld:
   
       c:\users\joe\downloads\AccessDatabaseEngine.exe /passive
   
       c:\users\joe\downloads\AccessDatabaseEngine_x64.exe /passive

## <a name="situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription"></a>Situatie 3: problemen met Access- of XLS-bestanden bij een Office 365-abonnement

Als u een Office 365-abonnement hebt (dit kan **Office 2013** of **Office 2016** zijn), is de provider van de Access-database-engine geregistreerd in een locatie voor virtuele registers die *alleen* toegankelijk is voor Microsoft Office-processen. Het gevolg is dat de Mashup-engine (die verantwoordelijk is voor het uitvoeren van niet-Office 365 Excel en Power BI Desktop en die geen Office-proces is), geen gebruik kan maken van de provider van de Access-database-engine.

U kunt deze situatie oplossen door de [herdistribueerbare versie van de Access-database-engine te downloaden en te installeren](http://www.microsoft.com/download/details.aspx?id=13255) die overeenkomt met de bitsversie van uw Power BI Desktop-toepassing. Zie de eerdere secties in dit artikel voor meer informatie over bitsversies.

## <a name="other-situations-that-can-cause-import-issues"></a>Andere situaties die problemen met importeren kunnen veroorzaken

Wij proberen zo veel mogelijk problemen met Access- of XLS-bestanden te behandelen. Als u een probleem hebt dat niet in dit artikel wordt behandeld, dien dan een vraag over het probleem in bij [Power BI Support](https://powerbi.microsoft.com/support/) (Ondersteuning van Power BI). Wij kijken regelmatig naar problemen waar veel klanten last van hebben en nemen ze in onze artikelen op.

