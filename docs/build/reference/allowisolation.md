---
title: -ALLOWISOLATION | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12ee07a0ea6dbe2c3bea21aaa6b394b4c3e6f156
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704083"
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
[/ ALLOWISOLATION (vyhledání manifestu)](../../build/reference/allowisolation-manifest-lookup.md)
[soubory odkaz na Manifest](/windows/desktop/SbsCs/manifest-files-reference)