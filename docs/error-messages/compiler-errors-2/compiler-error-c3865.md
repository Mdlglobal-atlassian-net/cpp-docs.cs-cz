---
title: Chyba kompilátoru C3865
ms.date: 11/04/2016
f1_keywords:
- C3865
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
ms.openlocfilehash: 960c795fe934433e4e3cf79e4c01c49d00205b9b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761488"
---
# <a name="compiler-error-c3865"></a>Chyba kompilátoru C3865

' calling_convention ': lze použít pouze pro nativní členské funkce

Konvence volání byla použita pro funkci, která byla buď globální funkcí, nebo na spravované členské funkci. Konvence volání se dá použít jenom u nativní (nespravované) členské funkce.

Další informace najdete v tématu [konvence volání](../../cpp/calling-conventions.md).

Následující ukázka generuje C3865:

```cpp
// C3865.cpp
// compile with: /clr
// processor: x86
void __thiscall Func(){}   // C3865

// OK
struct MyType {
   void __thiscall Func(){}
};
```
