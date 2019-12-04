---
title: Chyba kompilátoru C3628
ms.date: 11/04/2016
f1_keywords:
- C3628
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
ms.openlocfilehash: 9976cb2425f8f855ffb2903c07de22822c781e20
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755821"
---
# <a name="compiler-error-c3628"></a>Chyba kompilátoru C3628

základní třída: spravovaná nebo WinRTclasses podporuje pouze veřejnou dědičnost.

Byl proveden pokus o použití spravované třídy nebo třídy WinRT jako [soukromé](../../cpp/private-cpp.md) nebo [chráněné](../../cpp/protected-cpp.md) základní třídy. Spravovanou třídu nebo třídu WinRT lze použít pouze jako základní třídu s [veřejným](../../cpp/public-cpp.md) přístupem.

Následující ukázka generuje C3628 a ukazuje, jak ji opravit:

```cpp
// C3628a.cpp
// compile with: /clr
ref class B {
};

ref class D : private B {   // C3628

// The following line resolves the error.
// ref class D : public B {
};

int main() {
}
```
