---
title: Power BI rapporten-API exporteren
description: Meer informatie over hoe u een ingesloten Power BI-rapport kunt exporteren
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 03/24/2020
ms.openlocfilehash: db907897256ef4afc0bdb9a253a23880b6e79f53
ms.sourcegitcommit: 5ece366fceee9832724dae40eacf8755e1d85b04
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81525463"
---
# <a name="export-power-bi-report-to-file-preview"></a>Power BI-rapport exporteren naar bestand (preview)

Via de API `exportToFile` kunt u een Power BI-rapport exporteren met behulp van een REST-aanroep. De volgende bestandsindelingen worden ondersteund:
* **.pptx** (PowerPoint)
* **.pdf**
* **.png**
    * Wanneer u exporteert naar een PNG-bestand, wordt een rapport met meerdere pagina's gecomprimeerd naar een ZIP-bestand
    * Elk bestand in de ZIP vertegenwoordigt een rapportpagina
    * De paginanamen zijn dezelfde als de retourwaarden van de API voor [pagina’s ophalen](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) of [pagina’s in groep ophalen](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup)

## <a name="usage-examples"></a>Gebruiksvoorbeelden

U kunt de exportfunctie op verschillende manieren gebruiken. Hieronder vindt u enkele voorbeelden:

* **Knop Verzenden voor afdrukken**: maak in uw toepassing een knop waarmee een exporttaak wordt geactiveerd wanneer u erop klikt. Met de taak kan het weergegeven rapport worden geëxporteerd als een PDF- of PPTX-bestand. Wanneer dit is voltooid, kan de gebruiker het bestand ontvangen als een download. Met behulp van bladwijzers kunt u het rapport met een specifieke configuratie exporteren, bijvoorbeeld met filters, slicers en aanvullende instellingen. Aangezien de API asynchroon is, kan het enige tijd duren voordat het bestand beschikbaar is.

* **E-mailbijlage**: verzend op gezette tijden een geautomatiseerd e-mailbericht met een bijgevoegd PDF-rapport. Dit scenario kan handig zijn als u het verzenden van een wekelijks rapport naar leidinggevenden wilt automatiseren.

## <a name="using-the-api"></a>De API gebruiken

