---
title: Vyhledávání názvu závislého na argumentu (Koenig) ve funkcích
ms.date: 11/04/2016
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
ms.openlocfilehash: d979b79c0f712ed35a42a44047dd1091010c72bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650670"
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>Vyhledávání názvu závislého na argumentu (Koenig) ve funkcích

Kompilátor může použít vyhledávání názvu závislého na argumentu pro vyhledání definice neúplného volání funkce. Pro vyhledávání názvu závislého na argumentu je rovněž používán termín vyhledávání Koenig. Typ každého argumentu ve volání funkce je definován v rámci hierarchie oborů názvů, tříd, struktur, sjednocení nebo šablon. Při zadání neúplného [přípony](../cpp/postfix-expressions.md) volání funkce, vyhledává kompilátor definici funkce v hierarchii přidružené ke každému typu argumentu.

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