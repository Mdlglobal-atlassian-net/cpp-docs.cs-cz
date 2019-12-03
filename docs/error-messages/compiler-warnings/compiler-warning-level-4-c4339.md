---
title: Upozornění kompilátoru (úroveň 4) C4339
ms.date: 11/04/2016
f1_keywords:
- C4339
helpviewer_keywords:
- C4339
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
ms.openlocfilehash: fffdaa255f6b8f2259488df610f163bebf8d6dec
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683294"
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