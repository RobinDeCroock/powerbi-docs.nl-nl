---
title: Gegevensbeveiliging in Power BI
description: Informatie over gegevensbeveiliging in Power BI
author: paulinbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/21/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: fa969f8f738cf09e9e01e284de8f60e2fd8ce9ab
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315667"
---
# <a name="data-protection-in-power-bi"></a>Gegevensbeveiliging in Power BI

Moderne ondernemingen hebben strikte bedrijfsregelgeving en vereisten voor het verwerken en beveiligen van gevoelige gegevens. Power BI is geïntegreerd met Microsoft Information Protection en Microsoft Cloud App Security om beter beheer en betere zichtbaarheid van gevoelige gegevens in Power BI te krijgen. Hiermee kunt u:
* Gebruik de [vertrouwelijkheidslabels](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide) van Microsoft Information Protection om inhoud in de Power BI-service (dashboards, rapporten, gegevenssets en gegevensstromen) te classificeren en te labelen, met behulp van dezelfde taxonomie die wordt gebruikt om bestanden in Office 365 te classificeren en te beveiligen.
* Pas vertrouwelijkheidslabels en beveiliging van Microsoft Information Protection toe op gegevens wanneer deze worden geëxporteerd naar Excel-, PowerPoint- of PDF-bestanden.
* Gebruik Microsoft Cloud App Security om activiteiten in Power BI bij te houden, beveiligingsproblemen te onderzoeken en inhoud in Power BI te beveiligen met App-beheer voor voorwaardelijke toegang van Microsoft Cloud App Security.

