---
title: Definice makra NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
ms.openlocfilehash: 860a5766e0d766f7426cb6c1a7eaf5db02686aa4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498982"
---
# <a name="defining-an-nmake-macro"></a>Definice makra NMAKE

## <a name="syntax"></a>Syntaxe

```

macroname=string
```

## <a name="remarks"></a>Poznámky

*Makro* je kombinací písmena, číslice a podtržítka (_), maximálně 1 024 znaků a je případ citlivé. *Makro* může obsahovat vyvolaný – makro. Pokud *makro* se skládá zcela vyvolaný – makro, makro vyvolání nemůže být null nebo není definovaný.

`string` Může být libovolná sekvence nula nebo více znaků. Řetězec s hodnotou null obsahuje nulové znaky nebo pouze mezery nebo tabulátory. `string` Může obsahovat volání makra.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

[Speciální znaky v makrech](../build/special-characters-in-macros.md)

[Hodnota Null a Nedefinovaná makra](../build/null-and-undefined-macros.md)

[Místo definice maker](../build/where-to-define-macros.md)

[Priority v definicích maker](../build/precedence-in-macro-definitions.md)

## <a name="see-also"></a>Viz také

[Makra a příkaz NMAKE](../build/macros-and-nmake.md)