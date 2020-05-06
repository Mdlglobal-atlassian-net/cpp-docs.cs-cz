---
title: Převody přiřazení
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
ms.openlocfilehash: f118c4a7fee493793b1410cb26f6a0af571c5fcc
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998707"
---
# <a name="assignment-conversions"></a>Převody přiřazení

V operacích přiřazení je typ přiřazené hodnoty převeden na typ proměnné, která obdrží přiřazení. Jazyk C umožňuje převod mezi celočíselnými typy a typy s plovoucí desetinnou čárkou i v případě, že je informace při převodu ztracena. Použitá metoda převodu závisí na typech zahrnutých v přiřazení, jak je popsáno v tématu [obvyklé aritmetické převody](../c-language/usual-arithmetic-conversions.md) a v následujících částech:

- [Převody z integrálních typů se znaménkem](../c-language/conversions-from-signed-integral-types.md)

- [Převody z celočíselných typů bez znaménka](../c-language/conversions-from-unsigned-integral-types.md)

- [Převody z typů s plovoucí desetinnou čárkou](../c-language/conversions-from-floating-point-types.md)

- [Převody na typy ukazatelů a z nich](../c-language/conversions-to-and-from-pointer-types.md)

- [Převody z jiných typů](../c-language/conversions-from-other-types.md)

Kvalifikátory typu neovlivňují možnost Povolit převod, i když na levé straně přiřazení nelze použít **konstantní** l-value.

## <a name="see-also"></a>Viz také

[Převody typu](../c-language/type-conversions-c.md)
