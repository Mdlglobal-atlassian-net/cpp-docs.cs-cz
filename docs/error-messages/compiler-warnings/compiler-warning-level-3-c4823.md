---
title: Upozornění (úroveň 3) C4823 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4823
dev_langs:
- C++
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c3a6f24a32267f221dbc37e242bae48c0056af5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044649"
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
