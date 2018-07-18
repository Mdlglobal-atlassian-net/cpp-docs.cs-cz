---
title: Primární výrazy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4356e15d1b74508b7fc2606b45b5fb2bc9a435eb
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966664"
---
# <a name="primary-expressions"></a>Primární výrazy
Primární výrazy jsou stavebními bloky složitějších výrazů. Jsou literály, názvy a názvy kvalifikovány operátorem rozlišení oboru (`::`).  Primární výraz může mít některou z těchto forem:  
  
```  
  
literal  
this
name  
::name ( expression )  
```  
  
 A *literálu* je konstantní primární výraz. Jeho typ závisí na formuláři specifikace. Zobrazit [literály](../cpp/numeric-boolean-and-pointer-literals-cpp.md) podrobnější informace o zadávání literálů.  
  
 **To** – klíčové slovo je ukazatel na objekt třídy. Je k dispozici v rámci funkce nestatického členu a odkazuje na instanci třídy, pro kterou byla funkce vyvolána. **To** – klíčové slovo nelze použít mimo tělo funkce člena třídy.  
  
 Typ **to** ukazatel `type`  **\*const** (kde `type` je název třídy) v rámci funkcí, které ne specificky upravují **tento** ukazatele. Následující příklad ukazuje členské funkce deklarace a typy **to**:  
  
```cpp 
// expre_Primary_Expressions.cpp  
// compile with: /LD  
class Example  
{  
public:  
    void Func();          //  * const this  
    void Func() const;    //  const * const this  
    void Func() volatile; //  volatile * const this  
};  
```  
  
 V tématu [ukazatele this](this-pointer.md) pro další informace o změnách typu **to** ukazatele.  
  
 Operátor rozlišení oboru (`::`) následovaný názvem představuje primární výraz.  Tyto názvy musí být jména v globálním rozsahu, ne názvy členů.  Typ tohoto výrazu je určen deklarací názvu. Je to hodnota l (to znamená, že může být zobrazena na levé straně výrazu operátoru přiřazení), pokud je deklarující název hodnota l. Operátoru rozsahu rozlišení umožňuje odkazování na globální název, i když je tento název skrytý v aktuálním oboru. Zobrazit [oboru](../cpp/scope-visual-cpp.md) příklad použití operátoru rozsahu rozlišení.  
  
 Výraz uzavřený do závorek je primární výraz, jehož typ a hodnota jsou stejné jako typ a hodnota výrazu bez závorek. Je to hodnota l, pokud je výraz bez závorek hodnota l.  
  
 Příklady primárních výrazů zahrnují:  
  
```cpp 
100 // literal  
'c' // literal  
this // in a member function, a pointer to the class instance  
::func // a global function  
::operator + // a global operator function  
::A::B // a global qualified name  
( i + 1 ) // a parenthesized expression  
```  
  
 Následující příklady jsou všechny považovány za *názvy*a proto za primární výrazy v různých formách:  
  
```cpp 
MyClass // a identifier  
MyClass::f // a qualified name  
operator = // an operator function name  
operator char* // a conversion operator function name  
~MyClass // a destructor name  
A::B   // a qualified name  
A<int> // a template id  
```  
  
## <a name="see-also"></a>Viz také  
 [Typy výrazů](../cpp/types-of-expressions.md)