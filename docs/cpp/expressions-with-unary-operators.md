---
title: Výrazy s unárními operátory | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78808ba4ce8d54ecc8e88516ae5f9b2521f50979
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403976"
---
# <a name="expressions-with-unary-operators"></a>Výrazy s unárními operátory
Unární operátory pracují na pouze jeden operand ve výrazu. Unární operátory jsou následující:  
  
-   [Operátor dereference (*)](../cpp/indirection-operator-star.md)  
  
-   [Operátor address-of (&)](../cpp/address-of-operator-amp.md)  
  
-   [Unární plus (+) – operátor](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [Operátor unární negace (-)](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [Operátor logické negace (!)](../cpp/logical-negation-operator-exclpt.md)  
  
-   [Jeden z operátorů doplňku (~)](../cpp/one-s-complement-operator-tilde.md)  
  
-   [Předpona operátoru Inkrementace (++)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [Operátor dekrementace předpony (-)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [Operátor přetypování)](../cpp/cast-operator-parens.md)  
  
-   [sizeof – operátor](../cpp/sizeof-operator.md)  
  
-   [__uuidof – operátor](../cpp/uuidof-operator.md)  
  
-   [__alignof – operátor](../cpp/alignof-operator.md)  
  
-   [New – operátor](../cpp/new-operator-cpp.md)  
  
-   [delete – operátor](../cpp/delete-operator-cpp.md)  
  
 Tyto operátory mají asociativitu zprava doleva. Výrazy s unárními obvykle zahrnují syntaxe, která předchází li uplatněna přípona nebo primární výraz.  
  
 Tady jsou možné typy unární výrazů.  
  
-   *výraz přípony*  
  
-   `++` *Unární výraz*  
  
-   `--` *Unární výraz*  
  
-   *Unární operátor* *výrazem přetypování.*  
  
-   **operátor sizeof:** *unární výraz*  
  
-   `sizeof(` *Název typu* `)`  
  
-   `decltype(` *Výraz* `)`  
  
-   *přidělení – výraz*  
  
-   *zrušení přidělení – výraz*  
  
 Žádné *postfix-expression* se považuje za *unární výraz*, a protože se považuje za jakékoli primární výraz *postfix-expression*, se žádné primární výrazy považovat za *unární výraz* také. Další informace najdete v tématu [výrazy přípony](../cpp/postfix-expressions.md) a [primární výrazy](../cpp/primary-expressions.md).  
  
 A *unární operátor* obsahuje jeden nebo více z těchto symbolů: `* & + - ! ~`  
  
 *Výrazem přetypování* je jednočlenný výraz s volitelné přetypování na typ změnit. Další informace najdete v části [operátor přetypování: ()](../cpp/cast-operator-parens.md).  
  
 *Výraz* může být libovolný výraz. Další informace najdete v tématu [výrazy](../cpp/expressions-cpp.md).  
  
 *Allocation-expression* odkazuje **nové** operátor. *Zrušení přidělení výraz* odkazuje na **odstranit** operátor. Další informace najdete v tématech dříve v tomto tématu.  
  
## <a name="see-also"></a>Viz také:  
 [Typy výrazů](../cpp/types-of-expressions.md)