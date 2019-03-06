---
title: Definice makra NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
ms.openlocfilehash: 6eb7c2f7759bda21f1424cef91b1dc814ba8d8ba
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424103"
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

## <a name="see-also"></a>Viz také:

[Makra a příkaz NMAKE](../build/macros-and-nmake.md)
