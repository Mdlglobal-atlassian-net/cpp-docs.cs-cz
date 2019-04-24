---
title: Chyba kompilátoru C2872
ms.date: 11/04/2016
f1_keywords:
- C2872
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
ms.openlocfilehash: 103998c7872b683c7405796ee28bd550246ae9bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257607"
---
# <a name="compiler-error-c2872"></a>Chyba kompilátoru C2872

"*symbol*': nejednoznačný symbol

Kompilátor nemůže určit, který symbol se odkazuje na. Více než jeden symbol se zadaným názvem je v oboru. Viz poznámky následující chybová zpráva pro umístění souborů a deklarace kompilátor pro nejednoznačný symbol nalezen. Chcete-li vyřešit tento problém, můžete plnému nejednoznačný symbol s použitím svůj obor názvů, třeba `std::byte` nebo `::byte`. Můžete také použít [aliasu oboru názvů](../../cpp/namespaces-cpp.md#namespace_aliases) přiřadit uvedeném oboru názvů pohodlný krátký název pro použití při odstraňování symboly ve zdrojovém kódu.

C2872 může dojít, pokud obsahuje soubor hlaviček [direktiva using](../../cpp/namespaces-cpp.md#using_directives), a následné záhlaví souboru je zahrnuta, který obsahuje typ, který je také v oboru názvů určenému ve `using` – direktiva. Zadejte `using` direktiv až po hlavičkové soubory jsou určeny pomocí všechny `#include`.

C2872 může dojít v sadě Visual Studio 2013 z důvodu konfliktu mezi `Windows::Foundation::Metadata::Platform` typ výčtu a C++/definované CX `Platform` oboru názvů. Chcete-li tento problém vyřešit, postupujte podle těchto kroků:

- Odeberte klauzuli "pomocí oboru názvů Windows::Foundation::Metadata" ze souborů projektu.

- Zadejte plně kvalifikovaný název pro libovolný typ, který je součástí tohoto oboru názvů.

## <a name="example"></a>Příklad

Následující ukázka generuje C2872, protože je nejednoznačný odkaz na proměnnou s názvem `i`; dvě proměnné se stejným názvem, jsou v oboru:

```cpp
// C2872.cpp
// compile with: cl /EHsc C2872.cpp
namespace A {
   int i;
}

using namespace A;
int i;
int main() {
   ::i++;   // ok, uses i from global namespace
   A::i++;   // ok, uses i from namespace A
   i++;   // C2872 ambiguous: ::i or A::i?
   // To fix this issue, use the fully qualified name
   // for the intended variable.
}
```