**Belangrijke opmerkingen**
* Vertrouwelijkheidslabels zijn **niet** van invloed op de toegang tot inhoud in Power BI: de toegang tot inhoud in Power BI wordt uitsluitend beheerd via Power BI-machtigingen. Hoewel de labels zichtbaar zijn, worden de bijbehorende versleutelingsinstellingen (geconfigureerd in het [Microsoft 365-beveiligingscentrum](https://security.microsoft.com/) of het [Microsoft 365-compliancecentrum](https://compliance.microsoft.com/)) niet toegepast. Ze worden alleen toegepast op gegevens die worden geëxporteerd naar Excel-, PowerPoint- en PDF-bestanden.
* Vertrouwelijkheidslabels en bestandsversleuteling worden **niet** toegepast in andere exportpaden dan exportpaden naar Excel, PowerPoint en PDF. De Power BI-tenantbeheerder kan bepaalde of alle exportpaden uitschakelen waarvoor vertrouwelijkheidslabels en de bijbehorende bestandsversleutelingsinstellingen niet worden ondersteund.

## <a name="sensitivity-labels-in-power-bi"></a>Vertrouwelijkheidslabels in Power BI

Gevoeligheidslabel worden gemaakt en beheerd in het [Microsoft 365-beveiligingscentrum](https://security.microsoft.com/) of het [Microsoft 365-compliancecentrum](https://compliance.microsoft.com/).

Voor toegang tot vertrouwelijkheidslabels in deze centra navigeert u naar **Classificatie > Vertrouwelijkheidslabels**. Deze vertrouwelijkheidslabels kunnen worden gebruikt door meerdere Microsoft-services zoals Azure Information Protection, Office-apps en Office 365-services.

> [!Important]
> Als uw organisatie Azure Information Protection-vertrouwelijkheidslabels gebruikt, moet u naar een van de eerder genoemde services [migreren](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels) om de labels te kunnen gebruiken in Power BI.

> [!NOTE]
> Vertrouwelijkheidslabels worden alleen ondersteund in openbare clouds en niet voor tenants in clouds, zoals onafhankelijke clouds.

## <a name="how-sensitivity-labels-work-in-power-bi"></a>Hoe vertrouwelijkheidslabels werken in Power BI

Wanneer u een vertrouwelijkheidslabel toepast op een Power BI-dashboard, -rapport, -gegevensset of -gegevensstroom, is dit vergelijkbaar met het toepassen van een tag op die resource. Dit levert de volgende voordelen op:
* **Aanpasbaar**: u kunt categorieën maken voor verschillende niveaus van gevoelige inhoud in uw organisatie, zoals Persoonlijk, Openbaar, Algemeen, Vertrouwelijk en Zeer vertrouwelijk.
* **Duidelijke tekst**: omdat de tekst op het label vrij duidelijk is, kunnen gebruikers gemakkelijk begrijpen hoe ze de inhoud moeten behandelen volgens de richtlijnen voor vertrouwelijkheidslabels.
* **Persistentie**: nadat een vertrouwelijkheidslabel is toegepast op inhoud, wordt de inhoud ervan meegenomen bij het exporteren naar Excel-, PowerPoint en PDF-bestanden. Bovendien wordt het label de basis voor het toepassen en afdwingen van beleidsregels.

Dit houdt in dat het vertrouwelijkheidslabel de inhoud volgt bij het exporteren naar Excel-, PowerPoint- en PDF-bestanden. Bovendien wordt het label de basis voor het toepassen en afdwingen van beleidsregels.

Power BI-tenantbeheerders kunnen opties voor het [exporteren naar Excel-bestanden](service-admin-portal.md#export-to-excel) en [exporteren naar PowerPoint- en PDF-bestanden](service-admin-portal.md#export-reports-as-powerpoint-presentations-or-pdf-documents) beheren in de [Power BI-beheerportal](service-admin-portal.md).

## <a name="sensitivity-label-example"></a>Voorbeeld van een vertrouwelijkheidslabel

Hier ziet u een voorbeeld van de manier waarop een vertrouwelijkheidslabel in Power BI kan werken.
1. In de Power BI-service is het vertrouwelijkheidslabel **Zeer vertrouwelijk** toegepast op een rapport.

   ![Vertrouwelijkheidslabels in de lijstweergave](media/service-security-data-protection-overview/sensitivity-labels-overview-01.png)
   
1. Wanneer gegevens vanuit dit rapport worden geëxporteerd naar een Excel-bestand, worden het vertrouwelijkheidslabel en de beveiliging toegepast op het geëxporteerde Excel-bestand.

   ![Vertrouwelijkheidslabel volgt de inhoud](media/service-security-data-protection-overview/sensitivity-labels-overview-02.png)

In Microsoft Office-toepassingen wordt een vertrouwelijkheidslabel als een tag aan de e-mail of het document weergegeven, vergelijkbaar met wat er is weergegeven in de bovenstaande afbeelding. U kunt ook een classificatie aan de inhoud toewijzen (zoals een sticker) die bij de inhoud blijft en met de inhoud meegaat wanneer de gebruiker deze inhoud gebruikt en deelt in Power BI. U kunt deze classificatie gebruiken om gebruiksrapporten te genereren en om activiteitsgegevens voor uw gevoelige inhoud te zien. Op basis van deze informatie kunt u er altijd later voor kiezen om beveiligingsinstellingen toe te passen.

## <a name="requirements-for-using-sensitivity-labels-in-power-bi"></a>Vereisten voor het gebruik van vertrouwelijkheidslabels in Power BI

Voordat uw vertrouwelijkheidslabels kunnen worden ingeschakeld en gebruikt in Power BI, moet u eerst aan de volgende vereisten voldoen:
* Controleer of gevoeligheidslabels zijn gedefinieerd in het [Microsoft 365-beveiligingscentrum](https://security.microsoft.com/) of het [Microsoft 365-compliancecentrum](https://compliance.microsoft.com/).
* [Schakel vertrouwelijkheidslabels in](service-security-enable-data-sensitivity-labels.md) in Power BI.
* Controleer of gebruikers de [juiste licenties](#licensing) hebben.
* Als u Microsoft Cloud App Security gebruikt in combinatie met Power BI, moet u beschikken over de [juiste licenties](service-security-using-microsoft-cloud-app-security-controls.md#cloud-app-security-licensing).

## <a name="protect-content-using-microsoft-cloud-app-security"></a>Inhoud beveiligen met Microsoft Cloud App Security

U kunt inhoud in Power BI beveiligen tegen onbedoelde lekken of inbreuk met behulp van Microsoft Cloud App Security. Zodra Microsoft Cloud App Security is ingesteld en geconfigureerd, kunnen beveiligingsbeheerders gebruikerstoegang en -activiteit bijhouden, realtime risicoanalyse uitvoeren en labelspecifieke besturingselementen instellen.

Organisaties kunnen bijvoorbeeld Microsoft Cloud App Security gebruiken om een beleid in te stellen dat voorkomt dat gebruikers gevoelige gegevens vanuit Power BI kunnen downloaden naar onbeheerde apparaten. Met een dergelijke configuratie kunnen gebruikers productief blijven en vanuit elke locatie verbinding maken met Power BI, terwijl ze Microsoft Cloud App Security gebruiken om gebruikersacties te voorkomen die mogelijk voor problemen zorgen, allemaal in realtime.

**Vereisten**

Voordat u voor uw vertrouwelijkheidslabels gebruik kunt maken van Microsoft Cloud App Security, moet aan de volgende vereisten worden voldaan:
* Cloud App Security en Azure Information Protection [moeten worden ingeschakeld voor uw tenant](https://docs.microsoft.com/cloud-app-security/azip-integration).
* De app [moet worden verbonden met Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps).

## <a name="licensing"></a>Licentieverlening

* Voor het toepassen en weergeven van Microsoft Information Protection-vertrouwelijkheidslabels in Power BI is een Azure Information Protection Premium P1- of Premium P2-licentie vereist. Microsoft Azure Information Protection kan ofwel als zelfstandig product als via een van de Microsoft-licentiesuites worden aangeschaft. Zie [Prijzen voor Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/) voor meer informatie.
* Er gelden [licentievereisten](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels#subscription-and-licensing-requirements-for-sensitivity-labels) voor het weergeven en toepassen van labels in Office-apps.
* Als gebruikers labels willen toepassen op Power BI-inhoud, moeten ze naast een van de bovenstaande Azure Information Protection-licenties ook over een Power BI Pro-licentie beschikken.
* U moet de [benodigde licenties voor Microsoft Cloud App Security](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls#microsoft-cloud-app-security-licensing) hebben als u het wilt gebruiken om Power BI-inhoud te beschermen tegen onbedoelde lekken en inbreuken.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

De volgende lijst biedt een aantal beperkingen van vertrouwelijkheidslabels in Power BI:

**Algemeen**
* Vertrouwelijkheidslabels kunnen alleen worden toegepast op dashboards, rapporten, gegevenssets en gegevensstromen. Ze zijn momenteel niet beschikbaar voor [gepagineerde rapporten](../paginated-reports/report-builder-power-bi.md) en werkmappen.
* Vertrouwelijkheidslabels op Power BI-assets zijn zichtbaar in de werkruimtelijst en de weergaven Herkomst, Favorieten, Recente items en Apps; labels zijn momenteel niet zichtbaar in de weergave Gedeeld met mij. Houd er echter rekening mee dat een label dat op een Power BI-asset is toegepast, zelfs als dit niet zichtbaar is, permanent worden toegevoegd aan de gegevens die naar Excel-, PowerPoint- en PDF-bestanden worden geëxporteerd.
* Vertrouwelijkheidslabels worden alleen ondersteund voor tenants in de wereldwijde (openbare) cloud. Vertrouwelijkheidslabels worden niet ondersteund voor tenants in andere clouds.
* Vertrouwelijkheidslabels voor gegevens worden niet ondersteund voor sjabloon-apps. Gevoeligheidslabels die door de maker van de sjabloon-app zijn ingesteld, worden verwijderd wanneer de app wordt uitgepakt en geïnstalleerd, en gevoeligheidslabels die door gebruikers van de app aan artefacten in een geïnstalleerde sjabloon-app zijn toegevoegd, gaan verloren (opnieuw ingesteld op niets) wanneer de app wordt bijgewerkt.
* Power BI biedt geen ondersteuning voor vertrouwelijkheidslabels van de beveiligingstypen [Niet doorsturen](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions), [Door de gebruiker gedefinieerd](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions) en [HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions). De beveiligingstypen Niet doorsturen en Door de gebruiker gedefinieerd verwijzen naar labels die zijn gedefinieerd in het [Microsoft 365-beveiligingscentrum](https://security.microsoft.com/) of het [Microsoft 365-compliancecentrum](https://compliance.microsoft.com/).
* U wordt afgeraden gebruikers toe te staan om bovenliggende labels toe te passen in Power BI. Als een bovenliggend label wordt toegepast op inhoud, mislukt het exporteren van gegevens van die inhoud naar een bestand (Excel, PowerPoint en PDF). Zie [Sublabels (labels groeperen)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide#sublabels-grouping-labels).

**Exporteren**
* Besturingselementen voor labels en beveiliging worden alleen afgedwongen wanneer gegevens worden geëxporteerd naar Excel-, PowerPoint-en PDF-bestanden. Labels en beveiliging worden niet afgedwongen wanneer gegevens worden geëxporteerd naar CSV- of PBIX-bestanden, Analyseren in Excel of een ander exportpad.
* Bij het toepassen van een vertrouwelijkheidslabel en beveiliging op een geëxporteerd bestand wordt geen markering van inhoud toegevoegd aan het bestand. Als het label echter is geconfigureerd voor het toepassen van inhoudsmarkeringen, worden ze automatisch toegepast door de Azure Information Protection Unified labeling-client wanneer het bestand wordt geopend in Office-bureaublad-apps. De inhoudsmarkeringen worden niet automatisch toegepast wanneer u ingebouwde labels gebruikt voor desktop-, mobiele of web-apps. Zie [Wanneer Office-apps inhoud markeren en versleutelen](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption) voor meer details.
* Een gebruiker die een bestand uit Power BI exporteert, beschikt over machtigingen voor toegang tot en het bewerken van dat bestand volgens de instellingen voor het vertrouwelijkheidslabel. De gebruiker die de gegevens exporteert, krijgt geen eigenaarsmachtigingen voor het bestand.
* Het exporteren mislukt als een label niet kan worden toegepast wanneer gegevens naar een bestand worden geëxporteerd. Als u wilt controleren of het exporteren is mislukt omdat het label niet kan worden toegepast, klikt u op de naam van het rapport of het dashboard in het midden van de titelbalk en kijkt u of de tekst 'Vertrouwelijkheidslabel kan niet worden geladen' in de info-vervolgkeuzelijst wordt weergegeven. Dit kan gebeuren als het toegepaste label niet is gepubliceerd of verwijderd door de beveiligingsbeheerder of als gevolg van een tijdelijk systeemprobleem.


## <a name="next-steps"></a>Volgende stappen

In dit artikel hebt u een overzicht gekregen van gegevensbeveiliging in Power BI. De volgende artikelen bieden meer informatie over gegevensbeveiliging in Power BI. 

* [Vertrouwelijkheidslabels voor gegevens in Power BI inschakelen](service-security-enable-data-sensitivity-labels.md)
* [Vertrouwelijkheidslabels voor gegevens toepassen in Power BI](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Microsoft Cloud App Security-besturingselementen gebruiken in Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Metrisch rapport gegevensbescherming](service-security-data-protection-metrics-report.md)