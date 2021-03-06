---
title: 'Organisatie-inhoudspakketten: Toegang en kopiëren'
description: Meer informatie over het maken van kopieën van inhoudspakketten van uw organisatie in Power BI en over het oplossen van problemen hiermee
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp, kayu
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 01/12/2021
LocalizationGroup: Share your work
ms.openlocfilehash: 2fd2bca7e031d4a758031f80db0825f5af9e897c
ms.sourcegitcommit: ab28cf07b483cb4b01a42fa879b788932bba919d
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/15/2021
ms.locfileid: "98227233"
---
# <a name="organizational-content-packs-copy-refresh-and-get-access"></a>Organisatie-inhoudspakketten: Kopiëren, vernieuwen en toegang krijgen

> [!NOTE]
> Organisatie-inhoudspakketten worden afgeschaft. Het is nu een goed moment om uw inhoudspakketten te upgraden naar apps, als u dat nog niet hebt gedaan. Raadpleeg de sectie over roadmap voor de werkruimte-upgrade van deze blogpost [Aangekondigd: Power BI-beheerders kunnen klassieke werkruimten upgraden](https://powerbi.microsoft.com/blog/announcing-power-bi-admins-can-upgrade-classic-workspaces-and-roadmap-update/) voor de tijdlijn.
> 

Wanneer een organisatie-inhoudspakket wordt gepubliceerd, zien alle ontvangers de hetzelfde dashboard en dezelfde rapporten, Excel-werkmappen, gegevenssets en gegevens (tenzij het een SSAS-gegevensbron is (SQL Server Analysis Services).  [Alleen de maker van het inhoudspakket kan het inhoudspakket bewerken en opnieuw publiceren](service-organizational-content-pack-manage-update-delete.md).  Alle ontvangers kunnen echter een kopie van het inhoudspakket opslaan die naast het origineel kan bestaan.

Het maken van inhoudspakketten verschilt van het delen van dashboards of het samenwerken aan een dashboard in een groep. Lees [Samen aan dashboards en rapporten werken en deze delen?](service-how-to-collaborate-distribute-dashboards-reports.md) om te bepalen wat de beste optie is voor 

## <a name="create-a-copy-of-an-organizational-content-pack"></a>Een kopie maken van een organisatie-inhoudspakket
Maak uw eigen kopie van het inhoudspakket die niet zichtbaar is voor anderen.

1. Selecteer **Meer opties** (...) naast het dashboard van het inhoudspakket > Een kopie maken.

    ![Schermopname van een dialoogvenster voor meer opties.](media/service-organizational-content-pack-copy-refresh-access/power-bi-create-copy-organizational-content-pack.png)
2. Selecteer **Opslaan**.  

U hebt nu een kopie die u kunt wijzigen. Niemand anders ziet de wijzigingen die u aanbrengt.

> [!NOTE]
> Voorheen werd telkens een nieuwe gegevensset in de inhoudslijst van de werkruimte weergegeven wanneer u een inhoudspakket installeerde of hiervan een kopie maakte. Dankzij een recente update is de ervaring vereenvoudigd en wordt nu nog maar één item weergegeven met behulp van het nieuwe pictogram voor de gegevensset waarnaar wordt verwezen:
>
> ![pictogram database met koppeling](media/service-organizational-content-pack-copy-refresh-access/power-bi-dataset-reference-icon.png)
>

## <a name="help--i-can-no-longer-access-the-content-pack"></a>Help!  Ik heb geen toegang meer tot het inhoudspakket
Dit kan gebeuren om verschillende redenen:

* **Lidmaatschapswijzigingen**:  inhoudspakketten worden gepubliceerd naar e-maildistributiegroepen, beveiligingsgroepen en [Power BI-groepen op basis van Microsoft 365](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9).  Als u uit de groep wordt verwijderd, hebt u geen toegang meer tot het inhoudspakket.
* **Distributiewijzigingen**: de maker van het inhoudspakket wijzigt de distributie. Als het inhoudspakket bijvoorbeeld oorspronkelijk is gepubliceerd voor de hele organisatie, maar de maker het opnieuw heeft gepubliceerd voor een kleinere doelgroep, bent u daar mogelijk niet in opgenomen.
* **Gewijzigde beveiligingsinstellingen**: als het dashboard en de rapporten verbinding hebben met on-premises SSAS-gegevensbronnen en er wijzigingen worden aangebracht in de beveiligingsinstellingen, kunnen uw toegangsrechten tot die server worden ingetrokken.

## <a name="how-are-organizational-content-packs-refreshed"></a>Hoe worden organisatie-inhoudspakketten vernieuwd?
Wanneer het inhoudspakket is gemaakt, worden de vernieuwingsinstellingen overgenomen bij de gegevensset.  Wanneer u een kopie van het inhoudspakket maakt, blijven de koppeling naar de oorspronkelijke gegevensset en het schema voor gegevensvernieuwing behouden in de nieuwe versie.

Zie [Organisatie-inhoudspakketten beheren, bijwerken en verwijderen](service-organizational-content-pack-manage-update-delete.md).

## <a name="next-steps"></a>Volgende stappen
* [Inleiding tot organisatie-inhoudspakketten](service-organizational-content-pack-introduction.md)
* [Een groep maken in Power BI](service-create-distribute-apps.md)
* Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
