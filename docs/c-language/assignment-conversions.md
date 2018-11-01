---
title: Převody přiřazení
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
ms.openlocfilehash: fb3da57af62171ef9670267f94f01ccc097e5942
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649108"
---
# <a name="assignment-conversions"></a>Převody přiřazení

V operacích přiřazení je typ přiřazené hodnoty převeden na typ proměnné, která obdrží přiřazení. Jazyk C umožňuje převod mezi celočíselnými typy a typy s plovoucí desetinnou čárkou i v případě, že je informace při převodu ztracena. Použitá metoda převodu závisí na typech účastnících se přiřazení, jak je popsáno v [obvyklé aritmetické převody](../c-language/usual-arithmetic-conversions.md) a v následujících částech:

- [Převody z integrálních typů se znaménkem](../c-language/conversions-from-signed-integral-types.md)

- [Převody z integrálních typů bez znaménka](../c-language/conversions-from-unsigned-integral-types.md)

- [Převody z typů s plovoucí desetinnou čárkou](../c-language/conversions-from-floating-point-types.md)

- [Převod na a z typů ukazatele](../c-language/conversions-to-and-from-pointer-types.md)

- [Převody z ostatních typů](../c-language/conversions-from-other-types.md)

Kvalifikátory typu sice neovlivňují přípustnost převodu **const** l hodnotu nelze použít na levé straně přiřazení.

## <a name="see-also"></a>Viz také

[Převody typu](../c-language/type-conversions-c.md)