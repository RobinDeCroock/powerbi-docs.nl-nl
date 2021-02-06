---
title: Informatie over ondersteunde Python-pakketten
description: Python-pakketten die wel en niet worden ondersteund in Power BI
author: otarb
ms.author: otarb
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 06/26/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: d3a30098b793ccb75cbae6c271ab1685b3176a10
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/06/2021
ms.locfileid: "99616945"
---
# <a name="create-visuals-by-using-python-packages-in-the-power-bi-service"></a>Visuals maken met Python-pakketten in de Power BI-service
U kunt de krachtige [programmeertaal Python](https://www.python.org/) gebruiken om visuals te maken in Power BI-service. Er worden veel Python-pakketten ondersteund in de Power BI-service en dit worden er steeds meer.

De volgende secties bevatten een alfabetische lijst met de Python-pakketten die worden ondersteund in Power BI. 

## <a name="request-support-for-a-new-python-package"></a>Ondersteuning aanvragen voor een nieuw Python-pakket
Ondersteunde Python-pakketten voor de **Power BI-service** vindt u in de volgende sectie, met de naam **Ondersteunde pakketten**. Als u ondersteuning wilt aanvragen voor een Python-pakket dat niet in de lijst staat, dient u een aanvraag in op [Power BI Ideas](https://ideas.powerbi.com).

## <a name="requirements-and-limitations-of-python-packages"></a>Vereisten en beperkingen van Python-pakketten
Er zijn een paar vereisten en beperkingen voor Python-pakketten:

* Huidige Python-runtime: Python 3.7.7.
* De Power BI-service ondersteunt vrij wel alle Python-pakketten met gratis en open source-softwarelicenties zoals GPL-2, GPL 3, MIT +, enzovoort.
* De Power BI-service ondersteunt pakketten die zijn gepubliceerd in PyPI. De service biedt geen ondersteuning voor persoonlijke of aangepaste Python-pakketten. Gebruikers worden geadviseerd om hun persoonlijke pakketten beschikbaar te maken op PyPI en dan pas een aanvraag te versturen om het pakket beschikbaar te maken in de Power BI-service.
* Voor Python-visuals in **Power BI Desktop** kunt u elk pakket installeren, met inbegrip van aangepaste Python-pakketten.
* Uit veiligheids- en privacyoverwegingen worden Python-pakketten die client-serverquery's via het World Wide Web als service aanbieden niet ondersteund. De netwerktoegang wordt geblokkeerd voor deze pogingen.
* Het goedkeuringsproces voor het toevoegen van een nieuw Python-pakket heeft een structuur van afhankelijkheden. Enkele afhankelijkheden die moeten worden geïnstalleerd in de service, kunnen niet worden ondersteund.

## <a name="python-packages-that-are-supported-in-power-bi"></a>Python-pakketten die worden ondersteund in Power BI
In de volgende tabel ziet u welke pakketten **worden ondersteund** in de Power BI-service.


|        Pakket        |   Versie   |                                   Koppeling                                   |
|-----------------------|-------------|--------------------------------------------------------------------------|
|matplotlib|3.2.1|https://pypi.org/project/matplotlib|
|numpy|1.18.4|https://pypi.org/project/numpy|
|pandas|1.0.1|https://pypi.org/project/pandas|
|scikit-learn|0.23.0|https://pypi.org/project/scikit-learn|
|scipy|1.4.1|https://pypi.org/project/scipy|
|seaborn|0.10.1|https://pypi.org/project/seaborn|
|statsmodels|0.11.1|https://pypi.org/project/statsmodels|
|xgboost|1.1.0|https://pypi.org/project/xgboost|

## <a name="next-steps"></a>Volgende stappen
Raadpleeg de volgende artikelen voor meer informatie over Python in Power BI:

* [Power BI-visuals maken met Python](desktop-python-visuals.md)
* [Python-scripts uitvoeren in Power BI Desktop](desktop-python-scripts.md)
* [Python gebruiken in Query-editor van Power BI](desktop-python-in-query-editor.md)
