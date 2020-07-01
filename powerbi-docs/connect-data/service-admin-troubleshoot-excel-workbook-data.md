---
title: 'Fout: Kan geen gegevens vinden in uw Excel-werkmap'
description: 'Fout: Kan geen gegevens vinden in uw Excel-werkmap'
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/30/2019
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 5daf16cbd557be14f8b30900aabd560160d27736
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85222321"
---
# <a name="error-we-couldnt-find-any-data-in-your-excel-workbook"></a>Fout: Kan geen gegevens vinden in uw Excel-werkmap

>[!NOTE]  
>Dit artikel is van toepassing op Excel 2007 en hoger.

Wanneer u een Excel-werkmap in Power BI importeert, wordt mogelijk de volgende fout weergegeven:

*Fout: Kan geen gegevens ingedeeld als tabel vinden. Als u vanuit Excel wilt importeren in de Power BI-service, moet u de gegevens opmaken als een tabel. Selecteer alle gegevens voor de tabel en druk op Ctrl + T.*

![Kan geen gegevens vinden in werkmap](media/service-admin-troubleshoot-excel-workbook-data/power-bi-we-couldnt-find-any-data.png)

## <a name="quick-solution"></a>Snelle oplossing
1. Bewerk uw werkmap in Excel.
2. Selecteer het celbereik met uw gegevens. De eerste rij moet de kolomkoppen (kolomnamen) bevatten.
3. Druk op **Ctrl + T** om een tabel te maken.
4. Sla uw werkmap op.
5. Ga terug naar Power BI en importeer de werkmap of, als u in Excel 2016 werkt en u de werkmap hebt opgeslagen in OneDrive voor Bedrijven, klik in Excel op Bestand > Publiceren.

## <a name="details"></a>Details
### <a name="cause"></a>Oorzaak
In Excel kunt u een **tabel** van een celbereik maken, waardoor u gemakkelijker gegevens kunt sorteren, filteren en opmaken.

Wanneer u een Excel-werkmap importeert, worden deze tabellen door Power BI gezocht en geïmporteerd in een gegevensset. Als er geen tabellen worden gevonden, wordt dit foutbericht weergegeven.

### <a name="solution"></a>Oplossing
1. Open uw werkmap in Excel. 
    >[!NOTE]
    >De afbeeldingen die hier worden getoond zijn van Excel 2013. Als u een andere versie gebruikt, ziet alles er misschien net iets anders uit, maar zijn de stappen hetzelfde.
    
    ![Werkmap openen](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-1.png)
2. Selecteer het celbereik met uw gegevens. De eerste rij moet de kolomkoppen (kolomnamen) bevatten:
   
    ![Bereik van cellen selecteren](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-2.png)
3. Klik in het lint op het tabblad **Invoegen** op **Tabel**. (Of druk op de snelkoppeling **Ctrl + T**.)
   
    ![Tabel invoegen](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-3.png)
4. Het volgende dialoogvenster wordt weergegeven. Zorg ervoor dat het selectievakje **Mijn tabel bevat kopteksten** is ingeschakeld en selecteer **OK**:
   
    ![Tabel maken](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-create-table.png)
5. Uw gegevens zijn nu opgemaakt als een tabel:
   
    ![Gegevens opgemaakt als tabel](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-table.png)
6. Sla uw werkmap op.
7. Ga terug naar bij Power BI. Selecteer Gegevens ophalen onderaan het navigatievenster.
   
    ![Gegevens ophalen](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-data.png)
8. Selecteer in het vak **Bestanden** de optie **Ophalen**.
   
    ![Bestanden ophalen](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-files.png)
9. Importeer uw Excel-werkmap opnieuw. Deze keer moet de import de tabel vinden en slagen.
   
    Als het importeren nog steeds mislukt, kunt u ons dat laten weten door in het menu Help op ** Community ** te klikken:
   
    ![Koppeling naar community](media/service-admin-troubleshoot-excel-workbook-data/power-bi-question-menu-community.png)
