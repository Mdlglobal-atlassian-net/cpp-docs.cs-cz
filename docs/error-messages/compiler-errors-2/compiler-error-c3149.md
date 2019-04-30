---
title: Chyba kompilátoru C3149
ms.date: 11/04/2016
f1_keywords:
- C3149
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
ms.openlocfilehash: 8238dcec821256dad8101cd7ad59b2d85882c218
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345510"
---
# <a name="compiler-error-c3149"></a>Chyba kompilátoru C3149

'type': nelze použít tento typ tady bez nejvyšší úrovně 'char'.

Deklarace nebyl správně zadán.

Například můžete mít definovaný typ CLR v globálním oboru a pokusu o vytvoření proměnné typu jako součást definice. Protože globální proměnné typy CLR nejsou povoleny, bude kompilátor generovat C3149.

Chcete-li vyřešit tuto chybu, deklarujte proměnné typů CLR uvnitř definice funkce nebo typ.

Následující ukázka generuje C3149:

```
// C3149.cpp
// compile with: /clr
using namespace System;
int main() {
   // declare an array of value types
   array< Int32 ^> IntArray;   // C3149
   array< Int32>^ IntArray2;   // OK
}
```

Následující ukázka generuje C3149:

```
// C3149b.cpp
// compile with: /clr /c
delegate int MyDelegate(const int, int);
void Test1(MyDelegate m) {}   // C3149
void Test2(MyDelegate ^ m) {}   // OK
```
