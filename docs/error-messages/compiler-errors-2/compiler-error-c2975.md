---
title: Chyba kompilátoru C2975
ms.date: 11/04/2016
f1_keywords:
- C2975
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
ms.openlocfilehash: 66b7c0d61cbc8141b9ed3e5f6eb329b68eb00477
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344691"
---
# <a name="compiler-error-c2975"></a>Chyba kompilátoru C2975

> "*argument*': Neplatný argument šablony pro"*typ*", očekával se konstantní výraz za kompilace

Argument šablony se neshoduje s deklarace šablony; konstantní výraz by se zobrazit v lomených závorkách. Jako argumenty šablony nejsou povoleny proměnné. Zkontrolujte definici šablony se najít správné typy.

## <a name="example"></a>Příklad

Následující ukázka generuje C2975 a také ukazuje správné použití:

```cpp
// C2975.cpp
template<int I>
class X {};

int main() {
   int i = 4, j = 2;
   X<i + j> x1;   // C2975
   X<6> x2;   // OK
}
```

C2975 vyvolá také při použití &#95; &#95;řádku&#95; &#95; jako konstantu kompilace s [/zi](../../build/reference/z7-zi-zi-debug-information-format.md). Jedním řešením může být pro kompilaci pomocí [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) místo **/zi**.

```cpp
// C2975b.cpp
// compile with: /ZI
// processor: x86
template<long line>
void test(void) {}

int main() {
   test<__LINE__>();   // C2975
}
```