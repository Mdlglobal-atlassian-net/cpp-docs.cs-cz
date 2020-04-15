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
ms.openlocfilehash: 971ef08c5e79f851c502ea872c541517065797c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372036"
---
# <a name="overloading-unary-operators"></a>Přetížení unárních operátorů

Unární operátory, které mohou být přetíženy, jsou následující:

1. `!`([logické NOT](../cpp/logical-negation-operator-exclpt.md))

1. `&`([adresa- z](../cpp/address-of-operator-amp.md))

1. `~`(jeden[doplněk)](../cpp/one-s-complement-operator-tilde.md)

1. `*`([ukazatel dereference](../cpp/indirection-operator-star.md))

1. `+`([unární plus](../cpp/additive-operators-plus-and.md))

1. `-`([unární negace](../cpp/additive-operators-plus-and.md))

1. `++`([přírůstek](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--`([snížení )](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

1. operátory převodu

Operátory přípona přírůstek a`++` `--`snížení ( a ) jsou zpracovány samostatně [v přírůstek a snížení](../cpp/increment-and-decrement-operator-overloading-cpp.md).

Operátory převodu jsou také popsány v samostatné téma; viz [Převody typu definované uživatelem](../cpp/user-defined-type-conversions-cpp.md).

Následující pravidla platí pro všechny ostatní unární operátory. Chcete-li deklarovat funkci unárního operátoru jako nestatický člen, musíte ji deklarovat ve formě:

> *operace* **operátora** *ret typu* **()**

kde *ret-type* je návratový typ a *op* je jedním z operátorů uvedených v předchozí tabulce.

Chcete-li deklarovat funkci unárního operátoru jako globální funkci, musíte ji deklarovat ve formě:

> *operátor typu ret* **operator** *op* **(** *arg* **)**

kde *ret-type* a *op* jsou popsány pro funkce operátoru člena a *arg* je argument typu třídy, na kterém mají být provozovány.

> [!NOTE]
> Návratové typy unárních operátorů nejsou nijak omezeny. Například má smysl pro logické`!`NOT ( ) vrátit integrální hodnotu, ale to není vynuceno.

## <a name="see-also"></a>Viz také

[Přetížení operátora](../cpp/operator-overloading.md)
