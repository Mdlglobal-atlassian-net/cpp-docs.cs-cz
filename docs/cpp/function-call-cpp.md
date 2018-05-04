---
title: Volání (C++) funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, C++ functions
- functions [C++], calling
- operator overloading [C++], function calls
- function overloading [C++], function-call operator
- function calls, operator
- operators [C++], overloading
- operator overloading [C++], examples
- function call operator ()
ms.assetid: 5094254a-045b-46f7-8653-69bc91e80dce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85e7a752630b391d09140fa7552a452b3d2b751a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="function-call-c"></a>Volání funkcí (C++)
Operátor volání funkce je při vyvolání pomocí závorek binárním operátorem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
primary-expression ( expression-list )  
```  
  
## <a name="remarks"></a>Poznámky  
 V tomto kontextu `primary-expression` je první operand a `expression-list`, druhý operand je seznam argumentů, může být prázdný. Operátor volání funkce se používá pro operace, které vyžadují více parametrů. Toto funguje, protože `expression-list` je místo jedné operand seznam. Operátor volání funkce musí být nestatická členská funkce.  
  
 Operátor volání funkce nemění v případě přetížení způsob, jakým jsou funkce volány. Místo toho upravuje, jak se operátor interpretuje při použití na objekty daného typu třídy. Například následující kód by obvykle neměl význam:  
  
```  
Point pt;  
pt( 3, 2 );  
```  
  
 Zadaný operátor příslušné přetížené volání funkce, ale tuto syntaxi slouží k posunutí `x` koordinaci 3 jednotky a `y` koordinaci 2 jednotky. Následující kód ukazuje takovou definici:  
  
```  
// function_call.cpp  
class Point  
{  
public:  
    Point() { _x = _y = 0; }  
    Point &operator()( int dx, int dy )  
        { _x += dx; _y += dy; return *this; }  
private:  
    int _x, _y;  
};  
  
int main()  
{  
   Point pt;  
   pt( 3, 2 );  
}  
```  
  
 Je třeba poznamenat, že operátor volání funkce je použit na název objektu, nikoli na název funkce.  
  
 Můžete také přetížení operátor volání funkce pomocí ukazatel na funkci (spíše než samotná funkce).  
  
```cpp  
typedef void(*ptf)();  
void func()  
{  
}  
struct S  
{  
   operator ptf()  
   {  
      return func;  
   }  
};  
  
int main()  
{  
   S s;  
   s();//operates as s.operator ptf()()  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Přetížení operátoru](../cpp/operator-overloading.md)