---
title: Chyba kompilátoru C2975
ms.date: 11/04/2016
f1_keywords:
- C2975
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
ms.openlocfilehash: 70fc648de8bcf4f1e85edf3a12cc0b7d3d70625f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201562"
---
# <a name="compiler-error-c2975"></a>Chyba kompilátoru C2975

> '*argument*': neplatný argument šablony pro '*Type*', byl očekáván výraz konstanty při kompilaci

Argument šablony neodpovídá deklaraci šablony; v lomených závorkách by se měl objevit konstantní výraz. Proměnné nejsou povoleny jako skutečné argumenty šablony. Ověřte definici šablony a vyhledejte správné typy.

## <a name="example"></a>Příklad

Následující ukázka vygeneruje C2975 a také zobrazí správné použití:

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

K C2975 dochází také při použití &#95; &#95;řádku&#95; &#95; jako konstanty při kompilaci s [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md). Jedno řešení by bylo zkompilováno pomocí [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) namísto **/Zi**.

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
