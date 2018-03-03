---
title: "Logický operátor AND: &amp; &amp; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '&&'
dev_langs:
- C++
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0612b9c2430d316aa9ba3a6d2dd9351342b5d352
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="logical-and-operator-ampamp"></a>Logický operátor AND:&amp;&amp;
## <a name="syntax"></a>Syntaxe  
  
```  
  
expression   
&&  
 expression  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Logický operátor AND (**&&**) vrátí logickou hodnotu **true** Pokud jsou oba operandy **true** a vrátí **false** jinak. Operandy jsou před vyhodnocením implicitně převáděny na typ `bool`, přičemž výsledek je také typu `bool`. Logické a má asociativnost zleva doprava.  
  
 Operandy na logický operátor AND nemusí být stejného typu, ale musí být celé číslo nebo ukazatel typu. Operandy jsou obvykle relační výrazy nebo výrazy rovnosti.  
  
 První operand úplně vyhodnocena a před pokračováním vyhodnocení výrazu pro logické a jsou dokončeny všechny vedlejší účinky.  
  
 Druhý operand se vyhodnocují jenom v případě, že první operand vyhodnotí na hodnotu true (nenulové hodnoty). Toto testování eliminuje zbytečně vyhodnocení Druhý operand při logický výraz a je false. Můžete to použít krátká smyčka – vyhodnocení, aby se zabránilo nulový ukazatel vyhodnocení, jak je znázorněno v následujícím příkladu:  
  
```  
char *pch = 0;  
...  
(pch) && (*pch = 'a');  
```  
  
 Pokud `pch` má hodnotu null (0), na pravé straně výraz nikdy vyhodnotí. Proto není možné přiřazení prostřednictvím ukazatele null.  
  
## <a name="operator-keyword-for-"></a>Operator – klíčové slovo pro & &  
 **a** operátor je ekvivalentem text  **&&** . Existují dva způsoby pro přístup **a** operátor v programy: zahrnout soubor hlaviček `iso646.h`, nebo kompilovat s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázat jazyková rozšíření).  
  
## <a name="example"></a>Příklad  
  
```  
// expre_Logical_AND_Operator.cpp  
// compile with: /EHsc  
// Demonstrate logical AND  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   int a = 5, b = 10, c = 15;  
   cout  << boolalpha  
         << "The true expression "  
         << "a < b && b < c yields "  
         << (a < b && b < c) << endl  
         << "The false expression "  
         << "a > b && b < c yields "  
         << (a > b && b < c) << endl;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Předdefinované C++ operátory přednost a Asociativnost](cpp-built-in-operators-precedence-and-associativity.md) [operátory předdefinované C++, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Logické operátory jazyka C](../c-language/c-logical-operators.md)