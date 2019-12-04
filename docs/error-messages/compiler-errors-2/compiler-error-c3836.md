---
title: Chyba kompilátoru C3836
ms.date: 11/04/2016
f1_keywords:
- C3836
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
ms.openlocfilehash: 9c8a7e761f2ece046d5de5c0e74ee911e5ee550d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741401"
---
# <a name="compiler-error-c3836"></a>Chyba kompilátoru C3836

statický konstruktor nemá povolený seznam inicializátorů členů.

Spravovaná třída nemůže mít statický konstruktor, který má také seznam inicializace členů. Statické konstruktory třídy jsou volány modulem CLR (Common Language Runtime) při inicializaci třídy, inicializaci statických datových členů.

## <a name="example"></a>Příklad

Následující ukázka generuje C3836:

```cpp
// C3836a.cpp
// compile with: /clr
ref class M
{
   static int s_i;

public:
   static M() :  s_i(1234)   // C3836, delete initializer to resolve
   {
   }
};

int main()
{
}
```
