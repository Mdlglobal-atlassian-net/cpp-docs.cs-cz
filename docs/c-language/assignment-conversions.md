---
title: Převody přiřazení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90e77f4bd1eddaa11762b9449a54cb7127498bae
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038177"
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