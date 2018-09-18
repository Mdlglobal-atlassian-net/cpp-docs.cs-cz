---
title: Chyba kompilátoru C2872 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2872
dev_langs:
- C++
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 038c3475a6041dfb719bb2270a87ac2898f8b958
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036752"
---
# <a name="compiler-error-c2872"></a>Chyba kompilátoru C2872

"*symbol*': nejednoznačný symbol

Kompilátor nemůže určit, který symbol se odkazuje na. Více než jeden symbol se zadaným názvem je v oboru. Viz poznámky následující chybová zpráva pro umístění souborů a deklarace kompilátor pro nejednoznačný symbol nalezen. Chcete-li vyřešit tento problém, můžete plnému nejednoznačný symbol s použitím svůj obor názvů, třeba `std::byte` nebo `::byte`. Můžete také použít [aliasu oboru názvů](../../cpp/namespaces-cpp.md#namespace_aliases) přiřadit uvedeném oboru názvů pohodlný krátký název pro použití při odstraňování symboly ve zdrojovém kódu.

C2872 může dojít, pokud obsahuje soubor hlaviček [direktiva using](../../cpp/namespaces-cpp.md#using_directives), a následné záhlaví souboru je zahrnuta, který obsahuje typ, který je také v oboru názvů určenému ve `using` – direktiva. Zadejte `using` direktiv až po hlavičkové soubory jsou určeny pomocí všechny `#include`.

Další informace o C2872, najdete v článcích znalostní báze [PRB: kompilátoru chyby při používáte #import s XML v aplikaci Visual C++ .NET](http://support.microsoft.com/kb/316317) a ["C2872 Chyba: 'Platformy': nejednoznačný symbol" chybová zpráva při použití Obor názvů Windows::Foundation::metadata v sadě Visual Studio 2013](https://support.microsoft.com/kb/2890859).

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