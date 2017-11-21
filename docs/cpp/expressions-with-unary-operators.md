---
title: "Výrazy s unárními operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 48ebd210b67f07847ceccec05625fe01eb15055b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="expressions-with-unary-operators"></a>Výrazy s unárními operátory
Unární operátory fungují s pouze jedním operandem ve výrazu. Unární operátory jsou následující:  
  
-   [Indirection – operátor (*)](../cpp/indirection-operator-star.md)  
  
-   [Address-of – operátor (&)](../cpp/address-of-operator-amp.md)  
  
-   [Unární plus (+) – operátor](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [Operátor unární negace (-)](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [Logický operátor negace (!)](../cpp/logical-negation-operator-exclpt.md)  
  
-   [Vlastní operátor doplňku (~)](../cpp/one-s-complement-operator-tilde.md)  
  
-   [Předpony operátor přírůstku (++)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [Operátor snížení předpony (-)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [Operátor přetypování)](../cpp/cast-operator-parens.md)  
  
-   [sizeof – operátor](../cpp/sizeof-operator.md)  
  
-   [__uuidof – operátor](../cpp/uuidof-operator.md)  
  
-   [__alignof – operátor](../cpp/alignof-operator.md)  
  
-   [New – operátor](../cpp/new-operator-cpp.md)  
  
-   [delete – operátor](../cpp/delete-operator-cpp.md)  
  
 Tyto operátory mít asociativnost zprava doleva. Unární výrazy obvykle zahrnují syntaxi, která předchází operátory nebo primární výraz.  
  
 Níže jsou uvedeny možné formy unární výrazy.  
  
-   *operátory – výraz*  
  
-   `++`*unární výraz*  
  
-   `--`*unární výraz*  
  
-   *Unární operátor* *výraz cast*  
  
-   `sizeof`*unární výraz*  
  
-   `sizeof(`*název typu*`)`  
  
-   `decltype(`*výraz*`)`  
  
-   *přidělení – výraz*  
  
-   *zrušení přidělení výraz*  
  
 Všechny *operátory výraz* se považuje za *unární výraz*, a protože je považována za jakékoli primární výraz *operátory výraz*, je všechny primární výrazy považovat za *unární výraz* také. Další informace najdete v tématu [výrazy přípony](../cpp/postfix-expressions.md) a [primární výrazy](../cpp/primary-expressions.md).  
  
 A *unární operátor* se skládá z jednoho nebo více z následujících znaků:`* & + - ! ~`  
  
 *Výraz cast* je unární výraz s volitelné přetypování na typ změnit. Další informace najdete v části [operátor přetypování: ()](../cpp/cast-operator-parens.md).  
  
 *Výraz* může být jakýkoli výraz. Další informace najdete v tématu [výrazy](../cpp/expressions-cpp.md).  
  
 *Přidělení výraz* odkazuje `new` operátor. *Navrácení výraz* odkazuje `delete` operátor. Další informace najdete v tématech v tomto tématu výše.  
  
## <a name="see-also"></a>Viz také  
 [Typy výrazů](../cpp/types-of-expressions.md)