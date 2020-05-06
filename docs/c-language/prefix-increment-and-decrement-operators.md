---
title: Operátory přírůstku a snížení předpony
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators, types of
- decrement operators, syntax
- decrement operators
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
ms.openlocfilehash: 041c44829b8a267ca053dc85da0333e86db6b7b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325491"
---
# <a name="prefix-increment-and-decrement-operators"></a>Operátory přírůstku a snížení předpony

Unární operátory (`++` a **--**) se nazývají "prefix" nebo "operátory snížení" při zobrazení operátorů přírůstku nebo snížení před operandem. Přírůstek a snížení přípony mají vyšší prioritu než přírůstek a snížení předpony. Operand musí být typu integrální, plovoucí nebo ukazatel a musí být upravitelný výraz l-hodnoty (výraz bez atributu **const** ). Výsledkem je l-hodnota.

Když se operátor objeví před operandem, je operand zvýšen nebo snížen a jeho nová hodnota je výsledkem výrazu.

Operand integrálního nebo plovoucího typu se zvýší nebo sníží o celočíselnou hodnotu 1. Typ výsledku je stejný jako typ operandu. Operand typu ukazatele je zvětšen nebo snížen o velikost objektu, na který odkazuje. Zvýšený ukazatel ukazuje na další objekt; Snížený ukazatel ukazuje na předchozí objekt.

## <a name="example"></a>Příklad

Tento příklad ukazuje operátor odkládání unární předpony:

```
if( line[--i] != '\n' )
    return;
```

V tomto příkladu je proměnná `i` snížena předtím, než je použita jako dolní index. `line`

## <a name="see-also"></a>Viz také

[Unární operátory jazyka C](../c-language/c-unary-operators.md)