Voordat u de API gebruikt, moet u controleren of de volgende [beheerdersinstellingen voor de tenant](../../service-admin-portal.md#tenant-settings) zijn ingeschakeld:
* **Rapporten als PowerPoint-presentaties of PDF-documenten exporteren** - Standaard ingeschakeld.
* **Rapporten exporteren als afbeeldingsbestanden**: alleen vereist voor *PNG* en standaard uitgeschakeld.

De API is asynchroon. Wanneer de API [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile) is aangeroepen, wordt een exporttaak geactiveerd. Nadat de exporttaak is geactiveerd, gebruikt u [polling](https://docs.microsoft.com/rest/api/power-bi/reports/getexporttofilestatus) om de taak bij te houden totdat deze is voltooid.

Tijdens de polling retourneert de API een getal dat de hoeveelheid voltooid werk vertegenwoordigt. Het werk in elke exporttaak wordt berekend op basis van het aantal pagina's van het rapport. Alle pagina's hebben hetzelfde gewicht. Als u bijvoorbeeld een rapport met 10 pagina's exporteert en de polling 70 pagina’s retourneert, betekent dit dat met de API zeven van de 10 pagina's in de exporttaak zijn verwerkt.

Wanneer het exporteren is voltooid, retourneert de polling-API-aanroep een [Power BI-URL](https://docs.microsoft.com/rest/api/power-bi/reports/getfileofexporttofile) om het bestand op te halen. De URL is 24 uur beschikbaar.

## <a name="supported-features"></a>Ondersteunde functies

### <a name="selecting-which-pages-to-print"></a>Selecteren welke pagina's u wilt afdrukken

Geef de pagina’s op die u wilt afdrukken, volgens de retourwaarde voor [pagina’s ophalen](https://docs.microsoft.com/rest/api/power-bi/reports/getpages) of [pagina’s in groep ophalen](https://docs.microsoft.com/rest/api/power-bi/reports/getpagesingroup). U kunt ook de volgorde opgeven van de pagina's die u wilt exporteren.

### <a name="bookmarks"></a>Bladwijzers

 U kunt de `exportToFile`-API gebruiken om via een programma een rapport in een specifieke staat te exporteren, nadat u filters hebt toegepast. Dit doet u met behulp van de mogelijkheden van [Bladwijzers](../../consumer/end-user-bookmarks.md). Als u een rapport wilt exporteren met behulp van bladwijzers, gebruikt u de [JavaScript-API voor bladwijzers](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks).

 U kunt bijvoorbeeld de methode `capturedBookmark.state` van de bladwijzer gebruiken om de wijzigingen vast te leggen die een specifieke gebruiker heeft aangebracht in een rapport, en het rapport vervolgens in de huidige staat te exporteren.

[Persoonlijke bladwijzers](../../consumer/end-user-bookmarks.md#personal-bookmarks) en [permanente filters](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) worden niet ondersteund.

### <a name="authentication"></a>Verificatie

U kunt verifiëren met behulp van een gebruiker (of hoofdgebruiker) of een [service principal](embed-service-principal.md).

### <a name="row-level-security-rls"></a>RLS (Beveiliging op rijniveau)

Met [RLS (Beveiliging op rijniveau)](embedded-row-level-security.md) kunt u een rapport exporteren waarin gegevens worden weergegeven die alleen zichtbaar zijn voor bepaalde gebruikers. Als u bijvoorbeeld een verkooprapport exporteert dat is gedefinieerd met regionale rollen, kunt u het rapport via een programma filteren, zodat alleen een bepaalde regio wordt weergegeven.

U moet beschikken over de volgende machtigingen om te kunnen exporteren met behulp van RLS:
* Machtigingen voor schrijven en opnieuw delen voor de gegevensset waarmee het rapport is verbonden
* Als het rapport zich in een v1-werkruimte bevindt, moet u de werkruimtebeheerder zijn
* Als het rapport zich in een v2-werkruimte bevindt, moet u lid of beheerder van de werkruimte zijn

### <a name="data-protection"></a>Gegevensbescherming

De PDF- en PPTX-indeling bieden ondersteuning voor [gevoeligheidslabels](../../admin/service-security-data-protection-overview.md#sensitivity-labels-in-power-bi). Als u een rapport met een gevoeligheidslabel exporteert naar een PDF- of PPTX-bestand, wordt het rapport in het geëxporteerde bestand weergegeven met het bijbehorende gevoeligheidslabel.

Een rapport met een vertrouwelijkheidslabel kan niet worden geëxporteerd naar een PDF- of een PPTX-bestand met behulp van een [service principal](embed-service-principal.md).

### <a name="localization"></a>Lokalisatie

Wanneer u de `exportToFile`-API gebruikt, kunt u de gewenste locatie doorgeven. De lokalisatie-instellingen beïnvloeden de manier waarop het rapport wordt weergegeven, bijvoorbeeld door de opmaak aan te passen aan de geselecteerde locatie.

## <a name="concurrent-requests"></a>Gelijktijdige aanvragen

`exportToFile` biedt ondersteuning voor gelijktijdige aanvragen voor een exporttaak. In de volgende tabel wordt het aantal taken weergegeven dat u tegelijkertijd kunt uitvoeren, afhankelijk van de SKU waarin uw rapport zich bevindt. Bij gelijktijdige aanvragen wordt gekeken naar het aantal rapportpagina's. Bijvoorbeeld: 20 pagina's in één exportaanvraag in een A6-SKU worden gelijktijdig verwerkt. Dit duurt ongeveer net zolang als het verzenden van 20 exportaanvragen met elk één pagina.

Een taak die het aantal gelijktijdige aanvragen overschrijdt, wordt niet beëindigd. Als u bijvoorbeeld drie pagina's in een A1-SKU exporteert, wordt de eerste taak uitgevoerd en wordt bij de laatste twee taken gewacht op de volgende twee uitvoeringscycli.

|Azure SKU  |Office SKU  |Maximum aantal gelijktijdige rapportpagina's  |
|-----------|------------|-----------|
|A1         |EM1         |1          |
|A2         |EM2         |2          |
|A3         |EM3         |3          |
|A4         |P1          |6          |
|A5         |P2          |12         |
|A6         |P3          |24         |

## <a name="limitations"></a>Beperkingen

* Het rapport dat u exporteert, moet zich in een Premium- of Embedded-capaciteit bevinden.
* De gegevensset van het rapport dat u exporteert, moet zich in een Premium- of Embedded-capaciteit bevinden.
* Voor de openbare preview is het aantal Power BI-rapportpagina's dat per uur wordt geëxporteerd, beperkt tot 50 per capaciteit.
* Geëxporteerde rapporten mogen de bestandsgrootte van 250 MB niet overschrijden.
* Wanneer u exporteert naar PNG, worden gevoeligheidslabels niet ondersteund.
* Een rapport met een vertrouwelijkheidslabel kan niet worden geëxporteerd naar een PDF- of een PPTX-bestand met behulp van een [service principal](embed-service-principal.md).
* Er kunnen maximaal 30 pagina's worden opgenomen in een geëxporteerd rapport. Als het rapport meer pagina's bevat, retourneert de API een fout en wordt de exporttaak geannuleerd.
* [Persoonlijke bladwijzers](../../consumer/end-user-bookmarks.md#personal-bookmarks) en [permanente filters](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) worden niet ondersteund.
* Zelfstandige clouds worden niet ondersteund.
* De hieronder vermelde Power BI-visuals worden niet ondersteund. Wanneer u een rapport exporteert dat deze visuals bevat, worden de gedeelten van het rapport die deze visuals bevatten, niet weergegeven. In plaats hiervan ziet u een foutsymbool.
    * Niet-gecertificeerde visuals in Power BI
    * R-visuals
    * PowerApps
    * Python-visuals
    * Visio

## <a name="code-examples"></a>Codevoorbeelden

Wanneer u een exporttaak maakt, moet u de volgende drie stappen uitvoeren:

1. Een exportaanvraag verzenden.
2. Polling uitvoeren.
3. Het bestand ophalen.

Deze sectie bevat voorbeelden voor elke stap.

### <a name="step-1---sending-an-export-request"></a>Stap 1: een exportaanvraag verzenden

De eerste stap is het verzenden van een exportaanvraag. In dit voorbeeld wordt een exportaanvraag verzonden voor een specifieke pagina.

```csharp
/////// Export sample ///////
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    IList<string> pageNames = null /* Get the page names from the GetPages API */)
{
    var powerBIReportExportConfiguration = new PowerBIReportExportConfiguration
    {
        Settings = new ExportReportSettings
        {
            Locale = "en-us",
        },
        // Note that page names differ from the page display names.
        // To get the page names use the GetPages API.
        Pages = pageNames?.Select(pn => new ExportReportPage(Name = pn)).ToList(),
    };
    var exportRequest = new ExportReportRequest
    {
        Format = format,
        PowerBIReportConfiguration = powerBIReportExportConfiguration,
    };
    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);
    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>Stap 2: polling uitvoeren

Nadat u een exportaanvraag hebt verzonden, gebruikt u polling om te bepalen wanneer het exportbestand waarop u wacht, gereed is.

```csharp
private async Task<Export> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the ExportToAsync response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int c_secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations 
            return null;
        }
        var httpMessage = await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
        exportStatus = httpMessage.Body;
        // You can track the export progress using the PercentComplete that's part of the response
        SomeTextBox.Text = string.Format("{0} (Percent Complete : {1}%)", exportStatus.Status.ToString(), exportStatus.PercentComplete);
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;
            await Task.Delay(retryAfterInSec * c_secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);
    return exportStatus;
}
```

### <a name="step-3---getting-the-file"></a>Stap 3: het bestand ophalen

Zodra met polling een URL wordt geretourneerd, gebruikt u dit voorbeeld om het ontvangen bestand op te halen.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the GetExportStatusAsync response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        var fileStream = await Client.Reports.GetFileOfExportToFileAsync(groupId, reportId, export.Id);
        return new ExportedFile
        {
            FileStream = fileStream,
            FileSuffix = export.ResourceFileExtension,
        };
    }
    return null;
}
public class ExportedFile
{
    public Stream FileStream;
    public string FileSuffix;
}
```

### <a name="end-to-end-example"></a>Voorbeeld van het hele proces

Dit is een end-to-end-voorbeeld van het exporteren van een rapport. Dit voorbeeld bevat de volgende fasen:
1. [De exportaanvraag verzenden](#step-1---sending-an-export-request).
2. [Polling uitvoeren](#step-2---polling).
3. [Het bestand ophalen](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPowerBIReport(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    int pollingtimeOutInMinutes,
    CancellationToken token,
    IList<string> pageNames = null /* Get the page names from the GetPages API */)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId, format, pageNames);
        var export = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
        if (export == null || export.Status != ExportState.Succeeded)
        {
            // Error, failure in exporting the report
            return null;
        }
        return await GetExportedFile(reportId, groupId, export);
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="next-steps"></a>Volgende stappen

Lees hoe u inhoud insluit voor uw klanten en uw organisatie:

> [!div class="nextstepaction"]
>[Gepagineerd rapport exporteren naar een bestand](export-paginated-report.md)

> [!div class="nextstepaction"]
>[Insluiten voor uw klanten](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Insluiten voor uw organisatie](embed-sample-for-your-organization.md)
