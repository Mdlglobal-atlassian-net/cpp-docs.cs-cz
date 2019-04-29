---
title: Kompilátor upozornění (úroveň 3) C4823
ms.date: 11/04/2016
f1_keywords:
- C4823
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
ms.openlocfilehash: 28d490c341c4d14c2e6c03e13007b5a8be423622
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401537"
---
# <a name="compiler-warning-level-3-c4823"></a>Kompilátor upozornění (úroveň 3) C4823

'function': používá ukazatele Připnutí ale unwind není povolená sémantika. Zvažte použití možnosti/EHa

Odepnout objektu na spravované haldě, který ukazuje ukazatel Připnutí deklarovány v oboru bloku, kompilátor simuluje chování destruktory místní třídy "že se maskují", že má destruktor nichž ukazatel na ukazatel Připnutí. Pokud chcete povolit volání destruktoru po vyvolání výjimky, je nutné povolit uvolnění objektu, což lze provést pomocí [/EHsc](../../build/reference/eh-exception-handling-model.md).

Můžete také ručně Odepnout objektu a upozornění ignorovat.

## <a name="example"></a>Příklad

Následující ukázka generuje C4823.

```
// C4823.cpp
// compile with: /clr /W3 /EHa-
using namespace System;

ref struct G {
   int m;
};

void f(G ^ pG) {
   try {
      pin_ptr<int> p = &pG->m;
      // manually unpin, ignore warning
      // p = nullptr;
      throw gcnew Exception;
   }
   catch(Exception ^) {}
}   // C4823 warning

int main() {
   f( gcnew G );
}
```
