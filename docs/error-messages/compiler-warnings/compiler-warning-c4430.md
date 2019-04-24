---
title: Upozornění kompilátoru C4430
ms.date: 11/04/2016
f1_keywords:
- C4430
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
ms.openlocfilehash: 1d58efd57433a065f08e4111302f358405e3b9ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311433"
---
# <a name="compiler-warning-c4430"></a>Upozornění kompilátoru C4430

chybějící specifikátor typu: předpokládá se int Poznámka: Jazyk C++ nepodporuje typ default int.

Tuto chybu mohou být generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual C++ 2005: všechny deklarace musíte explicitně zadat typ; je již předpokládá.

C4430 je vždy vyvoláno jako chyba.  Můžete vypnout toto upozornění se `#pragma warning` nebo **/wd**; naleznete v tématu [upozornění](../../preprocessor/warning.md) nebo [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / we, Wo, WV, /WX (úroveň upozornění)](../../build/reference/compiler-option-warning-level.md)Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C4430.

```
// C4430.cpp
// compile with: /c
struct CMyClass {
   CUndeclared m_myClass;  // C4430
   int m_myClass;  // OK
};

typedef struct {
   POINT();   // C4430
   // try the following line instead
   // int POINT();
   unsigned x;
   unsigned y;
} POINT;
```