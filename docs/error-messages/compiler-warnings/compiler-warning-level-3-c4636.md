---
title: Upozornění kompilátoru (úroveň 3) C4636
ms.date: 11/04/2016
f1_keywords:
- C4636
helpviewer_keywords:
- C4636
ms.assetid: 59112a0f-850f-41c6-bd84-8ae8dc84706a
ms.openlocfilehash: a77579b741238547691289fa85a57a0b284ec7e9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991895"
---
# <a name="compiler-warning-level-3-c4636"></a>Upozornění kompilátoru (úroveň 3) C4636

Komentář k dokumentu XML aplikovaný na konstrukci: tag vyžaduje atribut, který není prázdný.

Značka, například `cref`, neměla hodnotu.

## <a name="example"></a>Příklad

Následující ukázka generuje C4636.

```cpp
// C4636.cpp
// compile with: /clr /doc /W3 /c
/// <see cref=''/>
// /// <see cref='System::Exception'/>
ref struct A {   // C4636
   void f(int);
};

// OK
/// <see cref='System::Exception'/>
ref struct B {
   void f(int);
};
```
