---
title: Vertrouwelijkheidslabels voor Microsoft Information Protection in Power BI
description: Meer informatie over hoe vertrouwelijkheidslabels voor Microsoft Information Protection werken in Power BI
author: paulinbar
ms.author: painbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: conceptual
ms.custom: contperf-fy21q2
ms.date: 12/20/2020
LocalizationGroup: Data from files
ms.openlocfilehash: de7715fc37748ee80cba61f9cc246ad9e1df5c33
ms.sourcegitcommit: a92a3570eb14793a758a32e8fa1a756ec5d83f8c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/21/2020
ms.locfileid: "97708037"
---
# <a name="sensitivity-labels-in-power-bi"></a>Vertrouwelijkheidslabels in Power BI

In dit artikel wordt de functionaliteit beschreven van vertrouwelijkheidslabels voor Microsoft Information Protection in Power BI.

Zie [Vertrouwelijkheidslabels inschakelen in Power BI](service-security-enable-data-sensitivity-labels.md) voor meer informatie over het inschakelen van vertrouwelijkheidslabels voor uw tenant, inclusief vereisten voor licenties.

Zie [Vertrouwelijkheidslabels toepassen in Power BI](./service-security-apply-data-sensitivity-labels.md) voor meer informatie over het toepassen van vertrouwelijkheidslabels op uw inhoud en bestanden in Power BI.

>[!NOTE]
>Ondersteuning voor vertrouwelijkheidslabels in Power BI Desktop bevindt zich momenteel in de preview-fase.

## <a name="introduction"></a>Inleiding

De vertrouwelijkheidslabels voor Microsoft Information Protection bieden gebruikers een eenvoudige manier om essentiële inhoud in Power BI te classificeren zonder dat dit ten koste gaat van de productiviteit of de mogelijkheid om samen te werken. Ze kunnen worden toegepast in Power BI Desktop (preview) en in de Power BI-service. Hierdoor kunt u uw gevoelige gegevens direct beschermen vanaf het moment dat u inhoud begint te ontwikkelen tot wanneer deze toegankelijk wordt via een liveverbinding met Excel. Vertrouwelijkheidslabels blijven behouden wanneer u inhoud, in de vorm van PBIX-bestanden, heen en weer verplaatst tussen de Desktop-versie en de service.

In de Power BI-service kunnen vertrouwelijkheidslabels worden toegepast op gegevenssets, rapporten, dashboards en gegevensstromen. Wanneer gelabelde gegevens Power BI verlaten, hetzij vanwege een export naar Excel-, PowerPoint-, PDF- of PBIX-bestanden, of via een ander ondersteund exportscenario, zoals Analyseren in Excel of draaitabellen in Excel voor liveverbindingen, wordt het label automatisch toegepast op het geëxporteerde bestand en wordt het label beschermd op basis van de instellingen voor bestandsversleutelings van het label. Op deze manier blijven uw gevoelige gegevens ook beschermd wanneer ze Power BI verlaten.

Daarnaast kunnen vertrouwelijkheidslabels worden toegepast op PBIX-bestanden in Power BI Desktop, zodat uw gegevens en inhoud zijn beschermd wanneer ze worden gedeeld buiten Power BI (bijvoorbeeld zodat alleen gebruikers binnen uw organisatie een vertrouwelijk PBIX-bestand dat is gedeeld in of bijgevoegd bij een e-mailbericht, kunnen openen), nog vóórdat ze zijn gepubliceerd in de Power BI-service. Raadpleeg [Toegang tot inhoud beperken met behulp van vertrouwelijkheidslabels om versleuteling toe te passen](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide) voor meer details.

Vertrouwelijkheidslabels op rapporten, dashboards, gegevenssets en gegevensstromen zijn op veel plaatsen in de Power BI-service zichtbaar. Vertrouwelijkheidslabels voor rapporten en dashboards zijn ook zichtbaar in de mobiele Power BI-apps voor iOS en Android en in ingesloten visuals. In de Desktop-versie ziet u het vertrouwelijkheidslabel in de statusbalk.

