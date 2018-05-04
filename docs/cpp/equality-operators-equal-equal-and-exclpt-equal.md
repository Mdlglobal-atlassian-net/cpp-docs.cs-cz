---
title: 'Operátory rovnosti: == a! = | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- not_eq
- '!='
- ==
dev_langs:
- C++
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16e4a85f31777581df1a138de6d50b1057253e5b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="equality-operators--and-"></a>Operátory rovnosti: == a !=
## <a name="syntax"></a>Syntaxe  
  
```  
expression == expression  
expression != expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Operátory rovnosti binární porovnání operandy striktní rovnosti nebo nerovnosti.  
  
 Operátory rovnosti rovno (`==`) a není rovno (`!=`), mít nižší prioritu než relační operátory, ale chovají podobně. Typ výsledku pro tyto operátory je `bool`.  
  
 Operátor je rovno (`==`) vrátí **true** (1) Pokud oba operandy mají stejnou hodnotu; jinak vrátí **false** (0). Operátor není rovno (`!=`) vrátí **true** Pokud operandy nemají stejnou hodnotu; jinak vrátí **false**.  
  
## <a name="operator-keyword-for-"></a>Operator – klíčové slovo pro! =  
 Operátor `not_eq` je textový ekvivalent operátoru `!=`. Existují dva způsoby pro přístup `not_eq` operátor v programy: zahrnout soubor hlaviček `iso646.h`, nebo kompilovat s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázat jazyková rozšíření).  
  
## <a name="example"></a>Příklad  
  
```  
// expre_Equality_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << boolalpha  
         << "The true expression 3 != 2 yields: "  
         << (3 != 2) << endl  
         << "The false expression 20 == 10 yields: "  
         << (20 == 10) << endl;  
}  
```  
  
 Operátory rovnosti můžete porovnat ukazatelé na členy stejného typu. Porovnání jsou prováděny převody ukazatele na člena. Ukazatelé na členy můžete také porovnání s konstantní výraz, jehož výsledkem je 0.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)   
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Relační operátory a operátory rovnosti jazyka C](../c-language/c-relational-and-equality-operators.md)