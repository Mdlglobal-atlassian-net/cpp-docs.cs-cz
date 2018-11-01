---
title: Kompilátor upozornění (úroveň 4) C4365
ms.date: 11/04/2016
f1_keywords:
- C4365
helpviewer_keywords:
- C4365
ms.assetid: af4b4191-bdfd-4dbb-8229-3ba4405df257
ms.openlocfilehash: 3f9f6df9f72608f0c1197e0602c3f54548f8efcb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600743"
---
# <a name="compiler-warning-level-4-c4365"></a>Kompilátor upozornění (úroveň 4) C4365

'action': převod z 'type_1' na 'type_2', neshoda signed/unsigned

Pokusili jste se například převod hodnoty bez znaménka na hodnota se znaménkem.

C4365 je vypnuto ve výchozím nastavení.  Další informace najdete v tématu [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4365.

```
// C4365.cpp
// compile with: /W4
#pragma warning(default:4365)

int f(int) { return 0; }
void Test(size_t i) {}

int main() {
   unsigned int n = 10;
   int o = 10;
   n++;
   f(n);   // C4365
   f(o);   // OK

   Test( -19 );   // C4365
}
```