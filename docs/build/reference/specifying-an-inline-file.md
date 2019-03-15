---
title: Zadání vloženého souboru
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
ms.openlocfilehash: 7eb123ef3f2115df5c65d266630bded8cb54baae
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823437"
---
# <a name="specifying-an-inline-file"></a>Zadání vloženého souboru

Zadejte dva lomené závorky (<<) v příkazu kde *filename* se zobrazí. Lomené závorky nemůže být rozšíření makra.

## <a name="syntax"></a>Syntaxe

```
<<[filename]
```

## <a name="remarks"></a>Poznámky

Při spuštění příkazu lomené závorky jsou nahrazené *filename*, pokud zadaný, nebo jedinečný název generovaný NMAKE. Je-li zadána, *filename* musí následovat ostrých závorek bez mezera nebo tabulátor. Smí obsahovat cestu. Bez přípony je vyžaduje nebo předpokládá, že. Pokud *filename* není zadán, soubor je vytvořen v aktuální nebo zadaný adresář, přepíše všechny existující soubor s tímto názvem; v opačném případě se vytvoří v adresáři TMP (nebo aktuálního adresáře, pokud TMP proměnné prostředí není definovaný). Pokud předchozí *filename* je znovu použít, NMAKE nahradí předchozí soubor.

## <a name="see-also"></a>Viz také:

[Soubory vložené do souboru pravidel](inline-files-in-a-makefile.md)
