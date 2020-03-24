---
title: Upozornění kompilátoru C4430
ms.date: 11/04/2016
f1_keywords:
- C4430
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
ms.openlocfilehash: 091d988a5af277e78a2954eb5b0b95bc64c56069
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165259"
---
# <a name="compiler-warning-c4430"></a>Upozornění kompilátoru C4430

chybějící specifikátor typu: předpokládá se int Poznámka: C++ nepodporuje default-int.

Tato chyba se může vygenerovat v důsledku práce s shodami s kompilátorem, která byla dokončena pro sadu Visual Studio 2005: všechny deklarace musí explicitně zadat typ; int již nepředpokládáme.

C4430 se vždy vydá jako chyba.  Toto upozornění můžete vypnout pomocí `#pragma warning` nebo **/WD**; Další informace najdete v tématech [Upozornění](../../preprocessor/warning.md) nebo [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/WO,/WV,/WX (úroveň upozornění)](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C4430.

```cpp
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
