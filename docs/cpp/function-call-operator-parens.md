---
title: "Operátor volání funkce: () | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- ( ) function call operator
- function calls, C++ functions
- () function call operator
- postfix operators [C++]
- function calls, operator
- functions [C++], function-call operator
- function call operator ()
ms.assetid: 50c92e59-a4bf-415a-a6ab-d66c679ee80a
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b28aa56905271da3e60cdfc08da855b6b4a23cc8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="function-call-operator-"></a>Operátor volání funkce: ()
Výraz operátory a operátor volání funkce **()**, určuje volání funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
postfix-expression   
( [argument-expression-list ] )  
```  
  
## <a name="remarks"></a>Poznámky  
 Argumenty, které mají operátor volání funkce jsou nula nebo více výrazů, které jsou oddělené čárkami – skutečné argumenty funkce.  
  
 *Operátory výraz* adresu funkce (například identifikátor funkce nebo hodnota ukazatel na funkci), se musí vyhodnotit a *seznam argumentů výraz* je seznam výrazů (oddělené čárkami) jejichž hodnoty (argumenty) jsou předaný funkci. *Seznam argumentů výraz* argument nesmí být prázdné.  
  
 *Operátory výraz* musí být jedním z těchto typů:  
  
-   Funkce vrácení typu `T`. Je také příklad prohlášení  
  
    ```  
    T func( int i )  
    ```  
  
-   Ukazatel na funkci vrácení typu `T`. Je také příklad prohlášení  
  
    ```  
    T (*func)( int i )  
    ```  
  
-   Odkaz na funkci vrácení typu `T`. Je také příklad prohlášení  
  
    ```  
    T (&func)(int i)  
    ```  
  
-   Ukazatele na člena funkce dereference vracejících typ `T`. Jsou například volání funkcí  
  
    ```  
    (pObject->*pmf)();  
    (Object.*pmf)();  
    ```  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu volání funkce standardní knihovny `strcat_s` s tři argumenty:  
  
```  
// expre_Function_Call_Operator.cpp  
// compile with: /EHsc  
  
#include <iostream>  
#include <string>  
  
// C++ Standard Library name space  
using namespace std;  
  
int main()  
{  
    enum  
    {  
        sizeOfBuffer = 20  
    };  
  
    char s1[ sizeOfBuffer ] = "Welcome to ";  
    char s2[ ] = "C++";  
  
    strcat_s( s1, sizeOfBuffer, s2 );  
  
    cout << s1 << endl;  
}  
```  
  
```Output  
Welcome to C++  
```  
  
## <a name="function-call-results"></a>Výsledky volání funkce  
 Volání funkce vyhodnocuje r-hodnotu, pokud není funkce deklarována jako typ odkazu. Funkce s návratovým typem ve formě odkazu vyhodnocují l-hodnoty a lze je použít na levé straně příkazu přiřazení následujícím způsobem:  
  
```  
// expre_Function_Call_Results.cpp  
// compile with: /EHsc  
#include <iostream>  
class Point  
{  
public:  
    // Define "accessor" functions as  
    // reference types.  
    unsigned& x() { return _x; }  
    unsigned& y() { return _y; }  
private:  
    unsigned _x;  
    unsigned _y;  
};  
  
using namespace std;  
int main()  
{  
    Point ThePoint;  
  
    ThePoint.x() = 7;           // Use x() as an l-value.  
    unsigned y = ThePoint.y();  // Use y() as an r-value.  
  
    // Use x() and y() as r-values.  
    cout << "x = " << ThePoint.x() << "\n"  
         << "y = " << ThePoint.y() << "\n";  
}  
```  
  
 Předchozí kód definuje třídu s názvem `Point`, který obsahuje privátní data objekty představující *x* a *y* souřadnice. Tyto datové objekty musejí být upraveny a jejich hodnoty načteny. Tento program je pouze jednou z několika možností pro takovou třídu. Použití funkcí `GetX` a `SetX` nebo `GetY` a `SetY` představuje další možnost.  
  
 Funkce vracející typy tříd, ukazatele na typy tříd nebo odkazy na typy tříd lze použít jako levý operand pro operátory výběru členů. Proto je platný následující kód:  
  
```  
// expre_Function_Results2.cpp  
class A {  
public:  
   A() {}  
   A(int i) {}  
   int SetA( int i ) {  
      return (I = i);  
   }  
  
   int GetA() {  
      return I;  
   }  
  
private:  
   int I;  
};  
  
A func1() {  
   A a = 0;  
   return a;  
}  
  
A* func2() {  
   A *a = new A();  
   return a;  
}  
  
A& func3() {  
   A *a = new A();  
   A &b = *a;  
   return b;  
}  
  
int main() {  
   int iResult = func1().GetA();  
   func2()->SetA( 3 );  
   func3().SetA( 7 );  
}  
```  
  
 Funkce lze volat rekurzivně. Další informace o deklaracích funkcí najdete v tématu [funkce](functions-cpp.md). Související materiálu je v [Program a propojení](../cpp/program-and-linkage-cpp.md).  
  
## <a name="see-also"></a>Viz také  
 [Výrazy přípony](../cpp/postfix-expressions.md)   
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Volání funkce](../c-language/function-call-c.md)   
