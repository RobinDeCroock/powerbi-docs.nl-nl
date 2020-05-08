---
title: Power BI rapporten-API exporteren
description: Meer informatie over hoe u een ingesloten gepagineerd Power BI-rapport kunt exporteren
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 04/05/2020
ms.openlocfilehash: acb13a70ea4693f447b70aa59da07cd91639de25
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "81268760"
---
# <a name="export-paginated-report-to-file-preview"></a>Gepagineerd rapport exporteren naar een bestand (preview)

Via de API `exportToFile` kunt u een gepagineerd Power BI-rapport exporteren met behulp van een REST-aanroep. De volgende bestandsindelingen worden ondersteund:
* **.pptx** (PowerPoint)
* **.pdf**
* **.xlsx** (Excel)
* **.docx** (Word)
* **.csv**
* **.xml**
* **.mhtml**
* **Afbeelding**
    * Bij het exporteren naar een afbeelding stelt u de afbeeldingsindeling in via de indelingsinstelling `OutputFormat`
    * De ondersteunde OutputFormat-waarden zijn: .bmp, .emf, .gif, .jpeg, .png en .tiff (standaard)

## <a name="usage-examples"></a>Gebruiksvoorbeelden

U kunt de exportfunctie op verschillende manieren gebruiken. Hieronder vindt u enkele voorbeelden:

* **Knop Verzenden voor afdrukken**: maak in uw toepassing een knop waarmee een exporttaak wordt geactiveerd wanneer u erop klikt. Met de taak kan het weergegeven rapport worden geëxporteerd als een .pdf of .pptx. Wanneer dit is voltooid, kan de gebruiker het bestand ontvangen als een download. Met rapportparameters en indelingsinstellingen kunt u het rapport in een specifieke staat exporteren, inclusief gefilterde gegevens, aangepaste paginaformaten en andere indelingsspecifieke instellingen. Aangezien de API asynchroon is, kan het enige tijd duren voordat het bestand beschikbaar is.

* **E-mailbijlage**: verzend op gezette tijden een geautomatiseerd e-mailbericht met een bijgevoegd PDF-rapport. Dit scenario kan handig zijn als u het verzenden van een wekelijks rapport naar leidinggevenden wilt automatiseren.

## <a name="using-the-api"></a>De API gebruiken

