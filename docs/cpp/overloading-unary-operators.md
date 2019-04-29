---
title: Přetížení unárních operátorů
ms.date: 11/04/2016
helpviewer_keywords:
- unary operators [C++], plus
- increment operators [C++], overloaded
- unary operators [C++], minus
- operators [C++], unary
- redefinable unary operators [C++]
- unary operators [C++]
- pointer dereference operator overloading
- plus operator
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
ms.openlocfilehash: 802380bad59534e8402020142e394b3948032476
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377221"
---
# <a name="overloading-unary-operators"></a>Přetížení unárních operátorů

Unární operátory, které mohou být přetíženy, jsou následující:

1. `!` ([logický operátor NOT](../cpp/logical-negation-operator-exclpt.md))

1. `&` ([address-of](../cpp/address-of-operator-amp.md))

1. `~` ([doplněk](../cpp/one-s-complement-operator-tilde.md))

1. `*` ([přesměrování ukazatele bylo](../cpp/indirection-operator-star.md))

1. `+` ([Unární plus](../cpp/additive-operators-plus-and.md))

1. `-` ([unární negace](../cpp/additive-operators-plus-and.md))

1. `++` ([přírůstek](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--` ([snížení](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

9. operátory převodu

Přípony Inkrementace a dekrementace operátory (`++` a `--`) jsou popsány odděleně v [addref()](../cpp/increment-and-decrement-operator-overloading-cpp.md).

Operátory převodu jsou popsány také v samostatném tématu; Zobrazit [uživatelem definovaných převodů typu](../cpp/user-defined-type-conversions-cpp.md).

Následující pravidla platí pro všechny ostatní unární operátory. Chcete-li deklarovat funkci unárního operátoru jako nestatický člen, musíte ji deklarovat ve formě:

> *RET-type* **operátor** *op* **)**

kde *ret-type* je návratový typ a *op* je jeden z operátorů uvedených v předchozí tabulce.

Chcete-li deklarovat funkci unárního operátoru jako globální funkci, musíte ji deklarovat ve formě:

> *RET-type* **operátor** *op* **(** *arg* **)**

kde *ret-type* a *op* jsou popsány pro členské funkce operátora a *arg* je argument typu třídy, na kterém chcete pracovat.

> [!NOTE]
>  Návratové typy unárních operátorů nejsou nijak omezeny. Například smysl pro logický operátor NOT (`!`) vrátit integrální hodnotu, ale to se nevynucuje.

## <a name="see-also"></a>Viz také:

[Přetížení operátoru](../cpp/operator-overloading.md)