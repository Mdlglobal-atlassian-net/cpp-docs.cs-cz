---
title: Chyba kompilátoru C3768
ms.date: 11/04/2016
f1_keywords:
- C3768
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
ms.openlocfilehash: e9c385fd178dc967e72f5e0ca7fab27b28ad962f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676728"
---
# <a name="compiler-error-c3768"></a>Chyba kompilátoru C3768

> nejde převzít adresu virtuální funkce vararg v čistě spravovaném kódu.

## <a name="remarks"></a>Poznámky

**/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Při kompilaci s **/CLR: pure**, nelze převzít adresu proměnné virtuální `vararg` funkce.

## <a name="example"></a>Příklad

Následující ukázka generuje C3768:

```cpp
// C3768.cpp
// compile with: /clr:pure
struct A
{
   virtual void f(...);
};

int main()
{
   &(A::f);   // C3768
}
```