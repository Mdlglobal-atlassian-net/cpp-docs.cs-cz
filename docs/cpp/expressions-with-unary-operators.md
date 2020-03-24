---
title: Výrazy s unárními operátory
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
ms.openlocfilehash: 26aad64e5b9c7a496c2e6bb131b82740c06abe07
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188971"
---
# <a name="expressions-with-unary-operators"></a>Výrazy s unárními operátory

Unární operátory pracují pouze s jedním operandem ve výrazu. Unární operátory jsou následující:

- [Operátor dereference (*)](../cpp/indirection-operator-star.md)

- [Address-of – operátor (&)](../cpp/address-of-operator-amp.md)

- [Unární operátor plus (+)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [Operátor unární negace (-)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [Logický operátor negace (!)](../cpp/logical-negation-operator-exclpt.md)

- [Druhý operátor doplňku (~)](../cpp/one-s-complement-operator-tilde.md)

- [Operátor přírůstku předpony (+ +)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Operátor snížení předpony (--)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Operátor přetypování ()](../cpp/cast-operator-parens.md)

- [sizeof – operátor](../cpp/sizeof-operator.md)

- [operátor __uuidof](../cpp/uuidof-operator.md)

- [operátor __alignof](../cpp/alignof-operator.md)

- [New – operátor](../cpp/new-operator-cpp.md)

- [delete – operátor](../cpp/delete-operator-cpp.md)

Tyto operátory mají asociativita zprava doleva. Unární výrazy obecně zahrnují syntaxi, která předchází příponou nebo primárním výrazem.

Níže jsou uvedené možné formy unárních výrazů.

- *výraz přípony*

- `++` *unární výraz*

- `--` *unární výraz*

- *unární operátor* *přetypování – výraz*

- **sizeof** *unární výraz*

- *název typu* `sizeof(` `)`

- *výraz* `decltype(` `)`

- *přidělení – výraz*

- *zrušení přidělení – výraz*

Libovolný *příponový výraz* je považován za *unární výraz*a protože jakýkoliv primární výraz je považován za *výraz přípony*, jsou všechny primární výrazy považovány také za *unární výraz* . Další informace naleznete v tématu [výrazy přípony](../cpp/postfix-expressions.md) a [primární výrazy](../cpp/primary-expressions.md).

*Unární operátor* se skládá z jednoho nebo více následujících symbolů: `* & + - ! ~`

*Výraz cast* je unární výraz s volitelným přetypováním pro změnu typu. Další informace naleznete v tématu [operátor přetypování: ()](../cpp/cast-operator-parens.md).

*Výraz* může být libovolný výraz. Další informace najdete v tématu [výrazy](../cpp/expressions-cpp.md).

*Výraz alokace* odkazuje na operátor **New** . *Výraz zrušení přidělení* odkazuje na operátor **Delete** . Další informace najdete v odkazech dříve v tomto tématu.

## <a name="see-also"></a>Viz také

[Typy výrazů](../cpp/types-of-expressions.md)
