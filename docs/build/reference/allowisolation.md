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
ms.openlocfilehash: 02012e7561fe8462f5f25ae13d961c35561666ec
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819669"
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

**/ALLOWISOLATION:No** označuje, zda jsou načteny spustitelné soubory, jako by nebyly žádné manifestu a způsobí, že [Editbin – referenční dokumentace](editbin-reference.md) nastavit `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit ve volitelné hlavičce `DllCharacteristics` pole.

Izolace zakázán pro spustitelný soubor, nebude Windows zavaděče pokuste se najít manifest aplikace pro nově vytvořený procesu. Nový proces nemá výchozí aktivační kontext, i když je manifest ve spustitelném souboru, samotné nebo pokud je manifest, který má název *název spustitelného souboru*. exe.manifest.

## <a name="see-also"></a>Viz také:

[EDITBIN – možnosti](editbin-options.md)<br/>
[/ALLOWISOLATION (vyhledání manifestu)](allowisolation-manifest-lookup.md)<br/>
[Referenční příručka souborů manifestu](/windows/desktop/SbsCs/manifest-files-reference)
