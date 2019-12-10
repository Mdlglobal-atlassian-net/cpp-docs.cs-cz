---
title: Upozornění kompilátoru (úroveň 4) C4365
ms.date: 11/04/2016
f1_keywords:
- C4365
helpviewer_keywords:
- C4365
ms.assetid: af4b4191-bdfd-4dbb-8229-3ba4405df257
ms.openlocfilehash: a9be67c8148b85167d10cd53318f5ef3b41b1340
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990920"
---
# <a name="compiler-warning-level-4-c4365"></a>Upozornění kompilátoru (úroveň 4) C4365

' Action ': převod z ' type_1 ' na ' type_2 ', signed/unsigned – neshoda

Například jste se pokusili převést hodnotu bez znaménka na hodnotu se znaménkem.

C4365 je ve výchozím nastavení vypnutá.  Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4365.

```cpp
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
