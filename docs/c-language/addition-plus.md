---
title: Sčítání (+)
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, adding integers
ms.assetid: b9014fee-825d-46ef-91db-5d46807081fc
ms.openlocfilehash: 48672315960e32cb324aacc6c90d3d67891f3d39
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313659"
---
# <a name="addition-"></a>Sčítání (+)

Operátor sčítání (**+**) způsobí, že se přidají dva operandy. Oba operandy mohou být typy s plovoucí desetinnou čárkou nebo celočíselné typy, případně může být jeden operand ukazatel a druhý celé číslo.

Když je celé číslo přidáno k ukazateli, je celočíselná hodnota (*i*) převedena vynásobením její velikosti hodnotou ukazatele. Po převodu celočíselná *hodnota představuje pozici* v paměti, kde každá pozice má délku určenou typem ukazatele. Když je do hodnoty ukazatele přidána převedená celočíselná hodnota, výsledkem je nová hodnota ukazatele představující adresu *i* pozice z původní adresy. Nová hodnota ukazatele adresuje hodnotu stejného typu jako původní hodnota ukazatele, a proto je stejná jako indexování pole [(viz jednorozměrné pole a](../c-language/one-dimensional-arrays.md) [multidimenzionální pole](../c-language/multidimensional-arrays-c.md)). Pokud součtové body ukazatele mimo pole, s výjimkou prvního umístění nad rámec vysokého konce, není výsledek definován. Další informace naleznete v tématu [aritmetický ukazatel](../c-language/pointer-arithmetic.md).

## <a name="see-also"></a>Viz také

[Operátory sčítání jazyka C](../c-language/c-additive-operators.md)
