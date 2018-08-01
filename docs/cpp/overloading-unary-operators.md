---
title: Přetížení unárních operátorů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c00f9d40fedd084afa2da6e2e7bfaf0ee831b3a9
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401877"
---
# <a name="overloading-unary-operators"></a>Přetížení unárních operátorů
Unární operátory, které mohou být přetíženy, jsou následující:  
  
1.  `!` ([logický operátor NOT](../cpp/logical-negation-operator-exclpt.md))  
  
2.  `&` ([adresy](../cpp/address-of-operator-amp.md))  
  
3.  `~` ([doplněk](../cpp/one-s-complement-operator-tilde.md))  
  
4.  `*` ([přesměrování ukazatele bylo](../cpp/indirection-operator-star.md))  
  
5.  `+` ([Unární plus](../cpp/additive-operators-plus-and.md))  
  
6.  `-` ([unární negace](../cpp/additive-operators-plus-and.md))  
  
7.  `++` ([přírůstek](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))  
  
8.  `--` ([snížení](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))  
  
9. operátory převodu  
  
 Přípony Inkrementace a dekrementace operátory (`++` a `--`) jsou popsány odděleně v [addref()](../cpp/increment-and-decrement-operator-overloading-cpp.md).  
  
 Operátory převodu jsou popsány také v samostatném tématu; Zobrazit [uživatelem definovaných převodů typu](../cpp/user-defined-type-conversions-cpp.md).  
  
 Následující pravidla platí pro všechny ostatní unární operátory. Chcete-li deklarovat funkci unárního operátoru jako nestatický člen, musíte ji deklarovat ve formě:  
  
 `ret-type operator` `op` `()`  
  
 kde `ret-type` je návratový typ a `op` je jeden z operátorů uvedených v předchozí tabulce.  
  
 Chcete-li deklarovat funkci unárního operátoru jako globální funkci, musíte ji deklarovat ve formě:  
  
 `ret-type operator` `op` (`arg` )  
  
 kde `ret-type` a `op` jsou popsány pro členské funkce operátora a `arg` je argument typu třídy, na kterém chcete pracovat.  
  
> [!NOTE]
>  Návratové typy unárních operátorů nejsou nijak omezeny. Například smysl pro logický operátor NOT (`!`) vrátit integrální hodnotu, ale to se nevynucuje.  
  
## <a name="see-also"></a>Viz také:  
 [Přetížení operátoru](../cpp/operator-overloading.md)