---
title: Upozornění kompilátoru (úroveň 2) C4244
ms.date: 11/04/2016
f1_keywords:
- C4244
helpviewer_keywords:
- C4244
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
ms.openlocfilehash: 43d8a992801d556ce85577f5f9da1bec584cb173
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052128"
---
# <a name="compiler-warning-level-2-c4244"></a>Upozornění kompilátoru (úroveň 2) C4244

' Argument ': převod z ' typ1 ' na ' typ2 ', možná ztráta dat

Typ s plovoucí desetinnou čárkou byl převeden na celočíselný typ.  Možná došlo ke ztrátě dat.

Pokud získáte C4244, měli byste buď změnit program na používání kompatibilních typů, nebo přidat do kódu určitou logiku, abyste zajistili, že rozsah možných hodnot bude vždy kompatibilní s typy, které používáte.

C4244 může také proaktivovat úroveň 3 a 4; Další informace najdete v tématu [Upozornění kompilátoru (úrovně 3 a 4) C4244](../../error-messages/compiler-warnings/compiler-warning-levels-3-and-4-c4244.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C4244:

```cpp
// C4244_level2.cpp
// compile with: /W2

int f(int x){ return 0; }
int main() {
   double x = 10.1;
   int i = 10;
   return (f(x));   // C4244
   // try the following line instead
   // return (f(i));
}
```