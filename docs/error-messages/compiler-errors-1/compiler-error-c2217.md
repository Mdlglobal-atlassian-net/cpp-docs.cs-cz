---
title: Chyba kompilátoru C2217 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2217
dev_langs:
- C++
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4eb8b9fcaffa30f3a5ced5362a0f9d54a45f07e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050616"
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