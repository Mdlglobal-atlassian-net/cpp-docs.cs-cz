---
title: Chyba kompilátoru C2217
ms.date: 11/04/2016
f1_keywords:
- C2217
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
ms.openlocfilehash: f178f969afa189910c9d23d70226ecc6c15876a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353533"
---
# <a name="compiler-error-c2217"></a>Chyba kompilátoru C2217

'atribut1' vyžaduje "atribut2"

První atribut funkce vyžaduje, aby druhý atribut.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Přerušení (`__interrupt`) funkce deklarovaná jako `near`. Přerušení funkce musí být `far`.

1. Přerušení funkce deklarovaná pomocí `__stdcall`, nebo `__fastcall`. Přerušení funkce musí C používá konvence volání.

## <a name="example"></a>Příklad

C2217 může také dojít, pokud při pokusu o připojení k funkci modulu CLR, která přijímá proměnný počet argumentů delegáta. Pokud funkci má také přetížení e param array, místo toho, který použijte. Následující ukázka generuje C2217.

```
// C2217.cpp
// compile with: /clr
using namespace System;
delegate void MyDel(String^, Object^, Object^, ...);   // C2217
delegate void MyDel2(String ^, array<Object ^> ^);   // OK

int main() {
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);
   array<Object ^ > ^ x = gcnew array<Object ^>(2);
   x[0] = safe_cast<Object^>(0);
   x[1] = safe_cast<Object^>(1);

   // wl("{0}, {1}", 0, 1);
   wl("{0}, {1}", x);
}
```