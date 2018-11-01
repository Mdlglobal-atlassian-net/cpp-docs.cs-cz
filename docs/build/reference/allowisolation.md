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
ms.openlocfilehash: ab07e3ac3f8c154ffa62a25ab8bad967b255e2e5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604968"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

Určuje chování při vyhledávání manifestu.

## <a name="syntax"></a>Syntaxe

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Poznámky

**/ ALLOWISOLATION** způsobí, že operační systém k vyhledání a načtení manifestu.

**/ ALLOWISOLATION** je výchozí nastavení.

**/ALLOWISOLATION:No** označuje, zda jsou načteny spustitelné soubory, jako by nebyly žádné manifestu a způsobí, že [Editbin – referenční dokumentace](../../build/reference/editbin-reference.md) nastavit `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit ve volitelné hlavičce `DllCharacteristics` pole.

Izolace zakázán pro spustitelný soubor, nebude Windows zavaděče pokuste se najít manifest aplikace pro nově vytvořený procesu. Nový proces nemá výchozí aktivační kontext, i když je manifest ve spustitelném souboru, samotné nebo pokud je manifest, který má název *název spustitelného souboru*. exe.manifest.

## <a name="see-also"></a>Viz také

[EDITBIN – možnosti](../../build/reference/editbin-options.md)<br/>
[/ALLOWISOLATION (vyhledání manifestu)](../../build/reference/allowisolation-manifest-lookup.md)<br/>
[Referenční příručka souborů manifestu](/windows/desktop/SbsCs/manifest-files-reference)