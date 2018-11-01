---
title: Kompilátor upozornění (úroveň 4) C4339
ms.date: 11/04/2016
f1_keywords:
- C4339
helpviewer_keywords:
- C4339
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
ms.openlocfilehash: bc9d335b3a09f7953a12b388d5bb40cc4d433969
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567762"
---
# <a name="compiler-warning-level-4-c4339"></a>Kompilátor upozornění (úroveň 4) C4339

'type': zjištěno použití nedefinovaného typu WinRT nebo CLR meta-data - použití tohoto typu může vést k výjimce modulu runtime

Typ není definovaný v kódu, který byl zkompilován pro prostředí Windows Runtime nebo modul common language runtime. Definice typu, aby se zabránilo možné běhovou výjimku.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

Následující ukázka generuje C4339 a ukazuje, jak ho opravit:

```
// C4339.cpp
// compile with: /W4 /clr /c
// C4339 expected
#pragma warning(default : 4339)

// Delete the following line to resolve.
class A;

// Uncomment the following line to resolve.
// class A{};

class X {
public:
   X() {}

   virtual A *mf() {
      return 0;
   }
};

X * f() {
   return new X();
}
```