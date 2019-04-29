---
title: Chyba kompilátoru C3828
ms.date: 11/04/2016
f1_keywords:
- C3828
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
ms.openlocfilehash: f499bb2a8fd6d3148935daec89835b79d2ff5b49
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390591"
---
# <a name="compiler-error-c3828"></a>Chyba kompilátoru C3828

Typ objektu: argumenty umístění není povoleno při vytváření instancí spravované nebo WinRTclasses

Při vytvoření objektu spravovaného typu nebo typ prostředí Windows Runtime, nemůžete použít formu umístění operátoru [ref new, gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md) nebo [nové](../../cpp/new-operator-cpp.md).

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