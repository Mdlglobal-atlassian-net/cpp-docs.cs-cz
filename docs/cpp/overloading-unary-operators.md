---
title: "Přetížení unárních operátorů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 54c3e7eff420c5ed562e71235d204800eff5019a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="overloading-unary-operators"></a>Přetížení unárních operátorů
Unární operátory, které mohou být přetíženy, jsou následující:  
  
1.  `!`([logické není](../cpp/logical-negation-operator-exclpt.md))  
  
2.  `&`([adresy](../cpp/address-of-operator-amp.md))  
  
3.  `~`([jeden na doplňku](../cpp/one-s-complement-operator-tilde.md))  
  
4.  `*`([zrušení ukazatele](../cpp/indirection-operator-star.md))  
  
5.  `+`([Unární plus](../cpp/additive-operators-plus-and.md))  
  
6.  `-`([unární negace](../cpp/additive-operators-plus-and.md))  
  
7.  `++`([přírůstek](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))  
  
8.  `--`([snížení](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))  
  
9. operátory převodu  
  
 Operátory přírůstku a snížení operátory (`++` a  **--** ) jsou zpracovány v samostatně [zvýší a sníží](../cpp/increment-and-decrement-operator-overloading-cpp.md).  
  
 Operátory převodu jsou popsány i v samostatném tématu; v tématu [uživatelem definované převody typů](../cpp/user-defined-type-conversions-cpp.md).  
  
 Následující pravidla platí pro všechny ostatní unární operátory. Chcete-li deklarovat funkci unárního operátoru jako nestatický člen, musíte ji deklarovat ve formě:  
  
 `ret-type operator` `op` `()`  
  
 kde `ret-type` je návratový typ a `op` je jeden z operátorů uvedené v předchozí tabulce.  
  
 Chcete-li deklarovat funkci unárního operátoru jako globální funkci, musíte ji deklarovat ve formě:  
  
 `ret-type operator` `op` (`arg` )  
  
 kde `ret-type` a `op` jsou popsané pro členské funkce operátor a `arg` je argument typu třídy, na kterém se bude pracovat.  
  
> [!NOTE]
>  Návratové typy unárních operátorů nejsou nijak omezeny. Například má smysl pro logický operátor NOT (`!`) vrátit celočíselné hodnoty, ale to se nevynucuje.  
  
## <a name="see-also"></a>Viz také  
 [Přetížení operátoru](../cpp/operator-overloading.md)