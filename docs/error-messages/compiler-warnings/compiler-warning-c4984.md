---
title: Upozornění kompilátoru C4984
ms.date: 08/19/2019
f1_keywords:
- C4984
helpviewer_keywords:
- C4984
ms.openlocfilehash: 91ae30018c7de633d8ba23d538b301ad4bbac984
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69632894"
---
# <a name="compiler-warning-c4984"></a>Upozornění kompilátoru C4984

> If constexpr je rozšíření jazyka C++ 17.

## <a name="remarks"></a>Poznámky

Kompilátor nalezl `if constexpr` výraz v kódu zkompilovaném pomocí výchozího standardu c++ 14. Tento výraz se zadává od standardu C++ 17. Pokud vyžadujete kompatibilitu C++ 11 nebo C++ 14, tento výraz není přenosný.

C4984 se ve výchozím nastavení vydá jako chyba, ale je to Suppressible. Pokud chcete tento výraz povolit sestavením kódu jako C++ 17, použijte [/std: c++ 17 nebo/std: C + + nejnovější](../../build/reference/std-specify-language-standard-version.md). Chcete-li `if constexpr` použít výraz v kódu kompilovaném pro c++ 14 jako rozšíření společnosti Microsoft, můžete potlačit, zakázat nebo změnit úroveň upozornění chybové zprávy. Pomocí [/wd4984](../../build/reference/compiler-option-warning-level.md) můžete zakázat C4984 nebo __/w__*n*__4984__ , abyste ho místo chyby povolili jako upozornění na úrovni *n* . Nebo použijte [#pragma upozornění (potlačení: 4984)](../../preprocessor/warning.md) před řádek, který způsobuje upozornění ve zdrojovém souboru.

Toto upozornění je k dispozici počínaje verzí Visual Studio 2017 verze 15,3. Informace o tom, jak zakázat upozornění zavedená v konkrétní verzi kompilátoru nebo novější, naleznete v tématu [Upozornění kompilátoru podle verze kompilátoru](compiler-warnings-by-compiler-version.md).

## <a name="example"></a>Příklad

Tato ukázka generuje C4984 a ukazuje způsoby, jak ji opravit:

```cpp
// C4984.cpp
// compile with: cl /EHsc C4984.cpp
#include <iostream>

int main()
{
    constexpr bool compile_time = true;
    // Uncomment the following line or use /std:c++17 to fix
    // #pragma warning(suppress:4984)
    if constexpr (compile_time)
    {
        std::cout << "compile_time is true";
    }
    else
    {
        std::cout << "compile_time is false";
    }
}
```
