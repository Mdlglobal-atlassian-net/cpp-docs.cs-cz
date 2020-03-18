---
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION_EDITBIN
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 3dae8ee83e25492fab0ba2c6a55681728d5f3453
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440368"
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

**/ALLOWISOLATION: No** znamená, že spustitelné soubory jsou načteny, jako kdyby neexistoval manifest, a způsobí, že [nástroje EDITBIN odkaz](editbin-reference.md) nastaví bit `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` v poli `DllCharacteristics` volitelného záhlaví.

Pokud je izolace pro spustitelný soubor zakázaná, zavaděč Windows se nepokusí najít manifest aplikace pro nově vytvořený proces. Nový proces nemá výchozí aktivační kontext, i když je v samotném spustitelném souboru manifest, nebo pokud existuje manifest, který má název *spustitelného souboru-Name*. exe. manifest.

## <a name="see-also"></a>Viz také

[EDITBIN – možnosti](editbin-options.md)<br/>
[/ALLOWISOLATION (vyhledání manifestu)](allowisolation-manifest-lookup.md)<br/>
[Referenční dokumentace souborů manifestu](/windows/win32/SbsCs/manifest-files-reference)
