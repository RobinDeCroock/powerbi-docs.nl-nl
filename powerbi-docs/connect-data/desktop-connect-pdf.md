---
title: Verbinding maken met een PDF-bestand in Power BI Desktop
description: Eenvoudig verbinding maken met gegevens in PDF-bestanden in Power BI Desktop en deze gebruiken
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: e68d860800f2265923189e470bc633589e612c11
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85224159"
---
# <a name="connect-to-pdf-files-in-power-bi-desktop"></a>Verbinding maken met PDF-bestanden in Power BI Desktop
In Power BI Desktop kunt u verbinding maken met een **PDF-bestand** en gebruikmaken van de opgenomen gegevens, net zoals elke andere gegevensbron in Power BI Desktop.

![Verbinding maken met gegevens in PDF-bestanden](media/desktop-connect-pdf/connect-pdf-04.png)

In de volgende secties wordt beschreven hoe u verbinding maakt met een **PDF-bestand**, gegevens selecteert en die gegevens overbrengt naar **Power BI Desktop**.

Het wordt altijd aanbevolen te upgraden naar de meest recente versie van **Power BI Desktop**, die u via een koppeling in [Power BI Desktop downloaden](../fundamentals/desktop-get-the-desktop.md) kunt krijgen. 

## <a name="connect-to-a-pdf-file"></a>Verbinding maken met een PDF-bestand
Als u verbinding wilt maken met een **PDF**-bestand, selecteert u **Gegevens ophalen** op het lint **Start** in Power BI Desktop. Selecteer **Bestand** in de categorieën aan de linkerkant en u ziet **PDF**.

![PDF selecteren in Gegevens ophalen](media/desktop-connect-pdf/connect-pdf-01.png)

U wordt gevraagd naar de locatie van het PDF-bestand dat u wilt gebruiken. Als u de bestandslocatie hebt opgegeven en het PDF-bestand wordt geladen, wordt een **Navigator**-scherm weergegeven waarin de gegevens van het bestand worden getoond. Hier kunt u een of meer elementen selecteren die u in **Power BI Desktop** wilt importeren en gebruiken.

![Verbinding maken met gegevens in PDF-bestanden](media/desktop-connect-pdf/connect-pdf-04.png)

Wanneer u een selectievakje naast gedetecteerde elementen in het PDF-bestand markeert, worden deze weergegeven in het rechterdeelvenster. Wanneer u klaar bent om te importeren, selecteert u de knop **Laden** om de gegevens in **Power BI Desktop** te laden.

Sinds de **Power BI Desktop**-versie van november 2018 kunt u de **Startpagina** en **Eindpagina** opgeven als optionele parameters voor uw pdf-bestand. U kunt deze parameters ook opgeven in de M-formuletaal. Maak daarbij gebruik van de volgende indeling:

`Pdf.Tables(File.Contents("c:\sample.pdf"), [StartPage=10, EndPage=11])`


## <a name="next-steps"></a>Volgende stappen
Met Power BI Desktop kunt u verbinding maken met allerlei andere gegevens. Bekijk de volgende bronnen voor meer informatie over gegevensbronnen:

* [Wat is Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Gegevensbronnen in Power BI Desktop](desktop-data-sources.md)
* [Gegevens vormgeven en combineren met Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connect to Excel workbooks in Power BI Desktop](desktop-connect-excel.md) (Verbinding maken met Excel-werkmappen in Power BI Desktop)   
* [Enter data directly into Power BI Desktop](desktop-enter-data-directly-into-desktop.md) (Rechtstreeks gegevens in Power BI Desktop invoeren)   
