---
title: Rapportweergave in Power BI Desktop
description: Rapportweergave in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 3e40d26570e37167c61ffd3241cfe96a90c55fa0
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760544"
---
# <a name="work-with-report-view-in-power-bi-desktop"></a>Werken met de rapportweergave in Power BI Desktop
Als u met Power BI hebt gewerkt, dan weet u hoe eenvoudig het is om rapporten te maken met dynamische perspectieven en inzichten in uw gegevens. Power BI heeft nog meer geavanceerde functies in Power BI Desktop. Met Power BI Desktop kunt u geavanceerde query's uitvoeren, een mashup maken van gegevens uit meerdere bronnen, relaties tussen tabellen maken en nog veel meer.

Power BI Desktop omvat een **rapportweergave**, waarin u een willekeurig aantal rapportpagina's met visuele elementen kunt maken. De rapportweergave kent vrijwel hetzelfde ontwerp als de bewerkweergave van een rapport in de Power BI-service. U kunt er visualisaties verplaatsen, kopiëren en plakken, samenvoegen enzovoort.

Het verschil is dat u in Power BI Desktop met uw query's kunt werken en gegevens kunt modelleren om ervoor te zorgen dat uw rapporten de beste inzichten geven in uw gegevens. U kunt uw Power BI Desktop-bestand vervolgens opslaan waar u wilt, bijvoorbeeld op de lokale harde schijf of in de cloud.

## <a name="lets-take-a-look"></a>Laten we dit eens bekijken.
Wanneer u de eerste keer uw gegevens in Power BI Desktop laadt, ziet u de **rapportweergave** met een leeg canvas.

![Power BI Desktop](media/desktop-report-view/pbi_reportviewinpbidesigner_reportview.png)

U kunt schakelen tussen de **rapportweergave**, **gegevensweergave** en **relatieweergave** door de pictogrammen in het navigatievenster te selecteren:

![Pictogram Rapportweergave](media/desktop-report-view/pbi_reportviewinpbidesigner_changeview.png)

Zodra u gegevens hebt toegevoegd, kunt u velden aan een nieuw visueel element op het canvas toevoegen.

![Een visual toevoegen door deze te slepen vanuit het venster Velden](media/desktop-report-view/pbid_reportview_addvis.gif)

Als u het visualisatietype wilt wijzigen, kunt u dit selecteren in de groep **Visualisatie** in het lint. U kunt ook met de rechtermuisknop klikken en een ander type selecteren via het pictogram **Visualisatietype wijzigen**.

![Een visual wijzigen door een nieuwe te selecteren](media/desktop-report-view/pbid_reportview_changevis.gif)

> [!TIP]
> Experimenteer met verschillende visualisatietypen. Het is belangrijk dat uw visuele elementen de informatie over uw gegevens duidelijk naar voren brengen.

Een rapport bevat ten minste één lege pagina om mee te beginnen. De pagina's worden links van het canvas in de navigatiebalk weergegeven. U kunt allerlei soorten visuele elementen aan een pagina toevoegen, maar het is belangrijk dat u er niet te veel gebruikt. Te veel visuele elementen op een pagina maken deze onoverzichtelijk, waardoor de juiste informatie lastig te vinden is. U kunt nieuwe pagina's toevoegen aan het rapport. U klikt in het lint gewoon op **Nieuwe pagina**.

![Pictogram Nieuwe pagina](media/desktop-report-view/pbidesignerreportviewnewpage.png)

Als u een pagina wilt verwijderen, klikt u op de **x** op het tabblad van de pagina onder aan de rapportweergave.

![Een pagina aan een rapport toevoegen](media/desktop-report-view/pbi_reportviewinpbidesigner_deletepage.png)

> [!NOTE]
> Rapporten en visuele elementen kunnen in Power BI Desktop niet worden vastgemaakt aan een dashboard. Als u dat wilt doen, moet u [publiceren vanuit Power BI Desktop](desktop-upload-desktop-files.md) (Engelstalig) naar uw Power BI-site.

## <a name="copy-and-paste-between-reports"></a>Kopiëren en plakken van het ene naar het andere rapport

U kunt een visual uit een Power BI Desktop-rapport gemakkelijk kopiëren en in een ander rapport plakken. Gebruik de sneltoets **Ctrl+C** om de rapportvisual te kopiëren. Vervolgens plakt u de visual met **Ctrl+V** in het andere Power BI Desktop-rapport. U kunt een visual per keer selecteren of alle visuals op een pagina selecteren en ze vervolgens kopiëren en plakken in het beoogde Power BI Desktop-rapport. 

De mogelijkheid om visuals te kopiëren en plakken is handig voor personen die regelmatig meerdere rapporten maken en bijwerken. Wanneer u elementen naar andere bestanden kopieert, worden de instellingen en opmaak die specifiek zijn ingesteld in het opmaakvenster, ook toegepast in het nieuwe bestand. Visuals die zijn gebaseerd op een thema of de standaardinstellingen, worden automatisch bijgewerkt, zodat ze overeenkomen met het thema van het doelrapport. Als u een visual dus volledig naar wens hebt opgemaakt, kunt u die eenvoudig kopiëren en plakken naar nieuwe rapporten zonder dat uw werk verloren gaat.

Als de velden in uw model afwijken, geeft de visual een foutmelding en een waarschuwing over welke velden niet bestaan. De fout is vergelijkbaar met de fout die optreedt wanneer u een veld uit het model verwijdert dat door de visual wordt gebruikt. 

![Fout bij kopiëren/plakken visual - geen gegevensveld](media/desktop-report-view/report-view_07.png)

Als u deze fout wilt oplossen, vervangt u de betreffende velden met door u gekozen velden uit het model in het rapport waarin u de visual hebt geplakt. Als u een aangepaste visual gebruikt, moet u de aangepaste visual ook in het doelrapport importeren.




## <a name="hide-report-pages"></a>Rapportpagina’s verbergen

Als u een rapport maakt, kunt u ook pagina's uit een rapport verbergen. Dit kan nuttig zijn als u onderliggende gegevens of visuals in een rapport wilt maken, maar u niet wilt dat anderen deze pagina's kunnen zien, bijvoorbeeld als u tabellen of ondersteunende visuals maakt die ook voor andere rapportpagina’s worden gebruikt. Er zijn veel andere creatieve redenen te bedenken waarom u een rapportpagina zou willen maken die u vervolgens wilt verbergen voor een rapport dat u wilt publiceren. 

Een rapportpagina verbergen is eenvoudig. Klik met uw rechtermuisknop op het tabblad Rapportpagina en selecteer **Verbergen** in het menu dat dan verschijnt.

![Optie Pagina verbergen](media/desktop-report-view/report-view_05.png)

Er zijn enkele overwegingen waarmee u rekening moet houden als u een rapportpagina verbergt:

* In **Power BI Desktop** kunt u nog steeds een weergave van een verborgen rapport zien, zelfs als de titel van de pagina in het grijs wordt weergegeven. In de volgende afbeelding is pagina 4 verborgen.

    ![grijs gemaakte pagina die is verborgen](media/desktop-report-view/report-view_06.png)

* U kunt een verborgen rapportpagina *niet* zien als u het rapport weergeeft met de **Power BI-service**.

* Een rapportpagina verbergen is *geen* veiligheidsmaatregel. Gebruikers kunnen nog steeds toegang krijgen tot de pagina en de inhoud is nog steeds toegankelijk door middel van detailanalyse of andere methoden.

* Als een pagina in de Weergavemodus verborgen is, worden er geen navigatiepijlen weergegeven.

