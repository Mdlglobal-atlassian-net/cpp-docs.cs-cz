---
title: Sčítání (+) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- pointers, adding integers
ms.assetid: b9014fee-825d-46ef-91db-5d46807081fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 62ed952113f3d8b3db46ac735ade4d2e9850dc97
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090851"
---
# <a name="addition-"></a>Sčítání (+)

Operátor sčítání (**+**) způsobí, že mají být přidány dva operandy. Oba operandy mohou být typy s plovoucí desetinnou čárkou nebo celočíselné typy, případně může být jeden operand ukazatel a druhý celé číslo.

Při přidání celého čísla na ukazatel celočíselnou hodnotu (*můžu*) je převeden vynásobením velikostí hodnoty, kterou tento ukazatel odkazuje. Po převodu představuje celočíselná hodnota *můžu* pozice v paměti, kde má každá pozice délku určený typem ukazatele. Když je převedená celočíselná hodnota se přidá k hodnotě ukazatele, výsledkem je nová hodnota ukazatele představující adresu *můžu* pozice z původní adresou. Nová hodnota ukazatele adresuje hodnotu stejného typu jako původní hodnotou ukazatele a proto je stejný jako indexování pole (viz [One-Dimensional pole](../c-language/one-dimensional-arrays.md) a [vícerozměrná pole](../c-language/multidimensional-arrays-c.md)). Pokud součet ukazatel ukazuje mimo pole, s výjimkou první umístění za koncem vysoké, výsledek není definován. Další informace najdete v tématu [aritmetické operace ukazatele](../c-language/pointer-arithmetic.md).

## <a name="see-also"></a>Viz také

[Sčítací operátory jazyka C](../c-language/c-additive-operators.md)