---
title: Primární výrazy
ms.date: 11/04/2016
helpviewer_keywords:
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
ms.openlocfilehash: 03f0d0d04ad8ef2b052b9303d15437c53369a003
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177622"
---
# <a name="primary-expressions"></a>Primární výrazy

Primární výrazy jsou stavebními bloky složitějších výrazů. Jsou to literály, názvy a názvy, které jsou kvalifikovány operátorem rozlišení oboru (`::`).  Primární výraz může mít některou z těchto forem:

```
literal
this
name
::name ( expression )
```

*Literál* je konstantní primární výraz. Jeho typ závisí na formuláři specifikace. Úplné informace o určení literálů naleznete v tématu [literály](../cpp/numeric-boolean-and-pointer-literals-cpp.md) .

Klíčové slovo **This** je ukazatel na objekt třídy. Je k dispozici v rámci funkce nestatického členu a odkazuje na instanci třídy, pro kterou byla funkce vyvolána. Klíčové slovo **This** nelze použít mimo tělo členské funkce třídy.

Typ **tohoto** ukazatele je `type` **\*const** (kde `type` je název třídy) v rámci funkcí, které nemění konkrétně **Tento** ukazatel. Následující příklad ukazuje deklarace členské funkce a **typy těchto typů:**

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

Další informace o úpravě typu **tohoto** ukazatele naleznete v [tomto ukazateli](this-pointer.md) .

Operátor rozlišení oboru (`::`) následovaný názvem představuje primární výraz.  Tyto názvy musí být jména v globálním rozsahu, ne názvy členů.  Typ tohoto výrazu je určen deklarací názvu. Je to hodnota l (to znamená, že může být zobrazena na levé straně výrazu operátoru přiřazení), pokud je deklarující název hodnota l. Operátoru rozsahu rozlišení umožňuje odkazování na globální název, i když je tento název skrytý v aktuálním oboru. Viz [obor](../cpp/scope-visual-cpp.md) pro příklad použití operátoru rozlišení oboru.

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

Níže uvedené příklady jsou považovány za *názvy*, a proto primární výrazy v různých formulářích:

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
