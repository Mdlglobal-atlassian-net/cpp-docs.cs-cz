---
title: Chyba kompilátoru C3862
ms.date: 11/04/2016
f1_keywords:
- C3862
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
ms.openlocfilehash: 2ba130862b1debbe2991ca7cbcae50192f900cd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446238"
---
# <a name="compiler-error-c3862"></a>Chyba kompilátoru C3862

> "*funkce*': nejde zkompilovat nespravovanou funkci s parametrem/CLR: pure nebo/CLR: safe

## <a name="remarks"></a>Poznámky

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Kompilace s **/CLR: pure** nebo **/CLR: safe** vytvoří bitové kopie pouze jazyk MSIL, bitovou kopii s bez nativního (nespravovaného) kódu.  Proto je nelze použít `unmanaged` direktivy pragma v **/CLR: pure** nebo **/CLR: safe** kompilace.

Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [spravované, nespravované](../../preprocessor/managed-unmanaged.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3862:

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```