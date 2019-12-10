---
title: 'Postupy: detekce kompilace CLR'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, detecting /clr
- /clr compiler option [C++], detecting use of
ms.assetid: a9310045-4810-4637-a64a-0b31a08791c1
ms.openlocfilehash: 42b2952e3b63023ca26c6b1f7d0ccb8871082499
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988213"
---
# <a name="how-to-detect-clr-compilation"></a>Postupy: Rozpoznání kompilace s volbou /clr

Pomocí makra `_MANAGED` nebo `_M_CEE` můžete zjistit, zda je modul zkompilován s možností **/CLR**. Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md).

Další informace o makrech naleznete v tématu [Předdefinovaná makra](../preprocessor/predefined-macros.md).

## <a name="example"></a>Příklad

```cpp
// detect_CLR_compilation.cpp
// compile with: /clr
#include <stdio.h>

int main() {
   #if (_MANAGED == 1) || (_M_CEE == 1)
      printf_s("compiling with /clr\n");
   #else
      printf_s("compiling without /clr\n");
   #endif
}
```

## <a name="see-also"></a>Viz také:

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
