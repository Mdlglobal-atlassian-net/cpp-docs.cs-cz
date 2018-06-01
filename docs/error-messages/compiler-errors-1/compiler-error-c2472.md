---
title: C2472 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2472
dev_langs:
- C++
helpviewer_keywords:
- C2472
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43279190847322fa2154c6faababdcd41b490eef
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704857"
---
# <a name="compiler-error-c2472"></a>C2472 chyby kompilátoru

> '*funkce*' nemůže být generována ve spravovaném kódu: '*zpráva*'; kompilace s volbou/CLR ke generování smíšený bitové kopie

## <a name="remarks"></a>Poznámky

Tato chyba nastane, když typy nejsou podporované ve spravovaném kódu se používají v rámci čistý společné prostředí runtime (CLR) jazyk. Kompilovat s **/CLR** vyřešit chyby.

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

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
