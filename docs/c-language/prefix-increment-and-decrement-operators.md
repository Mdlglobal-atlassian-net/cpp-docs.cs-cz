---
title: Operátory přírůstku a snížení předpony | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- increment operators, types of
- decrement operators, syntax
- decrement operators
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7077e1b40701f8586ce8322ac9922517ac77b22b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018285"
---
# <a name="prefix-increment-and-decrement-operators"></a>Operátory přírůstku a snížení předpony

Unární operátory (`++` a **--**) se nazývají "předponu" Inkrementace nebo dekrementace operátory, když se objeví před operand operátorů zvýšení nebo snížení. Přípona Inkrementace a dekrementace má vyšší prioritu než předpony Inkrementace a dekrementace. Operand musí mít typ integral, plovoucí nebo ukazatel a musí být výraz upravitelná l hodnota (výraz bez **const** atributu). Výsledkem je l hodnotou.

Pokud se operátor vyskytuje před jeho operandu, operand je zvýšena nebo snížena a její nová hodnota je výsledek výrazu.

Typ s plovoucí desetinnou čárkou nebo celočíselné operandy je zvýšena nebo snížena celočíselnou hodnotu 1. Typ výsledku je stejný jako typ operandu. Operand typu ukazatel, je zvýšena nebo snížena velikost objektu, který se zaměřuje. Zvýšena ukazatel odkazuje na další objekt. snížen ukazatel odkazuje na předchozí objekt.

## <a name="example"></a>Příklad

Tento příklad ukazuje unární operátor dekrementace předpony:

```
if( line[--i] != '\n' )
    return;
```

V tomto příkladu je proměnná `i` je snížen, než bude použit jako index do `line`.

## <a name="see-also"></a>Viz také

[Unární operátory jazyka C](../c-language/c-unary-operators.md)