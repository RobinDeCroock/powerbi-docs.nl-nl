---
title: Power BI rapporten-API exporteren
description: Meer informatie over hoe u een ingesloten Power BI-rapport kunt exporteren
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 10/01/2020
ms.openlocfilehash: f997547bb61bf203f7806dbe68d45beb29c6538b
ms.sourcegitcommit: 59d07be9c3e4a2067f6d42c3002a194371bc4341
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "92116449"
---
# <a name="export-power-bi-report-to-file-preview"></a>Power BI-rapport exporteren naar bestand (preview)

Via de API `exportToFile` kunt u een Power BI-rapport exporteren met behulp van een REST-aanroep. De volgende bestandsindelingen worden ondersteund:
* **.pptx** (PowerPoint)
* **.pdf**
* **.png**
    * Wanneer u exporteert naar een PNG-bestand, wordt een rapport met meerdere pagina's gecomprimeerd naar een ZIP-bestand
    * Elk bestand in de ZIP vertegenwoordigt een rapportpagina
    * De paginanamen zijn dezelfde als de retourwaarden van de API voor [pagina’s ophalen](/rest/api/power-bi/reports/getpages) of [pagina’s in groep ophalen](/rest/api/power-bi/reports/getpagesingroup)

## <a name="usage-examples"></a>Gebruiksvoorbeelden

U kunt de exportfunctie op verschillende manieren gebruiken. Hieronder vindt u enkele voorbeelden:

* **Knop Verzenden voor afdrukken**: maak in uw toepassing een knop waarmee een exporttaak wordt geactiveerd wanneer u erop klikt. Met de taak kan het weergegeven rapport worden geëxporteerd als een PDF- of PPTX-bestand. Wanneer dit is voltooid, kan de gebruiker het bestand ontvangen als een download. Met behulp van bladwijzers kunt u het rapport met een specifieke configuratie exporteren, bijvoorbeeld met filters, slicers en aanvullende instellingen. Aangezien de API asynchroon is, kan het enige tijd duren voordat het bestand beschikbaar is.

* **E-mailbijlage**: verzend op gezette tijden een geautomatiseerd e-mailbericht met een bijgevoegd PDF-rapport. Dit scenario kan handig zijn als u het verzenden van een wekelijks rapport naar leidinggevenden wilt automatiseren.

## <a name="using-the-api"></a>De API gebruiken

