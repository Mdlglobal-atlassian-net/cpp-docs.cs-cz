---
title: 'Logický operátor AND: &amp; &amp; | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4921a6de3072ef402ba355714ddd67328c3a3541
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406829"
---
# <a name="logical-and-operator-ampamp"></a>Logický operátor AND: &amp;&amp;
## <a name="syntax"></a>Syntaxe  
  
```  
expression && expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Logický operátor AND (**&&**) vrátí logickou hodnotu TRUE, pokud jsou oba operandy hodnotu TRUE a v opačném případě vrátí hodnotu FALSE. Operandy jsou implicitně převedeny na typ **bool** před hodnocení a výsledek je typu **bool**. Logický operátor AND má asociativní zleva doprava.  
  
 Operandy logického operátoru AND nemusí být stejného typu, ale musí být integrálového typu nebo typu ukazatele. Operandy jsou obvykle relační výrazy nebo výrazy rovnosti.  
  
 První operand je zcela vyhodnocen a všechny vedlejší účinky jsou dokončeny před pokračováním ve vyhodnocování logického výrazu AND.  
  
 Druhý operand je vyhodnocen pouze v případě, že první operand vyhodnocen na hodnotu true (nenulový). Toto vyhodnocení odstraňuje nepotřebná vyhodnocení druhého operandu po logický výraz AND je NEPRAVDA. To může být použito krátká smyčka – vyhodnocení, aby se zabránilo přístup přes ukazatel null, jak je znázorněno v následujícím příkladu:  
  
```cpp 
char *pch = 0;  
...  
(pch) && (*pch = 'a');  
```  
  
 Pokud `pch` má hodnotu null (0) pravé straně výraz nikdy není vyhodnocen. Proto není možné přiřazení přes ukazatel s hodnotou null.  
  
## <a name="operator-keyword-for-"></a>Klíčové slovo pro operátor & &  
 **a** operátor je textový ekvivalent operátoru **&&**. Existují dva způsoby přístupu k **a** operátor ve svých programech: zahrnutím souboru hlaviček `iso646.h`, nebo kompilací s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázání jazykových rozšíření).  
  
## <a name="example"></a>Příklad  
  
```cpp 
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
  
## <a name="see-also"></a>Viz také:  
 [Integrované operátory C++ Priorita a asociativita](cpp-built-in-operators-precedence-and-associativity.md)  
 [Integrované operátory C++, Priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Logické operátory jazyka C](../c-language/c-logical-operators.md)