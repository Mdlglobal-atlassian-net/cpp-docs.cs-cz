---
title: Upozornění (úroveň 4) C4365 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4365
dev_langs:
- C++
helpviewer_keywords:
- C4365
ms.assetid: af4b4191-bdfd-4dbb-8229-3ba4405df257
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8188e3fc861573025a4855102e3ced14d3136fb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079697"
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