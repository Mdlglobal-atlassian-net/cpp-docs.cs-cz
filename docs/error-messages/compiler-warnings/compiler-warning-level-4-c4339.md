---
title: Upozornění kompilátoru (úroveň 4) C4339
ms.date: 11/04/2016
f1_keywords:
- C4339
helpviewer_keywords:
- C4339
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
ms.openlocfilehash: e7c3f6f3a2cb9da9857d8336d24d57caf8114850
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991203"
---
# <a name="compiler-warning-level-4-c4339"></a>Upozornění kompilátoru (úroveň 4) C4339

' type ': zjištěno použití nedefinovaného typu v WinRT nebo CLR meta-data-použití tohoto typu může vést k výjimce za běhu.

Typ nebyl definován v kódu, který byl zkompilován pro prostředí Windows Runtime nebo modulu CLR (Common Language Runtime). Definujte typ, aby se předešlo možné výjimce za běhu.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Následující ukázka generuje C4339 a ukazuje, jak ji opravit:

```cpp
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
