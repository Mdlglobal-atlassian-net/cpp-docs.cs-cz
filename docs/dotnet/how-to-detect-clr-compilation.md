---
title: 'Postupy: zjištění kompilaci - clr'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, detecting /clr
- /clr compiler option [C++], detecting use of
ms.assetid: a9310045-4810-4637-a64a-0b31a08791c1
ms.openlocfilehash: 600c74bfda6673295269902021afcecd95b90077
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590824"
---
# <a name="how-to-detect-clr-compilation"></a>Postupy: Rozpoznání kompilace s volbou /clr

Použití `_MANAGED` nebo `_M_CEE` – makro, pokud chcete zobrazit, pokud modulu je kompilována s **/CLR**. Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

Další informace o makra, naleznete v tématu [předdefinovaná makra](../preprocessor/predefined-macros.md).

## <a name="example"></a>Příklad

```
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

## <a name="see-also"></a>Viz také

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)