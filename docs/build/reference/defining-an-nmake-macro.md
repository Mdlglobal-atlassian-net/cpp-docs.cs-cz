---
title: Definice makra NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
ms.openlocfilehash: b163c3dcbfb079a532bd1babca4ee881407bafc1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823439"
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

[Speciální znaky v makrech](special-characters-in-macros.md)

[Hodnota Null a Nedefinovaná makra](null-and-undefined-macros.md)

[Místo definice maker](where-to-define-macros.md)

[Priority v definicích maker](precedence-in-macro-definitions.md)

## <a name="see-also"></a>Viz také:

[Makra a příkaz NMAKE](macros-and-nmake.md)
