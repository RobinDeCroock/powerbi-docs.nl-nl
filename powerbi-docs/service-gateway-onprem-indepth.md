---
title: On-premises gegevensgateway nader bekeken
description: In dit artikel wordt de on-premises gateway uitvoerig besproken. Er wordt gekeken hoe de service samenwerkt met Azure Active Directory en uw lokale Active Directory in combinatie met Analysis Services
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: fa7d10403ca6bd8dc94729b7b4fd631475a3671e
ms.sourcegitcommit: 20ae9e9ffab6328f575833be691073de2061a64d
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58383411"
---
# <a name="on-premises-data-gateway-in-depth"></a>On-premises gegevensgateway nader bekeken
Het is mogelijk dat gebruikers in uw organisatie toegang hebben tot on-premises gegevens (waarvoor ze al zijn geautoriseerd), maar voordat deze gebruikers verbinding kunnen maken met uw on-premises gegevensbron, moet er een on-premises gegevensgateway worden geïnstalleerd en geconfigureerd. De gateway zorgt ervoor dat er op een snelle, veilige en transparante manier kan worden gecommuniceerd tussen een gebruiker in de cloud en de on-premises gegevensbron.

De installatie en configuratie van een gateway wordt meestal uitgevoerd door een beheerder. Hiervoor kan speciale kennis nodig zijn van uw on-premises servers en in sommige gevallen zijn ook machtigingen van een serverbeheerder vereist.

In dit artikel worden geen stapsgewijze instructies gegeven voor het installeren en configureren van de gateway. Uitgebreide instructies vindt u in [On-premises gegevensgateway](service-gateway-onprem.md). Dit artikel is bedoeld om uitgebreid in te gaan op de werking van de gateway. We besteden ook kort aandacht aan gebruikersnamen en beveiliging in zowel Azure Active Directory als Analysis Services. Daarnaast bespreken we hoe de cloudservices veilig verbinding maken met on-premises gegevens en deze bevragen door gebruik te maken van het e-mailadres waarmee gebruikers zich aanmelden, de gateway en Active Directory.

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-how-it-works-include.md)]

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="sign-in-account"></a>Aanmeldingsaccount
Gebruikers melden zich aan met een werk- of schoolaccount. Dit is uw organisatieaccount. Als u zich hebt geregistreerd voor een Office 365-aanbieding en niet het echte e-mailadres van uw werk hebt opgegeven, kan dit eruit zien als nancy@contoso.onmicrosoft.com. Uw account wordt binnen een cloudservice opgeslagen in een tenant van Azure Active Directory (AAD). In de meeste gevallen komt de UPN van uw AAD-account overeen met het e-mailadres.

## <a name="authentication-to-on-premises-data-sources"></a>Verificatie voor on-premises gegevensbronnen
Er worden opgeslagen referenties gebruikt voor verbinding met on-premises gegevensbronnen vanuit de gateway met uitzondering van Analysis Services. Ongeacht de individuele gebruiker, worden de opgeslagen referenties gebruikt om verbinding te maken.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Verificatie voor een live-gegevensbron van Analysis Services
Telkens wanneer een gebruiker interactie heeft met Analysis Services, wordt de effectieve gebruikersnaam doorgegeven aan de gateway en vervolgens aan de on-premises Analysis Services-server. De UPN (User Principal Name), meestal het e-mailadres waarmee u zich bij de cloud aanmeldt, is de informatie die als de effectieve gebruikersnaam wordt doorgegeven aan Analysis Services. De UPN wordt doorgegeven via de verbindingseigenschap EffectiveUserName. Dit e-mailadres moet overeenkomen met een UPN die is gedefinieerde in het lokale Active Directory-domein. De UPN is een eigenschap van een Active Directory-account. Dat Windows-account moet aanwezig zijn in een Analysis Services-rol om toegang te hebben tot de server. De aanmelding kan niet tot stand worden gebracht als er geen overeenkomst wordt gevonden in Active Directory.

Analysis Services kan ook filtering aanbieden op basis van dit account. Deze filtering kan plaatsvinden met behulp van op rollen gebaseerde beveiliging of beveiliging op rijniveau.

## <a name="role-based-security"></a>Beveiliging op basis van rollen
Modellen bieden beveiliging op basis van gebruikersrollen. Rollen worden gedefinieerd voor een bepaald modelproject tijdens het ontwerpen van het project in SQL Server Data Tools – Business Intelligence (BI-SSDT). Dit kan trouwens ook nadat een model is geïmplementeerd, in dat geval met behulp van SQL Server Management Studio (SSMS). Rollen bevatten leden op Windows-gebruikersnaam of Windows-groep. Rollen bepalen welke machtigingen een gebruiker heeft om query's of acties uit te voeren op het model. De meeste gebruikers behoren tot een rol met leesmachtigingen. Andere rollen zijn bedoeld voor beheerders met machtigingen voor het verwerken van items, en voor het beheren van databasefuncties en andere rollen.

