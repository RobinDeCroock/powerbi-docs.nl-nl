---
title: Richtlijnen voor het gebruik van afbeeldingen voor gepagineerde rapporten
description: Richtlijnen voor het gebruik van afbeeldingen in gepagineerde Power BI-rapporten.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 09fd2197cca31e083c0242b187d7e242244235eb
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77530367"
---
# <a name="image-use-guidance-for-paginated-reports"></a>Richtlijnen voor het gebruik van afbeeldingen voor gepagineerde rapporten

Dit artikel is bedoeld voor u wanneer u als auteur [gepagineerde rapporten](../paginated-reports-report-builder-power-bi.md) in Power BI gaat ontwerpen. Het bevat suggesties voor het werken met afbeeldingen. Doorgaans zijn afbeeldingen in rapportlay-outs grafische weergaven, zoals bedrijfslogo's, of foto's.

Afbeeldingen kunnen op drie verschillende locaties worden opgeslagen:

- In het rapport (ingesloten)
- Op een webserver
- In een database, die kan worden opgehaald met een gegevensset

Ze kunnen vervolgens in uiteenlopende scenario's worden gebruikt in uw rapportlay-outs:

- Vrijstaand logo, of foto
- Foto's die zijn gekoppeld aan rijen gegevens
- Achtergrond voor bepaalde rapportitems:
  - Hoofdtekst
  - Tekstvak
  - Rechthoek
  - Tablix-gegevensgebied (tabel, matrix of lijst)

## <a name="suggestions"></a>Suggesties

Bekijk de volgende suggesties voor professionele rapportlay-outs, onderhoudsgemak en geoptimaliseerde rapportprestaties:

- **Gebruik de kleinst mogelijke grootte**: We raden u aan afbeeldingen voor te bereiden die klein zijn, maar toch scherper en helder zijn. Het gaat om het juiste evenwicht tussen kwaliteit en grootte. U kunt een grafische editor (zoals MS Paint) gebruiken om het afbeeldingsbestand te verkleinen.
- **Vermijd ingesloten afbeeldingen**: Ten eerste kan het rapportbestand aanzienlijk worden vergroot door ingesloten afbeeldingen, wat kan bijdragen aan een tragere rapportweergave. Ten tweede kan het uiterst lastig worden om ingesloten afbeeldingen te onderhouden als u veel rapportafbeeldingen moet bijwerken (zoals wanneer uw bedrijfslogo verandert).
- **Gebruik webserveropslag**: Het opslaan van afbeeldingen op een webserver is een goede optie, met name voor het bedrijfslogo, dat afkomstig kan zijn uit de bedrijfswebsite. Wees echter voorzichtig als uw rapportgebruikers rapporten buiten uw netwerk gaan gebruiken. Zorg er in dit geval voor dat de afbeeldingen beschikbaar zijn via internet.

    Geef uw afbeeldingsbestanden namen wanneer afbeeldingen gerelateerd zijn aan uw gegevens (zoals foto's van uw verkooppersoneel), zodat het pad naar een afbeeldings-URL dynamisch kan worden geproduceerd via een rapportexpressie. Voor de namen van foto's van het verkooppersoneel kunt u bijvoorbeeld de werknemersnummers gebruiken. Als het werknemersnummer wordt opgehaald via de gegevensset van het rapport kunt u een expressie schrijven om het volledige pad naar de afbeeldings-URL te produceren.
- **Gebruik databaseopslag**: Wanneer afbeeldingsgegevens in een relationele database worden opgeslagen, is het zinvol om de afbeeldingsgegevens rechtstreeks uit de databasetabellen te halen, vooral wanneer de afbeeldingen niet zo groot zijn.
- **Geschikte achtergrondafbeeldingen**: Als u besluit om achtergrondafbeeldingen te gebruiken, moet u ervoor zorgen dat de rapportgebruiker niet wordt afgeleid van uw rapportgegevens. 

    Zorg er ook voor dat u _afbeeldingen in watermerkstijl_ gebruikt. Over het algemeen hebben afbeeldingen in watermerkstijl een transparante achtergrond (of dezelfde achtergrondkleur als het rapport). Ze hebben ook fletse kleuren. Gangbare voorbeelden van afbeeldingen in watermerkstijl zijn bedrijfslogo's of gevoeligheidslabels zoals Concept of Vertrouwelijk.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Wat zijn gepagineerde rapporten in Power BI Premium?](../paginated-reports-report-builder-power-bi.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)
