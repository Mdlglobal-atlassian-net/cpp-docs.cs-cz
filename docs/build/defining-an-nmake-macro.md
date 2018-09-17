---
title: Definice makra NMAKE | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c266a0be1c5ff16b719e9055f79b377d13ffbf3c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715703"
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