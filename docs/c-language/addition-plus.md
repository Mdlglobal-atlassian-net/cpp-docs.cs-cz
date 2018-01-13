---
title: "Sčítání (+) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: pointers, adding integers
ms.assetid: b9014fee-825d-46ef-91db-5d46807081fc
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d41fe0369235bbdaf6723d01fdaf4bbf552a9ea5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="addition-"></a>Sčítání (+)
Operátor sčítání (**+**) způsobí, že jeho dva operandy má být přidán. Oba operandy mohou být typy s plovoucí desetinnou čárkou nebo celočíselné typy, případně může být jeden operand ukazatel a druhý celé číslo.  
  
 Po přidání celé do ukazatel, celočíselnou hodnotu (*i*) je převést vynásobením velikost hodnoty, které řeší ukazatele. Po převodu celočíselná hodnota představuje *i* paměti pozice, kdy každý pozice má délku určeného je ukazatel typu. Při přidání převedený celočíselnou hodnotu na hodnotu ukazatele, výsledkem je, nová hodnota ukazatele představující adresu *i* pozice z původní adresu. Nová hodnota ukazatele adresy hodnotu stejného typu jako původní hodnota ukazatele a proto je stejný jako pole indexování (viz [One-Dimensional pole](../c-language/one-dimensional-arrays.md) a [vícerozměrná pole](../c-language/multidimensional-arrays-c.md)). Pokud je ukazatel součet odkazuje mimo pole, s výjimkou na první umístění nad vysokou end výsledek není definován. Další informace najdete v tématu [aritmetika ukazatele](../c-language/pointer-arithmetic.md).  
  
## <a name="see-also"></a>Viz také  
 [Sčítací operátory jazyka C](../c-language/c-additive-operators.md)