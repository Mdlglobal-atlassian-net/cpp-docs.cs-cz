---
title: Chyba kompilátoru C3865
ms.date: 11/04/2016
f1_keywords:
- C3865
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
ms.openlocfilehash: 846657d3598e268d78ff3c39f2bfc901756ad370
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642769"
---
# <a name="compiler-error-c3865"></a>Chyba kompilátoru C3865

'calling_convention': jde použít jenom pro nativní členské funkce

Konvence volání byl použit na funkci, která se globální funkce nebo na spravované členskou funkci. Konvence volání jde použít jenom u nativních (není spravované) členské funkce.

Další informace najdete v tématu [konvence volání](../../cpp/calling-conventions.md).

Následující ukázka generuje C3865:

```
// C3865.cpp
// compile with: /clr
// processor: x86
void __thiscall Func(){}   // C3865

// OK
struct MyType {
   void __thiscall Func(){}
};
```