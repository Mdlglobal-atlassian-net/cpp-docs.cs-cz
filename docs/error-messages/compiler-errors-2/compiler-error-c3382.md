---
title: Chyba kompilátoru C3382
ms.date: 11/04/2016
f1_keywords:
- C3382
helpviewer_keywords:
- C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
ms.openlocfilehash: c262ea963ae739fbb76211aae2622e98d5a9b6f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462748"
---
# <a name="compiler-error-c3382"></a>Chyba kompilátoru C3382

'možnost sizeof' není podporován s/clr: safe

Výstupní soubor **/CLR: safe** kompilace je soubor, který je prokazatelně typově bezpečný a sizeof není podporována, protože vrácená hodnota operátoru sizeof je size_t, jejichž velikost se liší v závislosti na operačním systému.

Další informace najdete v tématu,

- [sizeof – operátor](../../cpp/sizeof-operator.md)

- [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Obecné problémy migrace v 64bitovém prostředí Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Příklad

Následující ukázka generuje C3382.

```
// C3382.cpp
// compile with: /clr:safe
int main() {
   sizeof( char );   // C3382
}
```