## <a name="row-level-security"></a>Beveiliging op rijniveau
Beveiliging op rijniveau is specifiek voor beveiliging op rijniveau van Analysis Services. Modellen kunnen dynamische beveiliging op rijniveau bieden. In tegenstelling tot de aanpak waarbij gebruikers ten minste één rol moeten hebben, is dynamische beveiliging niet vereist voor een tabellair model. In algemene zin bepaalt dynamische beveiliging de leestoegang van een gebruiker voor gegevens, gespecificeerd tot een bepaalde rij in een bepaalde tabel. Net als bij rollen, is voor dynamische beveiliging op rijniveau de Windows-gebruikersnaam van een gebruiker nodig.

De mogelijkheid van gebruikers om modelgegevens op te vragen en weer te geven, wordt in eerste instantie bepaald door de rollen die zijn toegewezen aan hun Windows-gebruikersaccount. Als bovendien dynamische beveiliging op rijniveau is geconfigureerd, wordt hier in tweede instantie rekening mee gehouden.

De implementatie van op rollen gebaseerde beveiliging en dynamische beveiliging op rijniveau valt buiten het bereik van dit artikel.  U kunt op MSDN meer informatie (Engelstalig) vinden over [rollen (SSAS Tabular)](https://msdn.microsoft.com/library/hh213165.aspx) en [beveiligingsrollen (Analysis Services - Multidimensional Data)](https://msdn.microsoft.com/library/ms174840.aspx). Voor het meest uitgebreide overzicht van beveiliging met tabellaire modellen kunt u het technische artikel [Securing the Tabular BI Semantic Model](https://msdn.microsoft.com/library/jj127437.aspx) downloaden en lezen.

## <a name="what-about-azure-active-directory"></a>De rol van Azure Active Directory
Microsoft-cloudservices maken gebruik van [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) voor de verificatie van gebruikers. Azure Active Directory is de tenant met gebruikersnamen en beveiligingsgroepen. Het e-mailadres waarmee een gebruiker zich aanmeldt, is meestal hetzelfde als de UPN van het account.

Wat is de functie van mijn lokale Active Directory?

Analysis Services moet bepalen of een gebruiker die verbinding maakt met de service behoort tot een rol met machtigingen voor het lezen van gegevens. Hiervoor moet de server de effectieve gebruikersnaam converteren die door AAD wordt doorgegeven aan de gateway en vervolgens aan de Analysis Services-server. De Analysis Services-server geeft de effectieve gebruikersnaam door aan een Windows Active Directory-domeincontroller (DC). De Active Directory-domeincontroller controleert vervolgens of de effectieve gebruikersnaam een geldige UPN is, voor een lokaal account, en stuurt de Windows-gebruikersnaam van die gebruiker vervolgens terug naar de Analysis Services-server.

EffectiveUserName kan alleen worden gebruikt met een Analysis Services-server die aan een domein is gekoppeld. De Analysis Services-server moet deel uitmaken van een domein om aanmeldingsfouten te voorkomen.

## <a name="how-do-i-tell-what-my-upn-is"></a>Hoe weet ik wat mijn UPN is?
U weet mogelijk niet wat uw UPN is en u bent mogelijk geen domeinbeheerder. Gebruik de volgende vanaf uw werkstation om de UPN voor uw account op te vragen.

    whoami /upn

Het resultaat ziet eruit als een e-mailadres, maar dit is de UPN voor uw lokale domeinaccount. Als u een gegevensbron van Analysis Services gebruikt voor live-verbindingen, moet het resultaat overeenkomen met wat is doorgegeven aan EffectiveUserName vanuit de gateway.

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Gebruikersnamen toewijzen voor gegevensbronnen van Analysis Services
In Power BI kunt u gebruikersnamen toewijzen voor gegevensbronnen van Analysis Services. U kunt regels configureren om een gebruikersnaam die is aangemeld met Power BI toe te wijzen aan een naam die wordt doorgegeven voor EffectiveUserName tijdens de Analysis Services-verbinding. De functie voor het toewijzen van gebruikersnamen is een uitstekende oplossing voor het geval dat uw gebruikersnaam in AAD niet overeenkomt met een UPN in uw lokale Active Directory. Als uw e-mailadres bijvoorbeeld nancy@contoso.onmicrsoft.com is, kunt u dit adres toewijzen aan nancy@contoso.com, en dan wordt die waarde doorgegeven aan de gateway. U kunt hier meer lezen over het [toewijzen van gebruikersnamen](service-gateway-enterprise-manage-ssas.md#map-user-names).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Een on-premises Active Directory synchroniseren met Azure Active Directory
Het is handig als uw lokale Active Directory-accounts overeenkomen met Azure Active Directory als u gebruik gaat maken van live-verbindingen van Analysis Services. De UPN moet namelijk overeenkomen tussen de accounts.

De cloudservices kennen alleen accounts binnen Azure Active Directory. Het maakt niet uit of u een account hebt toegevoegd in uw lokale Active Directory. Als het account niet in AAD bestaat, kan het niet worden gebruikt. Er zijn verschillende manieren waarop u uw lokale Active Directory-accounts in overeenstemming kunt brengen met Azure Active Directory.

1. U kunt accounts handmatig toevoegen aan Azure Active Directory.
   
   U kunt een account maken in Azure Portal of in het Microsoft 365-beheercentrum. De accountnaam komt dan overeen met de UPN van het lokale Active Directory-account.
2. U kunt het hulpprogramma [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis) gebruiken om lokale accounts te synchroniseren met uw Azure Active Directory-tenant.
   
   Het hulpprogramma Azure AD Connect biedt opties voor adreslijstsynchronisatie en het instellen van verificatie, met inbegrip van wachtwoordhashsynchronisatie, pass-through-verificatie en federatie. Als u geen tenantbeheerder of lokale domeinbeheerder bent, moet u contact opnemen met uw IT-beheerder om dit in orde te laten maken.

Door gebruik te maken van Azure AD Connect weet u zeker dat de UPN overeenkomt tussen AAD en uw lokale Active Directory.

> [!NOTE]
> Het synchroniseren van accounts met het hulpprogramma Azure AD Connect betekent dat er nieuwe accounts worden gemaakt binnen uw AAD-tenant.
> 
> 

## <a name="now-this-is-where-the-gateway-comes-in"></a>De rol van de gateway
De gateway fungeert als een brug tussen de cloud en uw on-premises server. Gegevensoverdracht tussen de cloud en de gateway wordt beveiligd via [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview). De Service Bus maakt via een uitgaande verbinding op de gateway een beveiligd kanaal tussen de cloud en uw on-premises server.  Er zijn geen binnenkomende verbindingen die u moet openen op de on-premises firewall. Power BI beheert de Service Bus voor u, zodat er geen extra kosten of configuratiestappen vereist zijn.

Als u een gegevensbron van Analysis Services hebt, moet u de gateway installeren op een computer die lid is van hetzelfde forest/domein als de Analysis Services-server.

Hoe dichter de gateway zich bij de server bevindt, des te sneller de verbinding. Als u de gateway op dezelfde server als de gegevensbron kunt configureren, is dat de beste oplossing om netwerklatentie tussen de gateway en de server te voorkomen.

## <a name="what-to-do-next"></a>Volgende stap
Nadat de gateway is geïnstalleerd, kunt u de gegevensbronnen voor de gateway gaan maken. U kunt gegevensbronnen toevoegen via het scherm **Gateways beheren**. Zie voor meer informatie deze artikelen over het beheren van gegevensbronnen:

[Manage your data source - Analysis Services](service-gateway-enterprise-manage-ssas.md) (Gegevensbron beheren - Analysis Services)  
[Manage your data source - SAP HANA](service-gateway-enterprise-manage-sap.md) (Uw gegevensbron beheren - SAP HANA)  
[Manage your data source - SQL Server](service-gateway-enterprise-manage-sql.md) (Gegevensbron beheren - SQL Server)  
[Manage your data source - Oracle](service-gateway-onprem-manage-oracle.md) (Gegevensbron beheren - Oracle)  
[Manage your data source - Import/Scheduled refresh](service-gateway-enterprise-manage-scheduled-refresh.md) (Gegevensbron beheren - importeren/geplande vernieuwing)  

## <a name="where-things-can-go-wrong"></a>Aandachtspunten
Soms gaat er iets mis tijdens het installeren van de gateway. Of lijkt het dat de installatie goed is verlopen, maar kan de service nog steeds niet samenwerken met de gateway. In veel gevallen is het probleem heel eenvoudig op te lossen, bijvoorbeeld door het wachtwoord aan te passen dat door de gateway wordt gebruikt voor aanmelding bij de gegevensbron.

Soms wordt het probleem veroorzaakt door het type e-mailadres waarmee gebruikers zich aanmelden of doordat Analysis Services geen effectieve gebruikersnaam kan produceren. Als er meerdere domeinen met vertrouwensrelaties zijn en uw gateway zich in het ene domein bevindt en Analysis Services in een ander, kan dit soms problemen geven.

In plaats van hier procedures te geven voor het oplossen van dergelijke problemen, hebben we de verschillende stappen voor probleemoplossing verzameld in het artikel [Problemen met de on-premises gegevensgateway oplossen](service-gateway-onprem-tshoot.md). Maar we gaan er natuurlijk vanuit dat alles zonder problemen verloopt. Als er toch onverhoopt problemen zijn, zullen dit achtergrondartikel en het artikel over probleemoplossing zeker van pas komen.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

## <a name="next-steps"></a>Volgende stappen

[Problemen met de on-premises gegevensgateway oplossen](service-gateway-onprem-tshoot.md)  
[Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview/)  
[Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis/)  

Nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

