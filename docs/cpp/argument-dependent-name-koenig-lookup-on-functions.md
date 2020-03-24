---
title: Vyhledávání názvu závislého na argumentu (Koenig) ve funkcích
ms.date: 11/04/2016
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
ms.openlocfilehash: 88811e8070fdfe398bc12734221dee772515d8bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190533"
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>Vyhledávání názvu závislého na argumentu (Koenig) ve funkcích

Kompilátor může použít vyhledávání názvu závislého na argumentu pro vyhledání definice neúplného volání funkce. Pro vyhledávání názvu závislého na argumentu je rovněž používán termín vyhledávání Koenig. Typ každého argumentu ve volání funkce je definován v rámci hierarchie oborů názvů, tříd, struktur, sjednocení nebo šablon. Když zadáte nekvalifikované volání funkce [přípony](../cpp/postfix-expressions.md) , kompilátor vyhledá definici funkce v hierarchii přidružené k jednotlivým typům argumentů.

## <a name="example"></a>Příklad

V příkladu kompilátor zaznamená, že funkce `f()` přebírá argument `x`. Argument `x` je typu `A::X`, který je definován v oboru názvů `A`. Kompilátor vyhledá obor názvů `A` a najde definici funkce `f()`, která přebírá argument typu `A::X`.

```cpp
// argument_dependent_name_koenig_lookup_on_functions.cpp
namespace A
{
   struct X
   {
   };
   void f(const X&)
   {
   }
}
int main()
{
// The compiler finds A::f() in namespace A, which is where
// the type of argument x is defined. The type of x is A::X.
   A::X x;
   f(x);
}
```