Het [rapport met metrische gegevens over beveiliging](service-security-data-protection-metrics-report.md) dat beschikbaar is in de beheerportal van Power BI, biedt Power BI-beheerders volledig zicht op de gevoelige informatie in de Power BI-tenant. Daarnaast bevatten de auditlogboeken van Power BI vertrouwelijkheidslabelinformatie over activiteiten zoals het toepassen, verwijderen en wijzigen van labels, en over activiteiten zoals het weergeven van rapporten, dashboards enzovoort. Hierdoor krijgen Power BI- en beveiligingsbeheerders inzicht in het gebruik van vertrouwelijke gegevens ten behoeve van het bewaken en onderzoeken van beveiligingswaarschuwingen.

## <a name="important-considerations"></a>Belangrijke overwegingen

In de Power BI-service heeft het toepassen van vertrouwelijkheidslabels **geen** invloed op de toegang tot de inhoud. Toegang tot inhoud in de service wordt uitsluitend beheerd via Power BI-machtigingen. Hoewel de labels zichtbaar zijn, worden de bijbehorende versleutelingsinstellingen (geconfigureerd in het [Microsoft 365-beveiligingscentrum](https://security.microsoft.com/) of het [Microsoft 365-compliancecentrum](https://compliance.microsoft.com/)) niet toegepast. Ze worden alleen toegepast op gegevens die de service verlaten via een ondersteund exportpad, zoals exporteren naar Excel-, PowerPoint- of PDF-bestand, en downloaden in een PBIX-bestand.

In Power BI Desktop (preview) heeft het toepassen van vertrouwelijkheidslabel met versleutelingsinstellingen **wel** invloed op de toegang tot de inhoud. Als een gebruiker niet beschikt over voldoende [machtigingen](#power-bi-desktop-preview) volgens de versleutelingsinstellingen van het vertrouwelijkheidslabel voor het PBIX-bestand, kan deze het bestand niet openen. Daarnaast worden in de Desktop-versie alle eventuele vertrouwelijkheidslabels die u hebt toegevoegd, en de bijbehorende instellingen, toegepast op het opgeslagen PBIX-bestand, zelfs wanneer u uw werk opslaat.

Vertrouwelijkheidslabels en bestandsversleuteling **worden niet** toegepast op niet-ondersteunde exportpaden. De Power BI-beheerder kan het exporteren van niet-ondersteunde exportpaden blokkeren.

>[!NOTE]
> Gebruikers aan wie toegangsrechten voor een rapport worden verleend, krijgen toegang tot de hele onderliggende gegevensset, tenzij de toegang wordt beperkt door [beveiliging op rijniveau (RLS)](./service-admin-rls.md). Ontwerpers van rapporten kunnen rapporten classificeren en labelen met behulp van vertrouwelijkheidslabels. Als het vertrouwelijkheidslabel beveiligingsinstellingen heeft, worden deze beveiligingsinstellingen in Power BI toegepast wanneer het rapport Power BI verlaat via een ondersteund exportpad, zoals exporteren naar een Excel-, PowerPoint- of PDF-bestand, of downloaden naar een PBIX-bestand, en **Opslaan** (Desktop). Alleen geautoriseerde gebruikers kunnen beveiligde bestanden openen.

### <a name="supported-export-paths"></a>Ondersteunde exportpaden
Het toepassen van vertrouwelijkheidslabels en de bijbehorende beveiliging op gegevens die de Power BI-service verlaten, wordt momenteel ondersteund voor de volgende exportpaden:
* Exporteren naar Excel-, PDF- (alleen de service) en PowerPoint-bestanden.
* Analyseren in Excel vanuit de Power BI-service, waarmee een Excel-bestand wordt gedownload met een liveverbinding met een Power BI-gegevensset.
* Draaitabel in Excel met een liveverbinding met een Power BI-gegevensset voor gebruikers met M365 E3 en hoger.
* Downloaden naar PBIX-bestand (service)

>[!NOTE]
>Wanneer u in de Power BI-service **Het PBIX-bestand downloaden** gebruikt, en op het gedownloade rapport en de bijbehorende gegevensset verschillende labels zijn toegepast, wordt het meer beperkende label toegepast op het PBIX-bestand. 

## <a name="how-sensitivity-labels-work-in-power-bi"></a>Hoe vertrouwelijkheidslabels werken in Power BI

Wanneer u een vertrouwelijkheidslabel toepast op inhoud en bestanden in Power BI, is dit vergelijkbaar met het toepassen van een tag op deze resource. Dit levert de volgende voordelen op:
* **Aanpasbaar**: u kunt categorieën maken voor verschillende niveaus van gevoelige inhoud in uw organisatie, zoals Persoonlijk, Openbaar, Algemeen, Vertrouwelijk en Zeer vertrouwelijk.
* **Duidelijke tekst**: omdat de tekst op het label vrij duidelijk is, kunnen gebruikers gemakkelijk begrijpen hoe ze de inhoud moeten behandelen volgens de richtlijnen voor vertrouwelijkheidslabels.
* **Persistentie**: nadat een vertrouwelijkheidslabel is toegepast op inhoud, blijft dit label van toepassing wanneer deze inhoud wordt geëxporteerd naar een Excel-, PowerPoint- en PDF-bestand, wordt gedownload naar een PBIX-bestand, of wordt opgeslagen (Desktop). Bovendien wordt het label de basis voor het toepassen en afdwingen van beleidsregels.

Hier kunt u aan de hand van een voorbeeld zien hoe vertrouwelijkheidslabels in Power BI werken. In de onderstaande afbeelding ziet u hoe een vertrouwelijkheidslabel wordt toegepast op een rapport in de Power BI-service, hoe de gegevens uit het rapport worden geëxporteerd naar een Excel-bestand en hoe het vertrouwelijkheidslabel en de beveiligingen behouden blijven in het geëxporteerde bestand.

![GIF-animatie waarin de toepassing en persistentie van vertrouwelijkheidslabels wordt getoond](media/service-security-sensitivity-label-overview/ApplyLabelandProtection.gif)

De vertrouwelijkheidslabels die u op inhoud toepast, blijven behouden en roamen met de inhoud terwijl deze in Power BI wordt gebruikt en gedeeld. U kunt het labelen gebruiken om gebruiksrapporten te genereren en om activiteitsgegevens voor uw gevoelige inhoud te zien.

## <a name="sensitivity-labels-in-power-bi-desktop-preview"></a>Vertrouwelijkheidslabels in Power BI Desktop (preview)

Vertrouwelijkheidslabels kunnen ook worden toegepast in Power BI Desktop. Hierdoor kunt u uw gegevens beschermen vanaf het moment dat u inhoud begint te ontwikkelen. Wanneer u uw werk opslaat in de Desktop-versie, wordt het vertrouwelijkheidslabel dat u hebt toegepast, samen met alle eventuele bijbehorende versleutelingsinstellingen, toegepast op het resulterende PBIX-bestand. Als het label versleutelingsinstellingen heeft, is het bestand hiermee overal beveiligd, ongeacht of en hoe het bestand wordt verplaatst. Alleen gebruikers met de [benodigde RMS-machtigingen](#power-bi-desktop-preview) kunnen het bestand openen.

>[!NOTE]
>* In deze preview-release kunnen enkele beperkingen van toepassing zijn. Zie [Beperkingen](#limitations).
>* Gedurende de eerste 48 uur na het inschakelen van de preview-functie Information Protection **kunt u problemen ondervinden met PBIX-bestanden waarop vertrouwelijkheidslabels zijn toegepast (bijvoorbeeld bij het publiceren van het PBIX-bestand in de service, of het downloaden ervan vanuit de service)** . Dergelijke problemen zijn verwacht en worden binnen 48 uur automatisch opgelost.

Als u een vertrouwelijkheidslabel toepast in de Desktop-versie, en u uw werk vervolgens publiceert in de service of een PBIX-bestand met uw werk uploadt naar de service, wordt het label samen met de gegevens verplaatst naar de service. In de service wordt het label toegepast op zowel de gegevensset als op het rapport dat u krijgt bij het bestand. Als de gegevensset en het rapport al vertrouwelijkheidslabels hebben, worden deze labels overschreven met het label dat afkomstig is uit de Desktop-versie.
 
Als u een PBIX-bestand uploadt dat nog niet eerder is gepubliceerd in de service, en dat dezelfde naam heeft als een rapport of gegevensset die al bestaat in de service, slaagt het uploaden alleen als degene die uploadt, beschikt over de benodigde RMS-machtigingen om het label te wijzigen.

Hetzelfde geldt ook andersom: als u inhoud downloadt naar een PBIX-bestand in de service, en het PBIX-bestand vervolgens in de Desktop-versie laadt, wordt het label dat actief was in de service, toegepast op het gedownloade PBIX-bestand en op deze manier in de Desktop-versie geladen. Als het rapport en de gegevensset in de service verschillende labels hebben, wordt het meer beperkende van de twee labels toegepast op het gedownloade PBIX-bestand.

Wanneer u een label toepast in de Desktop-versie, wordt het weergegeven in de statusbalk.

![Schermopname van een vertrouwelijkheidslabel op de statusbalk van de Desktop-versie.](media/service-security-sensitivity-label-overview/sensitivity-label-in-desktop-status-bar.png)

[Meer informatie over het toepassen van vertrouwelijkheidslabels op inhoud en bestanden in Power BI](./service-security-apply-data-sensitivity-labels.md).


## <a name="sensitivity-label-inheritance-upon-creation-of-new-content"></a>Overname van vertrouwelijkheidslabels bij het maken van nieuwe inhoud

Wanneer er nieuwe rapporten en dashboards worden gemaakt in de Power BI-service, nemen ze automatisch het vertrouwelijkheidslabel over dat eerder is toegepast op de bovenliggende gegevensset of het rapport. Als er bijvoorbeeld een nieuw rapport wordt gemaakt voor een gegevensset met het vertrouwelijkheidslabel Zeer vertrouwelijk, wordt dit label ook automatisch toegepast op het nieuwe rapport.

In de volgende afbeelding ziet u hoe het vertrouwelijkheidslabel van een gegevensset automatisch wordt toegepast op een nieuw rapport dat op basis van de gegevensset is gebouwd.

![GIF-animatie waarin de overname van vertrouwelijkheidslabels wordt getoond](media/service-security-sensitivity-label-overview/InheritanceUponCreation.gif)

>[!NOTE]
>Als het vertrouwelijkheidslabel om welke reden dan ook niet kan worden toegepast op het nieuwe rapport of dashboard, kan Power BI **niet voorkomen** dat er een nieuw item wordt gemaakt.

## <a name="sensitivity-labels-and-protection-on-exported-data"></a>Vertrouwelijkheidslabels en beveiliging voor geëxporteerde gegevens

Wanneer gegevens worden geëxporteerd van Power BI naar Excel-, PowerPoint- of PDF-bestanden (alleen service), wordt in Power BI automatisch een vertrouwelijkheidslabel toegepast op het geëxporteerde bestand en wordt het beschermd op basis van de labelinstellingen voor bestandsversleuteling. Zodoende blijven uw gevoelige gegevens beschermd, ongeacht waar ze zich bevinden.

Een gebruiker die een bestand uit Power BI exporteert, beschikt over machtigingen voor toegang tot en het bewerken van dat bestand volgens de instellingen voor het vertrouwelijkheidslabel. Ze hebben geen eigenaarsmachtiging voor het bestand.

>[!NOTE]
>Wanneer u in de Power BI-service **Het PBIX-bestand downloaden** gebruikt, en op het gedownloade rapport en de bijbehorende gegevensset verschillende labels zijn toegepast, wordt het meer beperkende label toegepast op het PBIX-bestand. 

Vertrouwelijkheidslabels en beveiliging worden niet toegepast wanneer gegevens worden geëxporteerd naar CSV-bestanden, of een ander niet-ondersteund exportpad.

Bij het toepassen van een vertrouwelijkheidslabel en beveiliging op een geëxporteerd bestand wordt geen markering van inhoud toegevoegd aan het bestand. Als het label echter is geconfigureerd voor het toepassen van inhoudsmarkeringen, worden de markeringen automatisch toegepast door de Azure Information Protection Unified labeling-client wanneer het bestand wordt geopend in Office-bureaublad-apps. De inhoudsmarkeringen worden niet automatisch toegepast wanneer u ingebouwde labels gebruikt voor desktop-, mobiele of web-apps. Zie [Wanneer Office-apps inhoud markeren en versleutelen](/microsoft-365/compliance/sensitivity-labels-office-apps#when-office-apps-apply-content-marking-and-encryption) voor meer details.

Het exporteren mislukt als een label niet kan worden toegepast wanneer gegevens naar een bestand worden geëxporteerd. Als u wilt controleren of het exporteren is mislukt omdat het label niet kan worden toegepast, klikt u op de naam van het rapport of het dashboard in het midden van de titelbalk en kijkt u of de tekst Vertrouwelijkheidslabel kan niet worden geladen in de info-vervolgkeuzelijst wordt weergegeven. Dit kan gebeuren als gevolg van een tijdelijk systeemprobleem of als het toegepaste label niet is gepubliceerd of verwijderd door de beveiligingsbeheerder.

## <a name="sensitivity-label-inheritance-in-analyze-in-excel"></a>Overname van vertrouwelijkheidslabels in Analyseren in Excel

Wanneer u een draaitabel in Excel maakt met een liveverbinding naar een Power BI-gegevensset (u kunt dit doen vanuit Power BI via [Analyseren in Excel](../collaborate-share/service-analyze-in-excel.md) of vanuit [Excel](https://support.microsoft.com/office/create-a-pivottable-from-power-bi-datasets-31444a04-9c38-4dd7-9a45-22848c666884?ui=en-US&rs=en-US&ad=US)), wordt het vertrouwelijkheidslabel van de gegevensset overgenomen en toegepast op het Excel-bestand, samen met de bijbehorende beveiliging. Als het label van de gegevensset later wordt gewijzigd in een meer beperkend label, wordt het label dat is toegepast op het gekoppelde Excel-bestand, automatisch bijgewerkt bij het vernieuwen van de gegevens.

![Schermopname van Excel waarin het vertrouwelijkheidslabel wordt weergegeven dat via een liveverbinding is overgenomen van een gegevensset.](media/service-security-sensitivity-label-overview/live-connection-inheritance.png)
 
Vertrouwelijkheidslabels in Excel die handmatig zijn ingesteld, worden niet automatisch overschreven met het vertrouwelijkheidslabel van de gegevensset. In plaats hiervan geeft een banner aan dat de gegevensset een vertrouwelijkheidslabel heeft, en wordt u aangeraden om dit toe te passen.

>[!NOTE]
>Als het vertrouwelijkheidslabel van de gegevensset minder beperkend is dan het vertrouwelijkheidslabel van het Excel-bestand, wordt het label niet overgenomen of bijgewerkt. Een Excel-bestand neemt nooit een minder beperkend vertrouwelijkheidslabel over.

## <a name="sensitivity-label-persistence-in-embedded-reports-and-dashboards"></a>Persistentie van vertrouwelijkheidslabel in ingesloten rapporten en dashboards

U kunt Power BI-rapporten, -dashboards en -visuals insluiten in zakelijke toepassingen zoals Microsoft Teams en SharePoint of op de website van een organisatie. Wanneer u een visual, rapport of dashboard insluit waarop een vertrouwelijkheidslabel is toegepast, wordt het vertrouwelijkheidslabel zichtbaar in de ingesloten weergave, en blijven het label en de bijbehorende beveiliging gehandhaafd wanneer gegevens worden geëxporteerd naar Excel.

![Schermopname van een rapport dat is ingesloten in SharePoint Online](media/service-security-sensitivity-label-overview/embedded-report-sensitivity-label.png)

De volgende insluitingsscenario's worden ondersteund:
* [Insluiten voor uw organisatie](../developer/embedded/embed-sample-for-your-organization.md)
* Microsoft 365-apps (bijvoorbeeld [Teams](../collaborate-share/service-embed-report-microsoft-teams.md) en [SharePoint](../collaborate-share/service-embed-report-spo.md))
* [Veilige URL insluiten](../collaborate-share/service-embed-secure.md) (insluiten vanuit de Power BI-service) 

## <a name="sensitivity-labels-in-the-power-bi-mobile-apps"></a>Vertrouwelijkheidslabels in de mobiele Power BI-apps

Vertrouwelijkheidslabels kunnen worden weergegeven in rapporten en dashboards in de mobiele Power BI-apps. Een pictogram in de buurt van de naam van het rapport of dashboard geeft aan dat het een vertrouwelijkheidslabel heef. Het type label en een beschrijving van het label vindt u in het informatievak van het rapport of dashboard.

![Schermopname van een vertrouwelijkheidslabel in een mobiele app](media/service-security-sensitivity-label-overview/mobile-app-sensitivity-label2.png)

## <a name="supported-clouds"></a>Ondersteunde clouds
Vertrouwelijkheidslabels worden alleen ondersteund in algemene (openbare) clouds en niet voor tenants in clouds, zoals nationale clouds.

## <a name="licensing-and-requirements"></a>Licenties en vereisten

Zie [Licenties en vereisten](service-security-enable-data-sensitivity-labels.md#licensing-and-requirements).

## <a name="sensitivity-label-creation-and-management"></a>Vertrouwelijkheidslabel maken en beheren

Gevoeligheidslabel worden gemaakt en beheerd in het [Microsoft 365-beveiligingscentrum](https://security.microsoft.com/) of het [Microsoft 365-compliancecentrum](https://compliance.microsoft.com/).

Voor toegang tot vertrouwelijkheidslabels in deze centra navigeert u naar **Classificatie > Vertrouwelijkheidslabels**. Deze vertrouwelijkheidslabels kunnen worden gebruikt door meerdere Microsoft-services zoals Azure Information Protection, Office-apps en Office 365-services.

>[!Important]
> Als uw organisatie Azure Information Protection-vertrouwelijkheidslabels gebruikt, moet u naar een van de eerder genoemde services [migreren](/azure/information-protection/configure-policy-migrate-labels) om de labels te kunnen gebruiken in Power BI.

## <a name="limitations"></a>Beperkingen

### <a name="general"></a>Algemeen

* Het wordt niet aanbevolen om gebruikers toe te staan bovenliggende labels toe te passen in Power BI (een label wordt alleen als een bovenliggend label beschouwd als het sublabels heeft). Als een bovenliggend label wordt toegepast op inhoud, mislukt het exporteren van gegevens uit deze inhoud naar een bestand (Excel, PowerPoint en PDF). Zie [Sublabels (labels groeperen)](/microsoft-365/compliance/sensitivity-labels#sublabels-grouping-labels).

* Vertrouwelijkheidslabels voor gegevens worden niet ondersteund voor sjabloon-apps. Gevoeligheidslabels die door de maker van de sjabloon-app zijn ingesteld, worden verwijderd wanneer de app wordt uitgepakt en geïnstalleerd, en gevoeligheidslabels die door gebruikers van de app aan artefacten in een geïnstalleerde sjabloon-app zijn toegevoegd, gaan verloren (opnieuw ingesteld op niets) wanneer de app wordt bijgewerkt.

* Als een gegevensset in de Power BI-service een label heeft dat is verwijderd uit het beheercentrum voor labels, kunt u de gegevens niet exporteren of downloaden. In Analyseren in Excel wordt een waarschuwing gegenereerd, en de gegevens worden geëxporteerd naar een ODC-bestand zonder vertrouwelijkheidslabel. Als een PBIX-bestand in de Desktop-versie een dergelijk ongeldig label heeft, kunt u het bestand niet opslaan.

* Power BI biedt geen ondersteuning voor vertrouwelijkheidslabels van de beveiligingstypen [Niet doorsturen](/microsoft-365/compliance/encryption-sensitivity-labels#let-users-assign-permissions), [Door de gebruiker gedefinieerd](/microsoft-365/compliance/encryption-sensitivity-labels#let-users-assign-permissions) en [HYOK](/azure/information-protection/configure-adrms-restrictions). De beveiligingstypen Niet doorsturen en Door de gebruiker gedefinieerd verwijzen naar labels die zijn gedefinieerd in het [Microsoft 365-beveiligingscentrum](https://security.microsoft.com/) of het [Microsoft 365-compliancecentrum](https://compliance.microsoft.com/).

### <a name="power-bi-service"></a>Power BI-service

* Vertrouwelijkheidslabels kunnen alleen worden toegepast op dashboards, rapporten, gegevenssets en gegevensstromen. Ze zijn momenteel niet beschikbaar voor [gepagineerde rapporten](../paginated-reports/report-builder-power-bi.md) en werkmappen.

* Vertrouwelijkheidslabels op Power BI-assets zijn zichtbaar in de werkruimtelijst en de weergaven Herkomst, Favorieten, Recente items en Apps; labels zijn momenteel niet zichtbaar in de weergave Gedeeld met mij. Houd er echter rekening mee dat een label dat op een Power BI-asset is toegepast, zelfs als dit niet zichtbaar is, permanent worden toegevoegd aan de gegevens die naar Excel-, PowerPoint- en PDF-bestanden worden geëxporteerd.

### <a name="power-bi-desktop-preview"></a>Power BI Desktop (preview)

* Beveiligde PBIX-bestanden kunnen alleen worden geopend en/of gepubliceerd door een gebruiker die de RMS-eigenaar van het bestand is (de gebruiker die het label oorspronkelijk heeft toegepast op het bestand), of die [**Volledig beheer** heeft en/of beschikt over de gebruiksrechten](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide) voor **Exporteren** voor het relevante label. De RMS-eigenaar heeft Volledig beheer en kan nooit worden geblokkeerd. [Meer details bekijken](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner)

* Als het label dat is toegepast op een PBIX-bestand, niet is gepubliceerd voor de gebruiker in het Microsoft 365-beveiligingcentrum of in het Microsoft 365-compliancecentrum, kan de gebruiker het bestand niet opslaan in de Desktop-versie.

* Power BI Desktop-gebruikers kunnen problemen ondervinden bij het opslaan van hun werk wanneer de internetverbinding is verbroken, bijvoorbeeld wanneer ze offline gaan. Zonder internetverbinding worden sommige acties die betrekking hebben op vertrouwelijkheidslabels en rechtenbeheer, mogelijk niet juist voltooid. In dergelijke gevallen wordt aangeraden om weer online te gaan en opnieuw te proberen op te slaan.

* Als u een groot model hebt gemaakt en het resulterende beveiligde PBIX-bestand heel groot is (groter dan 2 GB), kan het bestand vastlopen wanneer u het wilt opslaan of openen. Als tijdelijke oplossing kunt u de beveiliging van het PBIX-bestand verwijderen en opnieuw toepassen nadat het bestand is gepubliceerd in de Power BI-service.

    Over het algemeen is het een goed idee om, wanneer u een bestand beveiligt met een vertrouwelijkheidslabel waarmee versleuteling wordt toegepast, ook een andere versleutelingsmethode te gebruiken, zoals versleuteling met wisselbestanden, NTFS-versleuteling, BitLocker, antimalware, enzovoort.

* Tijdelijke bestanden worden niet versleuteld.

* Met **Gegevens ophalen** kunnen beveiligde bestanden alleen worden opgehaald als ze lokaal zijn. Beveiligde bestanden uit onlineservices, zoals SharePoint Online of OneDrive voor Bedrijven, kunnen niet worden geüpload. Een beveiligd bestand kunt u uploaden vanaf een lokaal apparaat, of u kunt eerst het label van het bestand verwijderen in Power BI Desktop, en het bestand vervolgens uploaden via een van de onlineservices.

* **Exporteren naar PDF** biedt geen ondersteuning voor vertrouwelijkheidslabels. Als u een bestand dat een vertrouwelijkheidslabel bevat, exporteert naar de PDF-indeling, wordt het label niet overgedragen op het PDF-bestand en is er geen beveiliging toegepast.

* Gegevensbeveiliging in Power BI Desktop biedt geen ondersteuning voor **B2B** en **scenario's met meerdere tenants**.

## <a name="next-steps"></a>Volgende stappen

In dit artikel hebt u een overzicht gekregen van gegevensbeveiliging in Power BI. De volgende artikelen bieden meer informatie over gegevensbeveiliging in Power BI. 

* [Vertrouwelijkheidslabels inschakelen in Power BI](service-security-enable-data-sensitivity-labels.md)
* [Vertrouwelijkheidslabels toepassen in Power BI](service-security-apply-data-sensitivity-labels.md)
* [Microsoft Cloud App Security-besturingselementen gebruiken in Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Rapport met metrische gegevens voor beveiliging](service-security-data-protection-metrics-report.md)