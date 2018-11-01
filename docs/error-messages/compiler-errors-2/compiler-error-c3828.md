---
title: Chyba kompilátoru C3828
ms.date: 11/04/2016
f1_keywords:
- C3828
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
ms.openlocfilehash: 68a82105a2ff7d58090e9f345bf7aafb34d492d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515281"
---
# <a name="compiler-error-c3828"></a>Chyba kompilátoru C3828

Typ objektu: argumenty umístění není povoleno při vytváření instancí spravované nebo WinRTclasses

Při vytvoření objektu spravovaného typu nebo typ prostředí Windows Runtime, nemůžete použít formu umístění operátoru [ref new, gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md) nebo [nové](../../cpp/new-operator-cpp.md).

Následující ukázka generuje C3828 a ukazuje, jak ho opravit:

```
// C3828a.cpp
// compile with: /clr
ref struct M {
};

ref struct N {
   static array<char>^ bytes = gcnew array<char>(256);
};

int main() {
   M ^m1 = new (&N::bytes) M();   // C3828
   // The following line fixes the error.
   // M ^m1 = gcnew M();
}
```