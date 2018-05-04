---
title: 'Operátory ukazatelů na členy: .* a -&gt;* | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- .*
- ->*
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], pointer
- pointer-to-member operators [C++]
- .* operator
- expressions [C++], operators
- ->* operator
ms.assetid: 2632be3f-1c81-4523-b56c-982a92a68688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdece555ea58f0a1321258405fa76ba02cf12efa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="pointer-to-member-operators--and--gt"></a>Operátory ukazatelů na členy: .* a -&gt;*
## <a name="syntax"></a>Syntaxe  
  
```  
expression .* expression  
expression ->* expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Operátory ukazatelů na členy. * a ->\*, vrátí hodnotu člena určité třídy pro zadaný objekt na levé straně výrazu.  Pravá strana musí udávat člen třídy.  Následující příklad ukazuje způsob použití těchto operátorů:  
  
```  
// expre_Expressions_with_Pointer_Member_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
class Testpm {  
public:  
   void m_func1() { cout << "m_func1\n"; }  
   int m_num;  
};  
  
// Define derived types pmfn and pmd.  
// These types are pointers to members m_func1() and  
// m_num, respectively.  
void (Testpm::*pmfn)() = &Testpm::m_func1;  
int Testpm::*pmd = &Testpm::m_num;  
  
int main() {  
   Testpm ATestpm;  
   Testpm *pTestpm = new Testpm;  
  
// Access the member function  
   (ATestpm.*pmfn)();  
   (pTestpm->*pmfn)();   // Parentheses required since * binds  
                        // less tightly than the function call.  
  
// Access the member data  
   ATestpm.*pmd = 1;  
   pTestpm->*pmd = 2;  
  
   cout  << ATestpm.*pmd << endl  
         << pTestpm->*pmd << endl;  
   delete pTestpm;  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
m_func1  
m_func1  
1  
2  
```  
  
 V předchozím příkladu je pomocí ukazatele na člen `pmfn` vyvolána členská funkce `m_func1`. Jiný ukazatel na člen, `pmd`, je použit k přístupu ke členu `m_num`.  
  
 Binární operátor .* kombinuje svůj první operand, který musí být typu objektu třídy, se svým druhým operandem, který musí být typu ukazatele na člen.  
  
 Binární operátor -> * kombinuje jeho první operand, který musí být ukazatel na objekt typu třídy, se druhý operand, který musí být typu ukazatele na člena.  
  
 Ve výrazu obsahujícím operátor .* musí být první operand typu třídy ukazatele zadaného ve druhém operandu, pro nějž musí být první operand zároveň přístupný, nebo přístupného typu jednoznačně odvozeného z dané třídy, pro kterou také musí být přístupný.  
  
 Ve výrazu obsahující-> * První operand v musí být typu "ukazatel na typu třídy" typu zadán Druhý operand operátoru, nebo ho musí být typu jednoznačně odvozen od třídy.  
  
## <a name="example"></a>Příklad  
 Vezměte v úvahu následující třídy a část programu:  
  
```  
// expre_Expressions_with_Pointer_Member_Operators2.cpp  
// C2440 expected  
class BaseClass {  
public:  
   BaseClass(); // Base class constructor.  
   void Func1();  
};  
  
// Declare a pointer to member function Func1.  
void (BaseClass::*pmfnFunc1)() = &BaseClass::Func1;  
  
class Derived : public BaseClass {  
public:  
   Derived();  // Derived class constructor.  
   void Func2();  
};  
  
// Declare a pointer to member function Func2.  
void (Derived::*pmfnFunc2)() = &Derived::Func2;  
  
int main() {  
   BaseClass ABase;  
   Derived ADerived;  
  
   (ABase.*pmfnFunc1)();   // OK: defined for BaseClass.  
   (ABase.*pmfnFunc2)();   // Error: cannot use base class to  
                           // access pointers to members of  
                           // derived classes.   
  
   (ADerived.*pmfnFunc1)();   // OK: Derived is unambiguously  
                              // derived from BaseClass.   
   (ADerived.*pmfnFunc2)();   // OK: defined for Derived.  
}  
```  
  
 Výsledkem. * nebo ->\* operátory ukazatelů na členy je objekt, nebo funkce typ zadaný v deklaraci ukazatele na člena. V předchozím příkladu je tedy výsledkem výrazu `ADerived.*pmfnFunc1()` ukazatel na funkci vracející typ void. Je-li druhý operand l-hodnotou, je i tento výsledek l-hodnotou.  
  
> [!NOTE]
>  Je-li výsledkem jednoho z operátorů ukazatele na člen funkce, lze jej použít pouze jako operand operátoru volání funkce.  
  
## <a name="see-also"></a>Viz také  
 [Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

