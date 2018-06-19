---
title: Sčítání (+) | Microsoft Docs
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
ms.openlocfilehash: 3fcdb309e65c822e511b9cfd4a9ce7255be235a4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380924"
---
# <a name="addition-"></a>Sčítání (+)
Operátor sčítání (**+**) způsobí, že jeho dva operandy má být přidán. Oba operandy mohou být typy s plovoucí desetinnou čárkou nebo celočíselné typy, případně může být jeden operand ukazatel a druhý celé číslo.  
  
 Po přidání celé do ukazatel, celočíselnou hodnotu (*i*) je převést vynásobením velikost hodnoty, které řeší ukazatele. Po převodu celočíselná hodnota představuje *i* paměti pozice, kdy každý pozice má délku určeného je ukazatel typu. Při přidání převedený celočíselnou hodnotu na hodnotu ukazatele, výsledkem je, nová hodnota ukazatele představující adresu *i* pozice z původní adresu. Nová hodnota ukazatele adresy hodnotu stejného typu jako původní hodnota ukazatele a proto je stejný jako pole indexování (viz [One-Dimensional pole](../c-language/one-dimensional-arrays.md) a [vícerozměrná pole](../c-language/multidimensional-arrays-c.md)). Pokud je ukazatel součet odkazuje mimo pole, s výjimkou na první umístění nad vysokou end výsledek není definován. Další informace najdete v tématu [aritmetika ukazatele](../c-language/pointer-arithmetic.md).  
  
## <a name="see-also"></a>Viz také  
 [Sčítací operátory jazyka C](../c-language/c-additive-operators.md)