---
title: Zadání vloženého souboru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73983094f10088920100b4fbbb8d870aee13f05e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720561"
---
# <a name="specifying-an-inline-file"></a>Zadání vloženého souboru

Zadejte dva lomené závorky (<<) v příkazu kde *filename* se zobrazí. Lomené závorky nemůže být rozšíření makra.

## <a name="syntax"></a>Syntaxe

```
<<[filename]
```

## <a name="remarks"></a>Poznámky

Při spuštění příkazu lomené závorky jsou nahrazené *filename*, pokud zadaný, nebo jedinečný název generovaný NMAKE. Je-li zadána, *filename* musí následovat ostrých závorek bez mezera nebo tabulátor. Smí obsahovat cestu. Bez přípony je vyžaduje nebo předpokládá, že. Pokud *filename* není zadán, soubor je vytvořen v aktuální nebo zadaný adresář, přepíše všechny existující soubor s tímto názvem; v opačném případě se vytvoří v adresáři TMP (nebo aktuálního adresáře, pokud TMP proměnné prostředí není definovaný). Pokud předchozí *filename* je znovu použít, NMAKE nahradí předchozí soubor.

## <a name="see-also"></a>Viz také

[Soubory vložené do souboru pravidel](../build/inline-files-in-a-makefile.md)