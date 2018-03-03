---
title: "Primární výrazy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0a6e811e1fe074ce488b09fca29926989bc7f355
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="primary-expressions"></a>Primární výrazy
Primární výrazy jsou stavebními bloky složitějších výrazů. Jsou literály, názvy a názvy kvalifikovaný operátor řešení rozsahu (`::`).  Primární výraz může mít některou z těchto forem:  
  
```  
  
      literal  
      this  
:: namename( expression )  
```  
  
 A *literálu* je primární konstantní výraz. Jeho typ závisí na formuláři specifikace. V tématu [literály](../cpp/numeric-boolean-and-pointer-literals-cpp.md) úplné informace o zadávání literály.  
  
 **To** – klíčové slovo je ukazatel na objekt třídy. Je k dispozici v rámci funkce nestatického členu a odkazuje na instanci třídy, pro kterou byla funkce vyvolána. **To** – klíčové slovo se nedají použít mimo tělo funkce člena třídy.  
  
 Typ **to** ukazatel `type`  **\*const** (kde `type` je název třídy) v rámci funkcí úprava není konkrétně **tento** ukazatel. Následující příklad ukazuje členské funkce deklarace a typy **to**:  
  
```  
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
  
 V tématu [tento ukazatel](this-pointer.md) pro další informace o změnách typu **to** ukazatel.  
  
 Operátor řešení rozsahu (`::`) následuje název se považuje za primární výraz.  Tyto názvy musí být jména v globálním rozsahu, ne názvy členů.  Typ tohoto výrazu je určen deklarací názvu. Je to hodnota l (to znamená, že může být zobrazena na levé straně výrazu operátoru přiřazení), pokud je deklarující název hodnota l. Operátoru rozsahu rozlišení umožňuje odkazování na globální název, i když je tento název skrytý v aktuálním oboru. V tématu [oboru](../cpp/scope-visual-cpp.md) příklad toho, jak chcete použít operátor řešení rozsahu.  
  
 Výraz uzavřený do závorek je primární výraz, jehož typ a hodnota jsou stejné jako typ a hodnota výrazu bez závorek. Je to hodnota l, pokud je výraz bez závorek hodnota l.  
  
 V kontextu syntaxe primární výrazu výše uvedené *název* znamená něco v syntaxi popsané pro [názvy](http://msdn.microsoft.com/en-us/1c49cc24-08d5-4884-b170-ba8ed42d80db), i když při použití operátor řešení rozsahu před názvem typy názvů může dojít pouze v třídě nejsou povoleny.  To zahrnuje názvy funkcí převodu definovaného uživatelem a názvy destruktorů.  
  
 Příklady primárních výrazů zahrnují:  
  
```  
100 // literal  
'c' // literal  
this // in a member function, a pointer to the class instance  
::func // a global function  
::operator + // a global operator function  
::A::B // a global qualified name  
( i + 1 ) // a parenthesized expression  
```  
  
 Následující příklady jsou zvažovány všechny *názvy*a proto primární výrazy v různých formách:  
  
```  
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