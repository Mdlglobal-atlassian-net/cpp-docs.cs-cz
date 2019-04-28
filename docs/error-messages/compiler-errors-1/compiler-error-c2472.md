---
title: Chyba kompilátoru C2472
ms.date: 11/04/2016
f1_keywords:
- C2472
helpviewer_keywords:
- C2472
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
ms.openlocfilehash: d2f104bb61915f8d19d5fff22eea17929c0e8d74
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350907"
---
# <a name="compiler-error-c2472"></a>Chyba kompilátoru C2472

> "*funkce*' nemůže generovat ve spravovaném kódu:"*zpráva*"; proveďte kompilaci s parametrem/CLR k vygenerování smíšenou bitovou kopii

## <a name="remarks"></a>Poznámky

K této chybě dojde při typy nepodporované ve spravovaném kódu se používají v rámci čisté prostředí common language runtime (CLR). Kompilovat s **/CLR** tuto chybu napravíme.

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

## <a name="example"></a>Příklad

Následující ukázka generuje C2472.

```cpp
// C2472.cpp
// compile with: /clr:pure
// C2472 expected

#include <cstdlib>

int main()
{
   int * __ptr32 p32;
   int * __ptr64 p64;

   p32 = (int * __ptr32)malloc(4);
   p64 = p32;
}
```

## <a name="see-also"></a>Viz také:

- [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)
