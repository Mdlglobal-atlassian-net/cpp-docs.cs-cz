---
title: Chyba kompilátoru C3149
ms.date: 11/04/2016
f1_keywords:
- C3149
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
ms.openlocfilehash: 263eb03b7a9f45458f8d8b586adc6f1cfc5805be
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745977"
---
# <a name="compiler-error-c3149"></a>Chyba kompilátoru C3149

Typ: Tento typ tady nejde použít bez znaku char na nejvyšší úrovni.

Deklarace se nezadala správně.

Například jste mohli definovat typ CLR v globálním oboru a pokusili se vytvořit proměnnou typu v rámci definice. Vzhledem k tomu, že globální proměnné typů CLR nejsou povoleny, kompilátor vygeneruje C3149.

Chcete-li tuto chybu vyřešit, deklarujte proměnné typů CLR uvnitř funkce nebo definice typu.

Následující ukázka generuje C3149:

```cpp
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

```cpp
// C3149b.cpp
// compile with: /clr /c
delegate int MyDelegate(const int, int);
void Test1(MyDelegate m) {}   // C3149
void Test2(MyDelegate ^ m) {}   // OK
```