Voordat u de API gebruikt, moet u controleren of de volgende [beheerdersinstellingen voor de tenant](../../admin/service-admin-portal.md#tenant-settings) zijn ingeschakeld:
* **Rapporten als PowerPoint-presentaties of PDF-documenten exporteren** - Standaard ingeschakeld.
* **Rapporten exporteren als afbeeldingsbestanden**: alleen vereist voor *PNG* en standaard uitgeschakeld.

De API is asynchroon. Wanneer de API [exportToFile](/rest/api/power-bi/reports/exporttofile) is aangeroepen, wordt een exporttaak geactiveerd. Nadat de exporttaak is geactiveerd, gebruikt u [polling](/rest/api/power-bi/reports/getexporttofilestatus) om de taak bij te houden totdat deze is voltooid.

Tijdens de polling retourneert de API een getal dat de hoeveelheid voltooid werk vertegenwoordigt. Het werk in elke exporttaak wordt berekend op basis van het aantal pagina's van het rapport. Alle pagina's hebben hetzelfde gewicht. Als u bijvoorbeeld een rapport met 10 pagina's exporteert en de polling 70 pagina’s retourneert, betekent dit dat met de API zeven van de 10 pagina's in de exporttaak zijn verwerkt.

Wanneer het exporteren is voltooid, retourneert de polling-API-aanroep een [Power BI-URL](/rest/api/power-bi/reports/getfileofexporttofile) om het bestand op te halen. De URL is 24 uur beschikbaar.

## <a name="supported-features"></a>Ondersteunde functies

### <a name="selecting-which-pages-to-print"></a>Selecteren welke pagina's u wilt afdrukken

Geef de pagina’s op die u wilt afdrukken, volgens de retourwaarde voor [pagina’s ophalen](/rest/api/power-bi/reports/getpages) of [pagina’s in groep ophalen](/rest/api/power-bi/reports/getpagesingroup). U kunt ook de volgorde opgeven van de pagina's die u wilt exporteren.

### <a name="bookmarks"></a>Bladwijzers

[Bladwijzers](../../consumer/end-user-bookmarks.md) kunnen worden gebruikt om een rapport op te slaan in een specifieke configuratie, inclusief toegepaste filters en de status van de visuals van het rapport. U kunt de API [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile) gebruiken om de bladwijzer van een rapport op twee manieren programmatisch te exporteren:

* **Een bestaande bladwijzer exporteren**

    Als u een bestaande [rapportbladwijzer wilt exporteren](../../consumer/end-user-bookmarks.md#report-bookmarks), gebruikt u de eigenschap `name`, een unieke (hoofdlettergevoelige) id die u kunt opvragen met behulp van de [JavaScript-API voor bladwijzers](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks).

* **De status van het rapport exporteren**

    Als u de huidige status van het rapport wilt exporteren, gebruikt u de eigenschap `state`. U kunt bijvoorbeeld de methode `bookmarksManager.capture` van de bladwijzer gebruiken om de wijzigingen vast te leggen die een bepaalde gebruiker heeft aangebracht in een rapport, en het rapport vervolgens in de huidige staat exporteren met behulp van `capturedBookmark.state`.

>[!NOTE]
>[Persoonlijke bladwijzers](../../consumer/end-user-bookmarks.md#personal-bookmarks) en [permanente filters](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) worden niet ondersteund.

### <a name="authentication"></a>Verificatie

U kunt verifiëren met behulp van een gebruiker (of hoofdgebruiker) of een [service principal](embed-service-principal.md).

### <a name="row-level-security-rls"></a>RLS (Beveiliging op rijniveau)

Met [RLS (Beveiliging op rijniveau)](embedded-row-level-security.md) kunt u een rapport exporteren waarin gegevens worden weergegeven die alleen zichtbaar zijn voor bepaalde gebruikers. Als u bijvoorbeeld een verkooprapport exporteert dat is gedefinieerd met regionale rollen, kunt u het rapport via een programma filteren, zodat alleen een bepaalde regio wordt weergegeven.

U moet beschikken over de volgende machtigingen om te kunnen exporteren met behulp van RLS:
* Machtigingen voor schrijven en opnieuw delen voor de gegevensset waarmee het rapport is verbonden
* Als het rapport zich in een v1-werkruimte bevindt, moet u de werkruimtebeheerder zijn
* Als het rapport zich in een v2-werkruimte bevindt, moet u lid of beheerder van de werkruimte zijn

### <a name="data-protection"></a>Gegevensbescherming

De PDF- en PPTX-indeling bieden ondersteuning voor [gevoeligheidslabels](../../admin/service-security-sensitivity-label-overview.md). Als u een rapport met een gevoeligheidslabel exporteert naar een PDF- of PPTX-bestand, wordt het rapport in het geëxporteerde bestand weergegeven met het bijbehorende gevoeligheidslabel.

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
* Er kunnen maximaal 50 pagina's worden opgenomen in een geëxporteerd rapport. Als het rapport meer pagina's bevat, retourneert de API een fout en wordt de exporttaak geannuleerd.
* [Persoonlijke bladwijzers](../../consumer/end-user-bookmarks.md#personal-bookmarks) en [permanente filters](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) worden niet ondersteund.
* De hieronder vermelde Power BI-visuals worden niet ondersteund. Wanneer u een rapport exporteert dat deze visuals bevat, worden de gedeelten van het rapport die deze visuals bevatten, niet weergegeven. In plaats hiervan ziet u een foutsymbool.
    * Niet-gecertificeerde visuals in Power BI
    * R-visuals
    * PowerApps
    * Python-visuals
    * Visio

## <a name="code-examples"></a>Codevoorbeelden

Wanneer u een exporttaak maakt, moet u de volgende drie stappen uitvoeren:

1. [Een exportaanvraag verzenden](#step-1---sending-an-export-request).
2. [Polling uitvoeren](#step-2---polling).
3. [Het bestand ophalen](#step-3---getting-the-file).
4. [De bestandsstroom gebruiken](#step-4---using-the-file-stream).

Deze sectie bevat voorbeelden voor elke stap.

### <a name="step-1---sending-an-export-request"></a>Stap 1: een exportaanvraag verzenden

De eerste stap is het verzenden van een exportaanvraag. In dit voorbeeld wordt een exportaanvraag verzonden voor een specifieke pagina.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    IList<string> pageNames = null /* Get the page names from the GetPages REST API */)
{
    var powerBIReportExportConfiguration = new PowerBIReportExportConfiguration
    {
        Settings = new ExportReportSettings
        {
            Locale = "en-us",
        },
        // Note that page names differ from the page display names
        // To get the page names use the GetPages REST API
        Pages = pageNames?.Select(pn => new ExportReportPage(Name = pn)).ToList(),
    };

    var exportRequest = new ExportReportRequest
    {
        Format = format,
        PowerBIReportConfiguration = powerBIReportExportConfiguration,
    };

    // The 'Client' object is an instance of the Power BI .NET SDK
    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>Stap 2: polling uitvoeren

Nadat u een exportaanvraag hebt verzonden, gebruikt u polling om te bepalen wanneer het exportbestand waarop u wacht, gereed is.

```csharp
private async Task<HttpOperationResponse<Export>> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the PostExportRequest response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    HttpOperationResponse<Export> httpMessage = null;
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

        // The 'Client' object is an instance of the Power BI .NET SDK
        httpMessage = await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
        exportStatus = httpMessage.Body;

        // You can track the export progress using the PercentComplete that's part of the response
        SomeTextBox.Text = string.Format("{0} (Percent Complete : {1}%)", exportStatus.Status.ToString(), exportStatus.PercentComplete);
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is not always populated
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;
            await Task.Delay(retryAfterInSec * c_secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return httpMessage;
}
```

### <a name="step-3---getting-the-file"></a>Stap 3: het bestand ophalen

Zodra met polling een URL wordt geretourneerd, gebruikt u dit voorbeeld om het ontvangen bestand op te halen.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the PollExportRequest response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        // The 'Client' object is an instance of the Power BI .NET SDK
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

### <a name="step-4---using-the-file-stream"></a>Stap 4: de bestandsstroom gebruiken

Wanneer u de bestandsstroom hebt, kunt u deze afhandelen op de manier die het beste bij uw behoeften past. U kunt deze bijvoorbeeld per e-mail verzenden of gebruiken om de geëxporteerde rapporten te downloaden.

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
    IList<string> pageNames = null  /* Get the page names from the GetPages REST API */)
{
    const int c_maxNumberOfRetries = 3; /* Can be set to any desired number */
    const int c_secToMillisec = 1000;
    try
    {
        Export export = null;
        int retryAttempt = 1;
        do
        {
            var exportId = await PostExportRequest(reportId, groupId, format, pageNames);
            var httpMessage = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
            export = httpMessage.Body;
            if (export == null)
            {
                // Error, failure in exporting the report
                return null;
            }
            if (export.Status == ExportState.Failed)
            {
                // Some failure cases indicate that the system is currently busy. The entire export operation can be retried after a certain delay
                // In such cases the recommended waiting time before retrying the entire export operation can be found in the RetryAfter header
                var retryAfter = httpMessage.Response.Headers.RetryAfter;
                if(retryAfter == null)
                {
                    // Failed state with no RetryAfter header indicates that the export failed permanently
                    return null;
                }

                var retryAfterInSec = retryAfter.Delta.Value.Seconds;
                await Task.Delay(retryAfterInSec * c_secToMillisec);
            }
        }
        while (export.Status != ExportState.Succeeded && retryAttempt++ < c_maxNumberOfRetries);

        if (export.Status != ExportState.Succeeded)
        {
            // Error, failure in exporting the report
            return null;
        }

        var exportedFile = await GetExportedFile(reportId, groupId, export);

        // Now you have the exported file stream ready to be used according to your specific needs
        // For example, saving the file can be done as follows:
        /*
            var pathOnDisk = @"C:\temp\" + export.ReportName + exportedFile.FileSuffix;

            using (var fileStream = File.Create(pathOnDisk))
            {
                exportedFile.FileStream.CopyTo(fileStream);
            }
        */

        return exportedFile;
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