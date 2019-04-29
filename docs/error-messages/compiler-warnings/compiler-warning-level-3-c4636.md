---
title: Kompilátor upozornění (úroveň 3) C4636
ms.date: 11/04/2016
f1_keywords:
- C4636
helpviewer_keywords:
- C4636
ms.assetid: 59112a0f-850f-41c6-bd84-8ae8dc84706a
ms.openlocfilehash: 7327189a61e2545bb6003cd95e1ddb116f9f7c94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401706"
---
# <a name="compiler-warning-level-3-c4636"></a>Kompilátor upozornění (úroveň 3) C4636

Komentář k dokumentu XML použitý pro 'vytvořit': značka vyžaduje neprázdný "atribut.

A označit jako `cref`, nemá hodnotu.

## <a name="example"></a>Příklad

Následující ukázka generuje C4636.

```
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