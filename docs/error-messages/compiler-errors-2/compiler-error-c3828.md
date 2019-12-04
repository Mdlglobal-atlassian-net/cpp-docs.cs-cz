---
title: Chyba kompilátoru C3828
ms.date: 11/04/2016
f1_keywords:
- C3828
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
ms.openlocfilehash: 4b47ddbf0775cab2bd7214f68d1b4ed6e06e6eea
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741700"
---
# <a name="compiler-error-c3828"></a>Chyba kompilátoru C3828

' typ objektu ': argumenty umístění nejsou při vytváření instancí spravované nebo WinRTclasses povoleny.

Při vytváření objektu spravovaného typu nebo typu prostředí Windows Runtime nemůžete použít formulář umístění operátoru [ref new, gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md) nebo [New](../../cpp/new-operator-cpp.md).

Následující ukázka generuje C3828 a ukazuje, jak ji opravit:

```cpp
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
