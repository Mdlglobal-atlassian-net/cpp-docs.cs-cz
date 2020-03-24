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
ms.openlocfilehash: 60444ee3c55df39e6b7820ff9b9d7ad81017b0da
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188490"
---
# <a name="overloading-unary-operators"></a>Přetížení unárních operátorů

Unární operátory, které mohou být přetíženy, jsou následující:

1. `!` ([logický operátor NOT](../cpp/logical-negation-operator-exclpt.md))

1. `&` ([adresa-z](../cpp/address-of-operator-amp.md))

1. `~` ([doplněk 1](../cpp/one-s-complement-operator-tilde.md))

1. `*` ([zpětný odkaz ukazatele](../cpp/indirection-operator-star.md))

1. `+` ([Unární plus](../cpp/additive-operators-plus-and.md))

1. `-` ([unární negace](../cpp/additive-operators-plus-and.md))

1. `++` ([přírůstek](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--` ([snížení](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

9. operátory převodu

Operátory přírůstku a snížení přípony (`++` a `--`) se zpracovávají samostatně v [přírůstcích a snížení](../cpp/increment-and-decrement-operator-overloading-cpp.md).

Operátory převodu jsou také popsány v samostatném tématu. viz [uživatelsky definované převody typů](../cpp/user-defined-type-conversions-cpp.md).

Následující pravidla platí pro všechny ostatní unární operátory. Chcete-li deklarovat funkci unárního operátoru jako nestatický člen, musíte ji deklarovat ve formě:

> *operátor ret-Type* **operator** *op* **()**

kde *ret-Type* je návratový typ a *op* je jedním z operátorů uvedených v předchozí tabulce.

Chcete-li deklarovat funkci unárního operátoru jako globální funkci, musíte ji deklarovat ve formě:

> operátor *ret-Type* **operator** *op* **(** *arg* **)**

kde *ret-Type* a *op* jsou popsány pro členské funkce operátora a *arg* je argument typu třídy, na kterém chcete pracovat.

> [!NOTE]
>  Návratové typy unárních operátorů nejsou nijak omezeny. Například dává smysl pro logickou hodnotu NOT (`!`), která vrátí celočíselnou hodnotu, ale toto není vynutilo.

## <a name="see-also"></a>Viz také

[Přetížení operátoru](../cpp/operator-overloading.md)