De API is asynchroon. Wanneer de API [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile) is aangeroepen, wordt een exporttaak geactiveerd. Nadat de exporttaak is geactiveerd, gebruikt u [polling](https://docs.microsoft.com/rest/api/power-bi/reports/getexporttofilestatus) om de taak bij te houden totdat deze is voltooid.

Wanneer het exporteren is voltooid, retourneert de polling-API-aanroep een [Power BI-URL](https://docs.microsoft.com/rest/api/power-bi/reports/getfileofexporttofile) om het bestand op te halen. De URL is 24 uur beschikbaar.

## <a name="supported-features"></a>Ondersteunde functies

### <a name="format-settings"></a>Instellingen voor indeling

Geef een verscheidenheid aan indelingsinstellingen op voor elke bestandsindeling. De ondersteunde eigenschappen en waarden zijn gelijk aan [Parameters voor apparaatinfo](../../paginated-reports/report-builder-url-parameters.md#report-commands-rdl) voor URL-parameters voor gepagineerde rapporten.

Hier volgen twee voorbeelden: een voor het exporteren van de eerste vier pagina's van een rapport met behulp van de rapportpaginagrootte naar een PPTX-bestand en een ander voor het exporteren van de derde pagina van een rapport naar een JPEG-bestand.

**De eerste vier pagina's naar een .pptx exporteren**

```json
{
      "format": "PPTX",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "UseReportPageSize": "true",
                  "StartPage": "1",
                  "EndPage": "4"
            }
      }
}
```

**De derde pagina naar een .jpeg exporteren**

```json
{
      "format": "IMAGE",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "OutputFormat": "JPEG",
                  "StartPage": "3",
                  "EndPage": "3"
            }
      }
}
```

### <a name="report-parameters"></a>Rapportparameters

U kunt de API `exportToFile` gebruiken om een rapport programmatisch te exporteren met een set rapportparameters. Dit wordt gedaan met behulp van mogelijkheden van [rapportparameters](../../paginated-reports/paginated-reports-parameters.md).

Hier volgt een voorbeeld van het instellen van rapportparameterwaarden.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "parameterValues":[
                  {"name": "State", "value": "WA"},
                  {"name": "City", "value": "Seattle"},
                  {"name": "City", "value": "Bellevue"},
                  {"name": "City", "value": "Redmond"}
            ]
      }
}
```

### <a name="authentication"></a>Authentication

U kunt verifiëren met behulp van een gebruiker (of hoofdgebruiker) of een [service principal](embed-service-principal.md).

### <a name="row-level-security-rls"></a>RLS (Beveiliging op rijniveau)

Wanneer u een Power BI-gegevensset gebruikt waarvoor beveiliging op rijniveau (RLS) is gedefinieerd als gegevensbron, kunt u een rapport exporteren met gegevens die alleen zichtbaar zijn voor bepaalde gebruikers. Als u bijvoorbeeld een verkooprapport exporteert dat is gedefinieerd met regionale rollen, kunt u het rapport via een programma filteren, zodat alleen een bepaalde regio wordt weergegeven.

Als u wilt exporteren met behulp van RLS moet u leesmachtigingen hebben voor de Power BI-gegevensset die wordt gebruikt als gegevensbron voor het rapport.

Hier volgt een voorbeeld van het verstrekken van een efficiënte gebruikersnaam voor RLS.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "identities": [
                  {"username": "john@contoso.com"}            
            ]
      }
}
```

## <a name="code-examples"></a>Codevoorbeelden

De API-SDK van Power BI die in de codevoorbeelden wordt gebruikt, kunt u [hier](https://www.nuget.org/packages/Microsoft.PowerBI.Api) downloaden.

Wanneer u een exporttaak maakt, moet u de volgende drie stappen uitvoeren:

1. Een exportaanvraag verzenden.
2. Polling uitvoeren.
3. Het bestand ophalen.

Deze sectie bevat voorbeelden voor elke stap.

### <a name="step-1---sending-an-export-request"></a>Stap 1: een exportaanvraag verzenden

De eerste stap is het verzenden van een exportaanvraag. In dit voorbeeld wordt een exportaanvraag verzonden voor een specifiek paginabereik, een specifieke omvang en specifieke rapportparameterwaarden.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId)
{
    // For documentation purposes the export configuration is created in this method
    // Ordinarily, it would be created outside and passed in
    var paginatedReportExportConfiguration = new PaginatedReportExportConfiguration()
    {
        FormatSettings = new Dictionary<string, string>()
        {
            {"PageHeight", "14in"},
            {"PageWidth", "8.5in" },
            {"StartPage", "1"},
            {"EndPage", "4"}
        },
        ParameterValues = new List<ParameterValue>()
        {
            { new ParameterValue() {Name = "State", Value = "WA"} },
            { new ParameterValue() {Name = "City", Value = "Redmond"} }
        }
    };

    var exportRequest = new ExportReportRequest
    {
        Format = FileFormat.PDF,
        PaginatedReportExportConfiguration = paginatedReportExportConfiguration,
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
    const int secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations
            return null;
        }

        var httpMessage = 
            await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
            
        exportStatus = httpMessage.Body;
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;

            await Task.Delay(retryAfterInSec * secToMillisec);
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
        var httpMessage = 
            await Client.Reports.GetFileOfExportToFileInGroupWithHttpMessagesAsync(groupId, reportId, export.Id);

        return new ExportedFile
        {
            FileStream = httpMessage.Body,
            ReportName = export.ReportName,
            FileExtension = export.ResourceFileExtension,
        };
    }

    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string ReportName;
    public string FileExtension;
}
```

### <a name="end-to-end-example"></a>Voorbeeld van het hele proces

Dit is een end-to-end-voorbeeld van het exporteren van een rapport. Dit voorbeeld bevat de volgende fasen:
1. [De exportaanvraag verzenden](#step-1---sending-an-export-request).
2. [Polling uitvoeren](#step-2---polling).
3. [Het bestand ophalen](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPaginatedReport(
    Guid reportId,
    Guid groupId,
    int pollingtimeOutInMinutes,
    CancellationToken token)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId);

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
>[Rapport exporteren naar bestand](export-to.md)

> [!div class="nextstepaction"]
>[Insluiten voor uw klanten](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Insluiten voor uw organisatie](embed-sample-for-your-organization.md)