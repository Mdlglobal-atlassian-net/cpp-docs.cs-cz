---
title: Chyba kompilátoru C3195
ms.date: 11/04/2016
f1_keywords:
- C3195
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
ms.openlocfilehash: c8274e121e953c3e51a0f2ff8c68c315759ce3e1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760423"
---
# <a name="compiler-error-c3195"></a>Chyba kompilátoru C3195

' operator ': je rezervován a nemůže být použit jako člen třídy ref class nebo hodnotového typu. Operátory CLR nebo WinRT se musí definovat pomocí klíčového slova operator.

Kompilátor zjistil definici operátora pomocí spravovaného rozšíření pro C++ syntaxi. Je nutné použít C++ syntaxi operátorů.

Následující ukázka generuje C3195 a ukazuje, jak ji opravit:

```cpp
// C3195.cpp
// compile with: /clr /LD
#using <mscorlib.dll>
value struct V {
   static V op_Addition(V v, int i);   // C3195
   static V operator +(V v, char c);   // OK for new C++ syntax
};
```
