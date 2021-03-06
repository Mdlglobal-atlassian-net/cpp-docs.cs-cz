---
title: Kompilátor upozornění (úroveň 4) C4459
ms.date: 11/04/2016
f1_keywords:
- C4459
helpviewer_keywords:
- C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
ms.openlocfilehash: 441d01eca7c8266b6d7948508eeb561341e64c57
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447767"
---
# <a name="compiler-warning-level-4-c4459"></a>Kompilátor upozornění (úroveň 4) C4459

> deklarace "*identifikátor*' skryje globální deklaraci

Deklarace *identifikátor* v místním oboru skrývá deklaraci nazvanými *identifikátor* v globálním oboru. Toto upozornění umožňuje zjistit, která odkazuje na *identifikátor* v tomto oboru vyřešit lokálně deklarované verzi není globální verze, který může nebo nemusí být vašich představ. Obecně doporučujeme, abyste že minimalizovali použití globální proměnné podle osvědčené technické praxe. Chcete-li minimalizovat znečištění globální obor názvů, doporučujeme používat s názvem oboru názvů pro globální proměnné.

Toto upozornění byla nová v sadě Visual Studio 2015, v aplikaci Microsoft C++ verze kompilátoru 18.00 hodin. Chcete-li potlačit upozornění z této verze kompilátoru nebo později při migraci kódu, použijte [/WV: 18](../../build/reference/compiler-option-warning-level.md) – možnost kompilátoru.

## <a name="example"></a>Příklad

Následující ukázka generuje C4459:

```cpp
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() {
    int global_or_local; // warning C4459
    global_or_local = 2;
}
```

Jedním ze způsobů řešení tohoto problému je vytvoření oboru názvů pro váš globální parametry, ale velmi riskantní používat `using` směrnice přivádí daného oboru názvů do oboru, takže všechny odkazy musí použít jednoznačný kvalifikované názvy:

```cpp
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() {
    int global_or_local; // OK
    global_or_local = 2;
    globals::global_or_local = 3;
}
```
