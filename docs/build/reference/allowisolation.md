---
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 359a68d5ec0a8c7390b5f0343530864e880a057c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493121"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

Určuje chování při vyhledávání manifestu.

## <a name="syntax"></a>Syntaxe

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Poznámky

**/ALLOWISOLATION** způsobí, že operační systém provede vyhledání a načtení manifestu.

Výchozí hodnota je **/ALLOWISOLATION** .

**/ALLOWISOLATION: No** označuje, že spustitelné soubory jsou načteny, jako kdyby neexistoval manifest, a způsobí, že `DllCharacteristics` [nástroje EDITBIN odkaz](editbin-reference.md) nastaví `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit v poli volitelné hlavičky.

Pokud je izolace pro spustitelný soubor zakázaná, zavaděč Windows se nepokusí najít manifest aplikace pro nově vytvořený proces. Nový proces nemá výchozí aktivační kontext, i když je v samotném spustitelném souboru manifest, nebo pokud existuje manifest, který má název *spustitelného souboru-Name*. exe. manifest.

## <a name="see-also"></a>Viz také:

[EDITBIN – možnosti](editbin-options.md)<br/>
[/ALLOWISOLATION (vyhledání manifestu)](allowisolation-manifest-lookup.md)<br/>
[Referenční dokumentace souborů manifestu](/windows/win32/SbsCs/manifest-files-reference)
